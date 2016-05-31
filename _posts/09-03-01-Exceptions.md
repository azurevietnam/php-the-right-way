---
title: Ngoại lệ
isChild: true
anchor:  exceptions
---

## Ngoại lệ (Exceptions) {#exceptions_title}

Exceptions là một thành phần cơ bản của các ngôn ngữ lập trình, nhưng thường bị các lập trình viên PHP bỏ qua.
Các ngôn ngữ như Ruby quản lý Exception rất nghiêm ngặc, bất cứ khi nào có lỗi, như HTTP request thất bại, hay 
câu truy vần Database sai, ... Ruby sẽ ngay lập tức ném ra một ngoại lệ cho biết có lỗi xảy ra.

PHP khá thoải mái với điều này, gọi hàm `file_get_contents()` thường trả về `FALSE` một warning.
Nhiều framwork cũ như CodeIgniter chỉ trả về false.

Một vấn đề khác là khi các class tự động xuất lỗi ra màn hình và ngừng chạy. Khi làm điều đó bạn 
không cho các lập trình viên khác cơ hội quản lý lỗi đó. 
Ngoại lệ nên được ném ra để làm cho lập trình viên nhận ra lỗi, và tìm cách để quản lí nó.

{% highlight php %}
<?php
$email = new Fuel\Email;
$email->subject('My Subject');
$email->body('How the heck are you?');
$email->to('guy@example.com', 'Some Guy');

try
{
    $email->send();
}
catch(Fuel\Email\ValidationFailedException $e)
{
    // The validation failed
}
catch(Fuel\Email\SendingFailedException $e)
{
    // The driver could not send the email
}
finally
{
    // Executed regardless of whether an exception has been thrown, 
    and before normal execution resumes
}
{% endhighlight %}

### SPL Exceptions

Class `Exception` ccung cấp rất ít debugging context cho lập trình viên; tuy nhiên để khắc phục điều này, 

bạn có thể tạo một class kế thừa `Exception`:

{% highlight php %}
<?php
class ValidationException extends Exception {}
{% endhighlight %}

Bạn có thể thêm nhiều khối catch block và quản lý các ngoại lệ khác nhau, dẫn tới sự thành lập của nhiều 
ngoại lệ tùy chọn, một vài trong số chúng từ chối sử dụng PL Exceptions được cung cấp trong [SPL extension][splext].

Nếu giả sử bạn dùng hàm `__call()` và một phương thức không hợp lệ được yêu cầu, sau đó thay vì ném ra một ngoại lệ 
không rõ ràng bằng Exception chuẩn, hay tạo một Exception tùy chọn, bạn có thể `throw new BadMethodCallException;`.

* [Đọc thêm về Exceptions][exceptions]
* [Đọc thêm về SPL Exceptions][splexe]
* [Nesting Exceptions In PHP][nesting-exceptions-in-php]
* [Exception Best Practices in PHP 5.3][exception-best-practices53]


[splext]: /#standard_php_library
[exceptions]: http://php.net/language.exceptions
[splexe]: http://php.net/spl.exceptions
[nesting-exceptions-in-php]: http://www.brandonsavage.net/exceptional-php-nesting-exceptions-in-php/
[exception-best-practices53]: http://ralphschindler.com/2010/09/15/exception-best-practices-in-php-5-3
