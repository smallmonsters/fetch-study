## 第一次使用[fetch](https://developer.mozilla.org/zh-CN/docs/Web/API/Fetch_API)

* ##### 如何使用[fetch]((https://developer.mozilla.org/zh-CN/docs/Web/API/WindowOrWorkerGlobalScope/fetch))

* ##### fetch的使用场景
   1、服务器因该支持

* ##### fetch和XHR的区别

    ###### 1、XHR是使用它的实例来发送请求和接受响应,而fetch可以直接使用或者接受一个[Request](https://developer.mozilla.org/zh-CN/docs/Web/API/Request)

    ###### 2、fetch API是个更底层的API

    ``` JavaScript
    // XHR
    function xhr() {
        var xhr = new XMLHttpRequest();
        xhr.onload = function() {};
        xhr.open('GET', URL);
        xhr.send();
    }
    // fetch
    var req = new Request(URL, {
        method: 'GET',
        cache: 'reload'
    });
    fetch(req).then(function(response) {
        return response.json();
    }).then(function(json) {
        insertPhotos(json);
    });
    //or
    fetch(URL, {
        'GET',
        cache: 'reload'
    }
    }).then(function(response) {
        return response.json();
    }).then(function(json) {
        insertPhotos(json);
    });
    ```


    ###### 3、兼容性对比

    fetch
    ![image](https://github.com/smallmonsters/fetch-study/blob/master/static/1.png)

    XHR
    ![image](https://github.com/smallmonsters/fetch-study/blob/master/static/2.png)

    ###### 4、缺点对比
    fetch
    > 1. fetch只对网络错误报错，http状态码错误不报错
    > 2. fetch不支持[abort](https://github.com/smallmonsters/fetch-study/blob/master/extension_of_knowledge/1.md)，无法终止
    > 3. fetch不支持超时控制，使用setTimeout和Promise.reject实现的超时控制不能阻止请求过程继续在后台运行，造成了流量的浪费
    > 4. fetch没有原生检测请求进度的方式，XHR可以
    > 5. 默认情况下fetch不发送cookie，除非手动配置


* 发送一个简单的fetch

[demo](https://github.com/smallmonsters/fetch-study/blob/master/lesson_1/answer.html)

##### 问题

1、当fetch第一个参数是Request时，第二个参数会覆盖Request的配置吗？

2、如何发送post请求

[answer](https://github.com/smallmonsters/fetch-study/blob/master/lesson_1/index.html)
