# XMLHttpRequest 2

> https://xhr.spec.whatwg.org/


## Abstract

XMLHttpRequest defines an API that provides scripted client functionality for transferring data between a client and a server.  

XMLHttpRequest定义了一个API，它提供了用于在客户端和服务器之间传输数据的脚本化客户端功能。  

## Table of Contents

1 Introduction 介绍  
    1.1 Specification history  规范历史  
2 Conformance 一致性  
    2.1 Extensibility 可扩展性  
3 Terminology 术语  
4 Interface XMLHttpRequest
    4.1 Constructors
    4.2 Garbage collection
    4.3 Event handlers
    4.4 States
    4.5 Request
    4.5.1 The open() method
    4.5.2 The setRequestHeader() method
    4.5.3 The timeout attribute
    4.5.4 The withCredentials attribute
    4.5.5 The upload attribute
    4.5.6 The send() method
    4.5.7 The abort() method
    4.6 Response
    4.6.1 The responseURL attribute
    4.6.2 The status attribute
    4.6.3 The statusText attribute
    4.6.4 The getResponseHeader() method
    4.6.5 The getAllResponseHeaders() method
    4.6.6 Response body
    4.6.7 The overrideMimeType() method
    4.6.8 The responseType attribute
    4.6.9 The response attribute
    4.6.10 The responseText attribute
    4.6.11 The responseXML attribute
    4.7 Events summary
5 Interface FormData
6 Interface ProgressEvent
    6.1 Firing events using the ProgressEvent interface
    6.2 Suggested names for events using the ProgressEvent interface
    6.3 Security Considerations
    6.4 Example
References
Acknowledgments









