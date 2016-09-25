# 24.3 The JSON Object

The JSON object is the %JSON% intrinsic object and the initial value of the JSON property of the global object. The JSON object is a single ordinary object that contains two functions, parse and stringify, that are used to parse and construct JSON texts. The JSON Data Interchange Format is defined in ECMA-404. The JSON interchange format used in this specification is exactly that described by ECMA-404.

Conforming implementations of JSON.parse and JSON.stringify must support the exact interchange format described in the ECMA-404 specification without any deletions or extensions to the format.

The value of the [[Prototype]] internal slot of the JSON object is the intrinsic object %ObjectPrototype% (19.1.3). The value of the [[Extensible]] internal slot of the JSON object is set to true.

The JSON object does not have a [[Construct]] internal method; it is not possible to use the JSON object as a constructor with the new operator.

The JSON object does not have a [[Call]] internal method; it is not possible to invoke the JSON object as a function.

## 24.3.1 JSON.parse ( text [ , reviver ] )

The parse function parses a JSON text (a JSON-formatted String) and produces an ECMAScript value. The JSON format is a subset of the syntax for ECMAScript literals, Array Initializers and Object Initializers. After parsing, JSON objects are realized as ECMAScript objects. JSON arrays are realized as ECMAScript Array instances. JSON strings, numbers, booleans, and null are realized as ECMAScript Strings, Numbers, Booleans, and null.

The optional reviver parameter is a function that takes two parameters, key and value. It can filter and transform the results. It is called with each of the key/value pairs produced by the parse, and its return value is used instead of the original value. If it returns what it received, the structure is not modified. If it returns undefined then the property is deleted from the result.
Let JText be ToString(text).
ReturnIfAbrupt(JText).
Parse JText interpreted as UTF-16 encoded Unicode points (6.1.4) as a JSON text as specified in 
ECMA-404. Throw a SyntaxError exception if JText is not a valid JSON text as defined in that specification.
Let scriptText be the result of concatenating "(", JText, and ");".
Let completion be the result of parsing and evaluating scriptText as if it was the source text of an ECMAScript Script. but using the alternative definition of DoubleStringCharacter provided below. The extended PropertyDefinitionEvaluation semantics defined in B.3.1 must not be used during the evaluation.
Let unfiltered be completion.[[value]].
Assert: unfiltered will be either a primitive value or an object that is defined by either an ArrayLiteral or an ObjectLiteral.
If IsCallable(reviver) is true, then
Let root be ObjectCreate(%ObjectPrototype%).
Let rootName be the empty String.
Let status be CreateDataProperty(root, rootName, unfiltered).
Assert: status is true.
Return InternalizeJSONProperty(root, rootName).
Else
Return unfiltered.
JSON allows Unicode code units 0x2028 (LINE SEPARATOR) and 0x2029 (PARAGRAPH SEPARATOR) to directly appear in String literals without using an escape sequence. This is enabled by using the following alternative definition of DoubleStringCharacter when parsing scriptText in step 5:

DoubleStringCharacter ::
SourceCharacter but not one of " or \ or U+0000 through U+001F
\ EscapeSequence
The SV of DoubleStringCharacter :: SourceCharacter but not one of " or \ or U+0000 through U+001F is the UTF16Encoding (10.1.1) of the code point value of SourceCharacter.
NOTE The syntax of a valid JSON text is a subset of the ECMAScript PrimaryExpression syntax. Hence a valid JSON text is also a valid PrimaryExpression. Step 3 above verifies that JText conforms to that subset. When scriptText is parsed and evaluated as a Script the result will be either a String, Number, Boolean, or Null primitive value or an Object defined as if by an ArrayLiteral or ObjectLiteral.

### 24.3.1.1 Runtime Semantics: InternalizeJSONProperty( holder, name)

