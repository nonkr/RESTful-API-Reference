RESTful-api-reference
=====================

[RFC 2119][]中的`必须(MUST)`，`不可(MUST NOT)`，`建议(SHOULD)`，`不建议(SHOULD NOT)`，`可以/可能(MAY)`等关键词将在本规范中用来做一些解释性的描述。

使用[事务][]进行顶级的表述，**资源**属于一种**事务**。

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[事务]: http://www.infoq.com/cn/articles/rest-introduction/
[ISO 8601]: https://www.ietf.org/rfc/rfc3339.txt

#### 五条基本原则
* 为所有事务定义ID
* 将所有事务链接在一起(HATEOAS，Github的API就是这种设计)
* 使用标准方法(GET,POST,PUT,DELETE)
* 资源多重表述
* 无状态通信

---

1. `必须`使用HTTPS协议
1. `建议`使用名词对URI进行命名，对应某个或某些资源，实在难以和某资源对应上的，例如search，那就这么办吧
1. URI中的事务`建议`使用小写的复数形式，例如：`GET /users`
1. API的身份认证应该使用OAuth2.0框架
1. 服务器返回的数据格式，应该尽量使用JSON，避免使用XML，但也应该支持XML
2. 返回的时间统一使用[ISO 8601][]格式`YYYY-MM-DDTHH:MM:SSZ`
3. POST，PATCH，PUT和DELETE请求的参数应用JSON编码放在请求体中，并用`Content-Type: application/json`指明



#### DEMO
1. `GET /user/emails` 查询email

    * response
        * header
    
        ```
        Status: 200 OK
        ```
            
        * body
          
        ```
        [
            {
                "email": "name@hotmail.com",
                "primary": true
            }
        ]
        ```
        
2. `POST /user/emails` 新增email
    * request
    
    ```
    [
        "foo@hotmail.com",
        "gcc@gmail.com"
    ]
    ```
    * response
        * header
        
        ```
        Status: 201 Created
        ```
        
        * body
        
        ```
        [
            {
                "email": "foo@hotmail.com",
                "primary": false
            },
            {
                "email": "gcc@gmail.com",
                "primary": false
            }
        ]
        ```
        
3. `DELETE /user/emails` 删除email
    * request
    
    ```
    [
        "foo@hotmail.com",
        "gcc@gmail.com"
    ]
    ```
    
    * response
        * header
        
        ```
        Status: 204 No Content
        ```

#### HTTP Status Code
Code | Text
---- | ----
200  | OK
201  | Created
202  | Accepted
203  | Non-Authoritative Information
204  | No Content
205  | Reset Content
206  | Partial Content
301  | Moved Permanently
302  | Found
303  | See Other
304  | Not Modified
307  | Temporary Redirect
400  | Bad Request
401  | Unauthorized
403  | Forbidden
404  | Not Found
405  | Method Not Allowed
409  | Conflict
500  | Internal Server Error
502  | Bad Gateway



#### 参考
* [http://www.360doc.com/content/14/0523/09/15870680_380120012.shtml]()
* [https://developer.github.com/v3/]()
* [http://developer.openstack.org/api-ref.html]()
* [http://ningandjiao.iteye.com/blog/1990004]()
* [http://www.subbu.org/blog/2008/10/explaining-state-in-hateoas]()


<script src="http://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.1/highlight.min.js"></script>
<link rel="stylesheet" href="http://cdnjs.cloudflare.com/ajax/libs/highlight.js/8.1/styles/github.min.css">
<script>
  hljs.initHighlightingOnLoad();
</script>