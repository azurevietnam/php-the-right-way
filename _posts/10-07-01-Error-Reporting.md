---
title: Thông báo lỗi
isChild: true
anchor:  error_reporting
---

## Thông báo lỗi (Error Reporting) {#error_reporting_title}


Thông báo lỗi có thể hữu ích khi bạn tìm kiếm các vấn đề trong ứng dụng, nhưng nó cũng tiết lộ các thông tin 
về cấu trúc của ứng dụng ra ngoài. Để bảo vệ hiệu quả ứng dụng bạn cần phải cài đặt server khác với khi phát triển 
ứng dụng.

### Khi phát triển ứng dụng (Development)

Hiển thị lỗi **Khi phát triển ứng dụng**, cài đặt trong file `php.ini`:

{% highlight ini %}
display_errors = On
display_startup_errors = On
error_reporting = -1
log_errors = On
{% endhighlight %}

> Truyền giá trị `-1` để hiện tất cả các lỗi.
> Hằng `E_ALL` cũng tương tự trong PHP 5.4
> [php.net](http://php.net/function.error-reporting)

Hằng `E_STRICT` trong PHP 5.3.0 không là một phần của `E_ALL`, 
tuy nhiên trong PHP 5.4.0 nó là một phần của `E_ALL`. Có nghĩa là nếu bạn muốn hiển thị tất cả các lỗi 
trong PHP 5.3 phải dùng `-1` hoặc `E_ALL | E_STRICT`.

**Hiển thị tất cả các lỗi theo phiên bản PHP**

* &lt; 5.3 `-1` or `E_ALL`
* &nbsp; 5.3 `-1` or `E_ALL | E_STRICT`
* &gt; 5.3 `-1` or `E_ALL`

### Khi sản phẩm chạy thực tế (Production)

Để ẩn lỗi **khi sản phẩm chạy thực tế**, thiết đặt `php.ini` như sau:

{% highlight ini %}
display_errors = Off
display_startup_errors = Off
error_reporting = E_ALL
log_errors = On
{% endhighlight %}

Với thiết đặt như vậy, ứng dụng sẽ không thông báo lỗi ra bên ngoài nhưng sẽ ghi vào file log trên server. 
Tìm hiểu thêm thông tin:

* [error_reporting](http://php.net/errorfunc.configuration#ini.error-reporting)
* [display_errors](http://php.net/errorfunc.configuration#ini.display-errors)
* [display_startup_errors](http://php.net/errorfunc.configuration#ini.display-startup-errors)
* [log_errors](http://php.net/errorfunc.configuration#ini.log-errors)