The abstract operation InternalizeJSONProperty is a recursive abstract operation that takes two parameters: a holder object and the String name of a property in that object. InternalizeJSONProperty uses the value of reviver that was originally passed to the above parse function.
Let val be Get(holder, name).
ReturnIfAbrupt(val).
If Type(val) is Object, then
Let isArray be IsArray(val).
ReturnIfAbrupt(isArray).
If isArray is true, then
Set I to 0.
Let len be ToLength(Get(val, "length")).
ReturnIfAbrupt(len).
Repeat while I < len,
Let newElement be InternalizeJSONProperty(val, ToString(I)).
ReturnIfAbrupt(newElement).
If newElement is undefined, then
Let status be val.[[Delete]](ToString(I)).
Else
Let status be CreateDataProperty(val, ToString(I), newElement).
NOTE This algorithm intentionally does not throw an exception if status is false.
ReturnIfAbrupt(status).
Add 1 to I.
Else
Let keys be EnumerableOwnNames(val).
ReturnIfAbrupt(keys).
For each String P in keys do,
Let newElement be InternalizeJSONProperty(val, P).
ReturnIfAbrupt(newElement).
If newElement is undefined, then
Let status be val.[[Delete]](P).
Else
Let status be CreateDataProperty(val, P, newElement).
NOTE This algorithm intentionally does not throw an exception if status is false.
ReturnIfAbrupt(status).
Return Call(reviver, holder, «name, val»).
It is not permitted for a conforming implementation of JSON.parse to extend the JSON grammars. If an implementation wishes to support a modified or extended JSON interchange format it must do so by defining a different parse function.

NOTE In the case where there are duplicate name Strings within an object, lexically preceding values for the same key shall be overwritten.

## 24.3.2 JSON.stringify ( value [ , replacer [ , space ] ] )

The stringify function returns a String in UTF-16 encoded JSON format representing an ECMAScript value. It can take three parameters. The value parameter is an ECMAScript value, which is usually an object or array, although it can also be a String, Boolean, Number or null. The optional replacer parameter is either a function that alters the way objects and arrays are stringified, or an array of Strings and Numbers that acts as a white list for selecting the object properties that will be stringified. The optional space parameter is a String or Number that allows the result to have white space injected into it to improve human readability.

These are the steps in stringifying an object:
Let stack be an empty List.
Let indent be the empty String.
Let PropertyList and ReplacerFunction be undefined.
If Type(replacer) is Object, then
If IsCallable(replacer) is true, then
Let ReplacerFunction be replacer.
Else,
Let isArray be IsArray(replacer).
ReturnIfAbrupt(isArray).
If isArray is true, then
Let PropertyList be an empty List
Let len be ToLength(Get(replacer, "length")).
ReturnIfAbrupt(len).
Let k be 0.
Repeat while k<len.
Let v be Get(replacer, ToString(k)).
ReturnIfAbrupt(v).
Let item be undefined.
If Type(v) is String, let item be v.
Else if Type(v) is Number, let item be ToString(v).
Else if Type(v) is Object, then
If v has a [[StringData]] or [[NumberData]] internal slot, let item be ToString(v).
ReturnIfAbrupt(item).
If item is not undefined and item is not currently an element of PropertyList, then
Append item to the end of PropertyList.
Let k be k+1.
If Type(space) is Object, then
If space has a [[NumberData]] internal slot, then
Let space be ToNumber(space).
ReturnIfAbrupt(space).
Else if space has a [[StringData]] internal slot, then
Let space be ToString(space).
ReturnIfAbrupt(space).
If Type(space) is Number, then
Let space be min(10, ToInteger(space)).
Set gap to a String containing space occurrences of code unit 0x0020 (SPACE). This will be the empty String if space is less than 1.
Else if Type(space) is String, then
If the number of elements in space is 10 or less, set gap to space otherwise set gap to a String consisting of the first 10 elements of space.
Else
Set gap to the empty String.
Let wrapper be ObjectCreate(%ObjectPrototype%).
Let status be CreateDataProperty(wrapper, the empty String, value).
Assert: status is true.
Return SerializeJSONProperty(the empty String, wrapper).
NOTE 1 JSON structures are allowed to be nested to any depth, but they must be acyclic. If value is or contains a cyclic structure, then the stringify function must throw a TypeError exception. This is an example of a value that cannot be stringified:

a = [];
a[0] = a;
my_text = JSON.stringify(a); // This must throw a TypeError.
NOTE 2 Symbolic primitive values are rendered as follows:

