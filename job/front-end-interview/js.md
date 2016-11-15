# js

## 数组去重
```js
        // 以下是数组去重的三种方法：
        Array.prototype.unique1 = function() {
            var n = []; //临时数组
            for (var i = 0; i < this.length; i++){
                //遍历当前数组
                //如果当前数组的第i已经保存进了临时数组，那么跳过，
                //否则把当前项push到临时数组里面
                if(n.indexOf(this[i]) == -1){
                    n.push(this[i]);
                }
            }
            return n;
        }
        Array.prototype.unique2 = function(){
            var n = {},
                r = []; //n为hash表，r为临时数组
            for (var i = 0; i < this.length; i++) { //遍历当前数组
                if (!n[this[i]]) { //如果hash表中没有当前项
                    n[this[i]] = true; //存入hash表
                    r.push(this[i]); //把当前数组的当前项push到临时数组里面
                }
            }
            return r;
        }
        Array.prototype.unique3 = function(){
            var n = [this[0]]; //结果数组
            for (var i = 1; i < this.length; i++) //从第二项开始遍历
            {
                //如果当前数组的第i项在当前数组中第一次出现的位置不是i，
                //那么表示第i项是重复的，忽略掉。否则存入结果数组
                if (this.indexOf(this[i]) == i) n.push(this[i]);
            }
            return n;
        }
``` 

## setTimeout() 和 setInterval() 本质区别

```html
        <h1>setTimeout() 和 setInterval() 本质区别？</h1>
        <pre>
            setInterval(run, 1000);
            设置间隔/定时器, 
            每隔一段时间调用指定函数（N次）, 
            setInterval 执行的时间间隔, 最小是设置的时间 ？()
            持续占有独立线程的一个定时触发函数！, 
            推荐用内置方法 ？;

            setTimeout()
            设置超时, 
            是在一段时间后调用指定函数（仅一次）,
            不会持续占有一个线程的资源，执行完当前的方法，会释放当然的线程资源，等待下次触发，会重新申请资源！,
            setTimeout时间不是标准的系统时间，是有误差的。

            delay可选:
            时间，以毫秒（千分之一秒）计时器应该在执行指定的函数或代码之前等待。
            如果省略此参数，则使用值0。注意，实际延迟可能更长;请参阅延迟时间长于以下规定的原因。
            setTimeout(func, 0); === setTimeout(func);
        </pre>
    </div>
    <script>
        var n, m;
        let run0 = (n = 0) =>{
            console.log(`this is ${n}s`);
        }
        setTimeout(run0, 0);
        let run = (m = 1) =>{
            console.log(`this is ${m}s`);
        }
        run(1);
        let siID = setInterval(run0(2), 0);
        run(3);
        setTimeout(() => {
            clearInterval(siID);
            console.log(`over!`);
        }, 0);
    </script>
``` 

## 

```js
``` 

## 

```js
``` 

## 

```js
``` 


## 设计模式

```js
        // js常用设计模式的实现思路，单例，工厂，代理，装饰，观察者模式等

            // 1) 单例: 任意对象都是单例，无须特别处理
            var obj = {name: 'michaelqin', age: 30};

            // 2) 工厂: 就是同样形式参数返回不同的实例
            function Person() { this.name = 'Person1'; }
            function Animal() { this.name = 'Animal1'; }

            function Factory() {}
            Factory.prototype.getInstance = function(className) {
                return eval('new ' + className + '()');
            }

            var factory = new Factory();
            var obj1 = factory.getInstance('Person');
            var obj2 = factory.getInstance('Animal');
            console.log(obj1.name); // Person1
            console.log(obj2.name); // Animal1

            //3) 代理: 就是新建个类调用老类的接口,包一下
            function Person() { }
            Person.prototype.sayName = function() { console.log('michaelqin'); }
            Person.prototype.sayAge = function() { console.log(30); }

            function PersonProxy() {
                this.person = new Person();
                var that = this;
                this.callMethod = function(functionName) {
                    console.log('before proxy:', functionName);
                    that.person[functionName](); // 代理
                    console.log('after proxy:', functionName);
                }
            }

            var pp = new PersonProxy();
            pp.callMethod('sayName'); // 代理调用Person的方法sayName()
            pp.callMethod('sayAge'); // 代理调用Person的方法sayAge()

            //4) 观察者: 就是事件模式，比如按钮的onclick这样的应用.
            function Publisher() {
                this.listeners = [];
            }
            Publisher.prototype = {
                'addListener': function(listener) {
                    this.listeners.push(listener);
                },

                'removeListener': function(listener) {
                    delete this.listeners[listener];
                },

                'notify': function(obj) {
                    for(var i = 0; i < this.listeners.length; i++) {
                        var listener = this.listeners[i];
                        if (typeof listener !== 'undefined') {
                            listener.process(obj);
                        }
                    }
                }
            }; // 发布者
            function Subscriber() {

            }
            Subscriber.prototype = {
                'process': function(obj) {
                    console.log(obj);
                }
            };　// 订阅者

            var publisher = new Publisher();
            publisher.addListener(new Subscriber());
            publisher.addListener(new Subscriber());
            publisher.notify({name: 'michaelqin', ageo: 30}); // 发布一个对象到所有订阅者
            publisher.notify('2 subscribers will both perform process'); // 发布一个字符串到所有订阅者
``` 
