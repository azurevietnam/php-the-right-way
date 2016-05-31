---
isChild: true
anchor:  object_caching
---

## Object Caching {#object_caching_title}

Đôi khi bạn nên cache từng object trong ứng dụng, như các dữ liệu đắt đỏ, hay các truy vấn dữ liệu mà kết quả 
không thay đổi. Bạn có thể dùng phần mềm caching object để quản lý những dữ liệu này trong bộ nhớ để tăng tốc truy 
cập trong những lần sau.

Hầu hết các giải pháp bytecode caching cũng cho phép bạn lưu trữ custom data. APCu, XCache, và WinCache đều cung cấp các API 
cho phép lưu dữ liệu từ code PHP trong bộ nhớ cache của chúng.

Hệ thống object caching phổ biến nhất là APCu và memcached. APCu bao gồm một AOI đơn giản để thêm dữ liệu vào bộ nhớ 
của nó và cài đặt, sử dụng rất đơn giản. Nhưng hạn chế của APCu là nó phụ thuộc vào server được cài đặt. 
Memcached thì được cài đặt như một ứng dụng tách biệt, có thể truy cập trên nhiều network, bạn có thể lưu trữ 
các đối tượng vào khu vực lưu trữ dữ liệu siêu nhanh ở khu vực trung tâm và các hệ thống khác cũng có thể truy cập tới.

Ghi chú rằng khi chay PHP như một ứng dụng (Fast-)CGI bên trong webserver, mỗi tiến trình PHP sẽ có cache của nó.
Ví dụ, dữ liệu của APCu sẽ không được chia sẽ giữa các process của các worker của bạn. Trong những trường hợp 
này, bạn có thể muốn cân nhắc dùng memcached thay thế, bởi vì nó không phụ thuộc vào các PHP process.

Trong thiết đặt network của ACPu thông thường sẽ làm tốt hơn về tốc độ truy cập, nhưng memcached cho phép 
mở rộng nhanh hơn và hơn thế nữa. Nếu bạn không muốn có nhiều server chạy ứng dụng của mình hay không cần thêm 
nhiều tính năng memcached cung cấp thì ACPu là lựa chọn tốt nhất cho object caching.

Ví dụ sử dụng APCu:

{% highlight php %}
<?php
// check if there is data saved as 'expensive_data' in cache
$data = apc_fetch('expensive_data');
if ($data === false) {
    // data is not in cache; save result of expensive call for later use
    apc_add('expensive_data', $data = get_expensive_data());
}

print_r($data);
{% endhighlight %}

Note that prior to PHP 5.5, APC provides both an object cache and a bytecode cache. 
APCu is a project to bring APC's
object cache to PHP 5.5+, since PHP now has a built-in bytecode cache (OPcache).

Ghi chú: Từ PHP 5.5, ACP cung cấp cả object cache và bytecode cache. ACPu là dự án mang object cache của ACP vào 
PHP 5.5+.

### Tìm hiểu thêm về các hệ thống object caching phổ biến:

* [APCu](https://github.com/krakjoe/apcu)
* [APC Functions](http://php.net/ref.apc)
* [Memcached](http://memcached.org/)
* [Redis](http://redis.io/)
* [XCache APIs](http://xcache.lighttpd.net/wiki/XcacheApi)
* [WinCache Functions](http://php.net/ref.wincache)
