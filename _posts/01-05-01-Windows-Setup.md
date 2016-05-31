---
title: Cài đặt PHP trên Windows
isChild: true
anchor:  windows_setup
---

## Cài đặt PHP trên Windows {#windows_setup_title}

Tải bản cài đặt tại [windows.php.net/download][php-downloads]. Sau khi cài đặt, 
bạn nên cài đặt [PATH][windows-path] tới dường dẫn của thư mục PHP 
(nơi chứa file php.exe) và bạn có thể chạy PHP mọi nơi.

Bạn có thể dùng webserver cung cấp sẵn từ PHP 5.4+ và không cần lo lắng về việc cấu hình. 
Bạn cũng có thể cài đặt các gói "All-in-one" "All-in-one"
 như [Web Platform Installer][wpi], [XAMPP][xampp], [EasyPHP][easyphp], 
     [OpenServer][openserver] and [WAMP][wamp] sẽ cài đặt PHP và Apache, SQL server.

Bạn có thể dùng [phpmanager][phpmanager] (GUI plugin của IIS7) để quản lý và cấu hình. Xem thêm tại [php-iis].

Việc phát triển ứng dụng trong nhiều môi trường khác nhau có thể làm xuất hiện nhiều lỗi. 
Nếu bạn đang phát triển ứng dụng trên Windows và muốn chuyển sang Linux (hay khác) 
 thì nên cân nhắc sử dụng [Virtual Machine](#virtualization_title).

Chris Tankersley có một bài blog rất hữu ích nói về các công cụ 
[phát triển PHP trên Windows][windows-tools].

[easyphp]: http://www.easyphp.org/
[phpmanager]: http://phpmanager.codeplex.com/
[openserver]: http://open-server.ru/
[wamp]: http://www.wampserver.com/en/
[php-downloads]: http://windows.php.net/download/
[php-iis]: http://php.iis.net/
[windows-path]: http://www.windows-commandline.com/set-path-command-line/
[windows-tools]: http://ctankersley.com/2015/07/01/developing-on-windows/
[wpi]: http://www.microsoft.com/web/downloads/platform.aspx
[xampp]: http://www.apachefriends.org/en/xampp.html