The null value is rendered in JSON text as the String null.
The undefined value is not rendered.
The true value is rendered in JSON text as the String true.
The false value is rendered in JSON text as the String false.
NOTE 3 String values are wrapped in QUOTATION MARK (") code units. The code units " and \ are escaped with \ prefixes. Control characters code units are replaced with escape sequences \uHHHH, or with the shorter forms, \b (BACKSPACE), \f (FORM FEED), \n (LINE FEED), \r (CARRIAGE RETURN), \t (CHARACTER TABULATION).

NOTE 4 Finite numbers are stringified as if by calling ToString(number). NaN and Infinity regardless of sign are represented as the String null.

NOTE 5 Values that do not have a JSON representation (such as undefined and functions) do not produce a String. Instead they produce the undefined value. In arrays these values are represented as the String null. In objects an unrepresentable value causes the property to be excluded from stringification.

NOTE 6 An object is rendered as U+007B (LEFT CURLY BRACKET) followed by zero or more properties, separated with a U+002C (COMMA), closed with a U+007D (RIGHT CURLY BRACKET). A property is a quoted String representing the key or property name, a U+003A (COLON), and then the stringified property value. An array is rendered as an opening U+005B (LEFT SQUARE BRACKET followed by zero or more values, separated with a U+002C (COMMA), closed with a U+005D (RIGHT SQUARE BRACKET).

### 24.3.2.1 Runtime Semantics: SerializeJSONProperty ( key, holder ) 

The abstract operation SerializeJSONProperty with arguments key, and holder has access to ReplacerFunction from the invocation of the stringify method. Its algorithm is as follows:
Let value be Get(holder, key).
ReturnIfAbrupt(value).
If Type(value) is Object, then
Let toJSON be Get(value, "toJSON").
ReturnIfAbrupt(toJSON).
If IsCallable(toJSON) is true
Let value be Call(toJSON, value, «key»).
ReturnIfAbrupt(value).
If ReplacerFunction is not undefined, then
Let value be Call(ReplacerFunction, holder, «key, value»).
ReturnIfAbrupt(value).
If Type(value) is Object, then
If value has a [[NumberData]] internal slot, then
Let value be ToNumber(value).
ReturnIfAbrupt(value).
Else if value has a [[StringData]] internal slot, then
Let value be ToString(value).
ReturnIfAbrupt(value).
Else if value has a [[BooleanData]] internal slot, then
Let value be the value of the [[BooleanData]] internal slot of value.
If value is null, return "null".
If value is true, return "true".
If value is false, return "false".
If Type(value) is String, return QuoteJSONString(value).
If Type(value) is Number, then
If value is finite, return ToString(value).
Else, return "null".
If Type(value) is Object, and IsCallable(value) is false, then
Let isArray be IsArray(value).
ReturnIfAbrupt(isArray).
If isArray is true, return SerializeJSONArray(value).
Else, return SerializeJSONObject(value).
Return undefined.
### 24.3.2.2 Runtime Semantics: QuoteJSONString ( value )

The abstract operation QuoteJSONString with argument value wraps a String value in QUOTATION MARK code units and escapes certain other code units within it.
Let product be code unit 0x0022 (QUOTATION MARK).
For each code unit C in value
If C is 0x0022 (QUOTATION MARK) or 0x005C (REVERSE SOLIDUS), then
Let product be the concatenation of product and code unit 0x005C (REVERSE SOLIDUS).
Let product be the concatenation of product and C.
Else if C is 0x0008 (BACKSPACE), 0x000C (FORM FEED), 0x000A (LINE FEED), 0x000D (CARRIAGE RETURN), or 0x000B (LINE TABULATION), then
Let product be the concatenation of product and code unit 0x005C (REVERSE SOLIDUS).
Let abbrev be the String value corresponding to the value of C as follows:
BACKSPACE	"b"
FORM FEED (FF)	"f"
LINE FEED (LF)	"n"
CARRIAGE RETURN (CR)	"r"
LINE TABULATION	"t"
Let product be the concatenation of product and abbrev.
Else if C has a code unit value less than 0x0020 (SPACE), then
Let product be the concatenation of product and code unit 0x005C (REVERSE SOLIDUS).
Let product be the concatenation of product and "u".
Let hex be the string result of converting the numeric code unit value of C to a String of four hexadecimal digits. Alphabetic hexadecimal digits are presented as lowercase Latin letters.
Let product be the concatenation of product and hex.
Else,
Let product be the concatenation of product and C.
Let product be the concatenation of product and code unit 0x0022 (QUOTATION MARK).
Return product.
### 24.3.2.3 Runtime Semantics: SerializeJSONObject ( value )

The abstract operation SerializeJSONObject with argument value serializes an object. It has access to the stack, indent, gap, and PropertyList values of the current invocation of the stringify method.
If stack contains value, throw a TypeError exception because the structure is cyclical.
Append value to stack.
Let stepback be indent.
Let indent be the concatenation of indent and gap.
If PropertyList is not undefined, then
Let K be PropertyList.
Else,
Let K be EnumerableOwnNames(value).
Let partial be an empty List.
For each element P of K,
Let strP be SerializeJSONProperty(P, value).
ReturnIfAbrupt(strP).
If strP is not undefined, then
Let member be QuoteJSONString(P).
Let member be the concatenation of member and the string ":".
If gap is not the empty String, then
Let member be the concatenation of member and code unit 0x0020 (SPACE).
Let member be the concatenation of member and strP.
Append member to partial.
If partial is empty, then
Let final be "{}".
Else,
If gap is the empty String, then
Let properties be a String formed by concatenating all the element Strings of partial with each adjacent pair of Strings separated with code unit 0x002C (COMMA). A comma is not inserted either before the first String or after the last String.
Let final be the result of concatenating "{", properties, and "}".
Else gap is not the empty String
Let separator be the result of concatenating code unit 0x002C (COMMA), code unit 0x000A (LINE FEED), and indent.
Let properties be a String formed by concatenating all the element Strings of partial with each adjacent pair of Strings separated with separator. The separator String is not inserted either before the first String or after the last String.
Let final be the result of concatenating "{", code unit 0x000A (LINE FEED), indent, properties, code unit 0x000A, stepback, and "}".
Remove the last element of stack.
Let indent be stepback.
Return final.
### 24.3.2.4 Runtime Semantics: SerializeJSONArray ( value )

The abstract operation SerializeJSONArray with argument value serializes an array. It has access to the stack, indent, and gap values of the current invocation of the stringify method.
If stack contains value, throw a TypeError exception because the structure is cyclical.
Append value to stack.
Let stepback be indent.
Let indent be the concatenation of indent and gap.
Let partial be an empty List.
Let len be ToLength(Get(value, "length")).
ReturnIfAbrupt(len).
Let index be 0.
Repeat while index < len
Let strP be SerializeJSONProperty(ToString(index), value).
ReturnIfAbrupt(strP).
If strP is undefined, then
Append "null" to partial.
Else,
Append strP to partial.
Increment index by 1.
If partial is empty, then
Let final be "[]".
Else,
If gap is the empty String, then
Let properties be a String formed by concatenating all the element Strings of partial with each adjacent pair of Strings separated with code unit 0x002C (COMMA). A comma is not inserted either before the first String or after the last String.
Let final be the result of concatenating "[", properties, and "]".
Else,
Let separator be the result of concatenating code unit 0x002C (COMMA), code unit 0x000A (LINE FEED), and indent.
Let properties be a String formed by concatenating all the element Strings of partial with each adjacent pair of Strings separated with separator. The separator String is not inserted either before the first String or after the last String.
Let final be the result of concatenating "[", code unit 0x000A (LINE FEED), indent, properties, code unit 0x000A, stepback, and "]".
Remove the last element of stack.
Let indent be stepback.
Return final.
NOTE The representation of arrays includes only the elements between zero and array.length – 1 inclusive. Properties whose keys are not array indexes are excluded from the stringification. An array is stringified as an opening LEFT SQUARE BRACKET, elements separated by COMMA, and a closing RIGHT SQUARE BRACKET.

## 24.3.3 JSON [ @@toStringTag ]

The initial value of the @@toStringTag property is the String value "JSON".

This property has the attributes { [[Writable]]: false, [[Enumerable]]: false, [[Configurable]]: true }.
