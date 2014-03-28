SAQ
===

SAQ是指Small Asynchronous Queue，即短小的异步调用库。

<pre><code>
var obj = {
    value: null
};

saq([
    function(callback) {
        var self = this;
        setTimeout(function() {
            self.value = 10;
            callback(20);
        }, 200);
    },
    function(callback, add) {  
        console.log(this.value + add);  
        callback();
    },
    function(callback) {
        this.value += 10;
        console.log(obj.value);
        setTimeout(function() {
            callback();
        }, 200);
    },
    function() {
      console.log("end");
    }
], obj);

</code></pre>
