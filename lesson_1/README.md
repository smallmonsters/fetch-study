## 第一次使用[fetch](https://developer.mozilla.org/zh-CN/docs/Web/API/WindowOrWorkerGlobalScope/fetch)

* ##### fetch的使用场景

* ##### fetch和XHR的区别
    1、XHR是使用它的实例来发送请求和接受响应,而fetch可以直接使用或者接受一个[Request](https://developer.mozilla.org/zh-CN/docs/Web/API/Request)

    ```JavaScript
    // XHR
    function xhr() {
        var xhr = new XMLHttpRequest();
        xhr.onload = function() {};
        xhr.open('GET', URL);
        xhr.send();
    }
    // fetch
    var req = new Request(URL, {method: 'GET', cache: 'reload'});
      fetch(req).then(function(response) {
        return response.json();
      }).then(function(json) {
        insertPhotos(json);
    });
    //or
    fetch(URL,{'GET', cache: 'reload'}}).then(function(response) {
        return response.json();
      }).then(function(json) {
        insertPhotos(json);
    });
    ```

    2、fetch 默认情况下不会发送 cookie

* 发送一个简单的fetch
[demo]()

##### 问题
1、当fetch第一个参数是Request时，第二个参数会覆盖Request的配置吗？
2、fetch如何带上cookie