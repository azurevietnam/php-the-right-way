---
title: Giao diện dòng lệnh
isChild: true
anchor:  command_line_interface
---

## Giao diện dòng lệnh (Command Line Interface) {#command_line_interface_title}

PHP được tạo để viết ứng dụng web, nhưng nó cũng rất hữu ích cho các chương trình có giao diện dòng lệnh.
Chương trình PHP có giao diện dòng lệnh có thể tự động hóa các tác vụ thông dụng như testing, deployment, 
và ứng dụng administration.

Chương trình PHP có giao diện dòng lệnh rất mạnh mẽ vì chạy ứng dụng trực tiếp không cần phải tạo và bảo mật Giao
diện đồ họa cho nó. Nhưng **đừng** bao giờ đặt các chương trình PHP có giao diện dòng lệnh vào thư mục gốc của web!

Thử chạy php bằng giao diện dòng lệnh:

{% highlight console %}
> php -i
{% endhighlight %}

Tùy chọn `-i` sẽ in ra các cài đặt của PHP giống như hàm [`phpinfo()`][phpinfo].

Tùy chọn `-a` cung cấp một interactive shell, giống với IRB của ruby hay python. Xem thêm [một lệnh phổ biến][cli-options].

Hãy viết một chương trình đơn giản như "Hello, $name". Để thử, trước tiên tạo file `hello.php` như sau:

{% highlight php %}
<?php
if ($argc !== 2) {
    echo "Usage: php hello.php [name].\n";
    exit(1);
}
$name = $argv[1];
echo "Hello, $name\n";
{% endhighlight %}


PHP cài đặt hai biến dựa vào các tham số trong đoạn mã của bạn.
[`$argc`][argc] là biến nguyên chứa tham số **count**.
[`$argv`][argv] là biến mảng chứa mỗi giá trị của tham số.
Tham số đầu tiên luôn là tên của file PHP, trong trường hợp này là `hello.php`.

`exit()` được dùng với một số khác 0 để cho shell biết câu lệnh thất bại. Xem thêm cách sử dụng `exit()` [tại đây][exit-codes].

Để chạy đoạn mã trên:

{% highlight console %}
> php hello.php
Usage: php hello.php [name]
> php hello.php world
Hello, world
{% endhighlight %}


 * [Xem thêm về chạy PHP trên dòng lệnh][php-cli]
 * [Xem thêm về cài đặt Windows để chạy PHP trên dòng lệnh][php-cli-windows]


[phpinfo]: http://php.net/function.phpinfo
[cli-options]: http://php.net/features.commandline.options
[argc]: http://php.net/reserved.variables.argc
[argv]: http://php.net/reserved.variables.argv
[exit-codes]: http://www.gsp.com/cgi-bin/man.cgi?section=3&amp;topic=sysexits
[php-cli]: http://php.net/features.commandline
[php-cli-windows]: http://php.net/install.windows.commandline
