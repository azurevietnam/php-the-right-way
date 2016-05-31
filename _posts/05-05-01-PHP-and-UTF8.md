---
title:   Làm việc với UTF-8
isChild: true
anchor:  php_and_utf8
---

## Làm việc với UTF-8 {#php_and_utf8_title}

_Phần này được viết bởi [Alex Cabal](https://alexcabal.com/) tại 
[PHP Best Practices](https://phpbestpractices.org/#utf-8)_.

### Hãy cẩn thận, tỉ mỉ, và thống nhất!

Hiện tại PHP không hỗ trợ Unicode ở cấp độ thấp. Có nhiều cách để chắc rằng các chuỗi UTF-8 được thực thi, 
nhưng rất khó khăn, và yêu cầu phải đào sâu vào từng cấp độ của ứng dụng web, từ HTML, SQL tới PHP. Chúng ta sẽ nói qua các phần thông dụng.

### UTF-8 tại cấp độ PHP


Toán tử chuỗi cơ bản như nối chuỗi, gán chuỗi không cần quan tâm UTF-8. Nhưng đa số các hàm chuỗi như 
`strpos()` và `strlen()` cần một sự cân nhắc cẩn thận. Các hàm này thường có hàm tương ứng với `mb_*` 
ở phía trước như `mb_strpos()` và `mb_strlen()`, các hàm này được cung cấp tại [Multibyte String Extension], 
và được thiết kế đặc biệt để làm việc với các chuỗi Unicode.

Bạn cần dùng các hàm `mb_*` bất cứa khi nào cần làm việc với chuỗi Unicode. Ví dụ như `substr()` trên chuỗi UTF-8, 
bạn nên dùng hàm `mb_substr()` thay thế. Không phải lúc nào cũng có hàm `mb_*` tương ứng.

Bạn nên dùng hàm `mb_internal_encoding()` trên đầu mỗi file PHP và hàm `mb_http_output()` ngay sau nó 
nếu mã PHP của bạn xuất kết quả ra trình duyệt, việc này sẽ khiến bạn khá đau đầu.

Thêm vào đó, nhiều hàm chuỗi trong PHP có tham số tùy chọn cho bạn khai báo character encoding, 
bạn nên khai báo UTF-8 trong tùy chọn. Ví dụ `htmlentities()` và `htmlspecialchars()` (trong PHP 5.4 
tùy chọn mặc định của encoding là UTF-8).

Cuối cùng, nếu bạn đang xây dựng một ứng dụng được phân phối và không chắc rằng `mbstring` có bật hay không, 
bạn nên sử dụng package [patchwork/utf8] của Composer. Nó sẽ sửng dụng `mbstring` nếu có sẵn, nếu không 
dùng các hàm non UTF-8.

[Multibyte String Extension]: http://php.net/book.mbstring
[patchwork/utf8]: https://packagist.org/packages/patchwork/utf8

### UTF-8 cấp độ Database

Khi dùng PHP để truy cập MySQL, vẫn có khả năng dữ liệu của bạn sẽ bị lưu dưới dạng non-UTF-8 cho dù bạn 
đã làm theo các ví dụ bên trên.

Để lưu chuỗi vào MySQL dạng UTF-8, cài đặt encoding cho Database và các bảng là `utf8mb4`, 
và dùng `utf8mb4` trong chuỗi kết nối của PDO.

Note that you must use the `utf8mb4` character set for complete UTF-8 support, not the `utf8` 
character set!

### UTF-8 cấp độ trình duyệt

Hàm `mb_http_output()` giúp PHP xuất chuỗi UTF-8 ra trình duyệt. 
Cách khác là dùng thể meta charset
[charset `<meta>` tag](http://htmlpurifier.org/docs/enduser-utf8.html) trong thẻ `<head>` của trang html. 
Cách này hợp lệ, nhưng cài đặt charset trong `Content-Type` header sẽ nhanh hơn nhiều 
[xem thêm](https://developers.google.com/speed/docs/best-practices/rendering#SpecifyCharsetEarly).

{% highlight php %}
<?php
// Tell PHP that we're using UTF-8 strings until the end of the script
mb_internal_encoding('UTF-8');
 
// Tell PHP that we'll be outputting UTF-8 to the browser
mb_http_output('UTF-8');
 
// Our UTF-8 test string
$string = 'Êl síla erin lû e-govaned vîn.';
 
// Transform the string in some way with a multibyte function
// Note how we cut the string at a non-Ascii character for demonstration purposes
$string = mb_substr($string, 0, 15);
 
// Connect to a database to store the transformed string
// See the PDO example in this document for more information
// Note the `charset=utf8mb4` in the Data Source Name (DSN)
$link = new PDO(
    'mysql:host=your-hostname;dbname=your-db;charset=utf8mb4',
    'your-username',
    'your-password',
    array(
        PDO::ATTR_ERRMODE => PDO::ERRMODE_EXCEPTION,
        PDO::ATTR_PERSISTENT => false
    )
);
 
// Store our transformed string as UTF-8 in our database
// Your DB and tables are in the utf8mb4 character set and collation, right?
$handle = $link->prepare('insert into ElvishSentences (Id, Body) values (?, ?)');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->bindValue(2, $string);
$handle->execute();
 
// Retrieve the string we just stored to prove it was stored correctly
$handle = $link->prepare('select * from ElvishSentences where Id = ?');
$handle->bindValue(1, 1, PDO::PARAM_INT);
$handle->execute();
 
// Store the result into an object that we'll output later in our HTML
$result = $handle->fetchAll(\PDO::FETCH_OBJ);

header('Content-Type: text/html; charset=UTF-8');
?><!doctype html>
<html>
    <head>
        <meta charset="UTF-8">
        <title>UTF-8 test page</title>
    </head>
    <body>
        <?php
        foreach($result as $row){
            print($row->Body);  // This should correctly output our transformed UTF-8 string 
            to the browser
        }
        ?>
    </body>
</html>
{% endhighlight %}

### Tham khảo

* [PHP Manual: String Operations](http://php.net/language.operators.string)
* [PHP Manual: String Functions](http://php.net/ref.strings)
    * [`strpos()`](http://php.net/function.strpos)
    * [`strlen()`](http://php.net/function.strlen)
    * [`substr()`](http://php.net/function.substr)
* [PHP Manual: Multibyte String Functions](http://php.net/ref.mbstring)
    * [`mb_strpos()`](http://php.net/function.mb-strpos)
    * [`mb_strlen()`](http://php.net/function.mb-strlen)
    * [`mb_substr()`](http://php.net/function.mb-substr)
    * [`mb_internal_encoding()`](http://php.net/function.mb-internal-encoding)
    * [`mb_http_output()`](http://php.net/function.mb-http-output)
    * [`htmlentities()`](http://php.net/function.htmlentities)
    * [`htmlspecialchars()`](http://php.net/function.htmlspecialchars)
* [PHP UTF-8 Cheatsheet](http://blog.loftdigital.com/blog/php-utf-8-cheatsheet)
* [Handling UTF-8 with PHP](http://www.phpwact.org/php/i18n/utf-8)
* [Stack Overflow: What factors make PHP Unicode-incompatible?](http://stackoverflow.com/questions/571694/what-factors-make-php-unicode-incompatible)
* [Stack Overflow: Best practices in PHP and MySQL with international strings](http://stackoverflow.com/questions/140728/best-practices-in-php-and-mysql-with-international-strings)
* [How to support full Unicode in MySQL databases](http://mathiasbynens.be/notes/mysql-utf8mb4)
* [Bringing Unicode to PHP with Portable UTF-8](http://www.sitepoint.com/bringing-unicode-to-php-with-portable-utf8/)
* [Stack Overflow: DOMDocument loadHTML does not encode UTF-8 correctly](http://stackoverflow.com/questions/8218230/php-domdocument-loadhtml-not-encoding-utf-8-correctly)
