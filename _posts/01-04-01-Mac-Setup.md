---
title: Cài đặt PHP trên MAC
isChild: true
anchor:  mac_setup
---

## Cài đặt PHP trên MAC {#mac_setup_title}


Có nhiều cách để cài đặt PHP trên OS X.

### Cài PHP từ Homebrew

[Homebrew] là một package manager mạnh mẽ cho OS X, sẽ giúp chúng ta cài đặt PHP và các phần mở rộng dễ dàng.
[Homebrew PHP] Chứa cách cài đặt PHP cho Homebrew.

Bạn có thể cài `php53`, `php54`, `php55`, `php56` hoặc `php70` dùng câu lệnh `brew install`, và chuyển đổi
qua lại giữa chúng bằng cách thay đổi biến `PATH`. Bạn có thể dùng [brew-php-switcher][brew-php-switcher] để chuyển đồi một cách tự động.

### Cài đặt qua Macports

[MacPorts] là một dự án mã nguồn mở để thiết kế một hệ thống dễ sử dụng cho biên dịch, cài đặt và nâng cấp 
ngay cả trên command-line, X11 hay Aqua dựa vào các phần mềm mã nguồn mở trên OS X.


Hiện tại bạn có thể cài `php54`, `php55`, `php56` hay `php70` bằng lệnh `port install`, ví dụ:

    sudo port install php56
    sudo port install php70

Dùng lệnh `select` để chuyển phiên bản PHP:

    sudo port select --set php php70

### Cài từ phpbrew

[phpbrew] có thể cài đặt và quản lý nhiều phiên bản PHP khác nhau, rất hữu ích nếu bạn có hai project
 chạy trên hai phiên bản PHP khác nhau.

### Cài đặt với [Liip's binary installer][php-osx.liip.ch]

Nó không ghi đè lên phiên bản PHP mà MAC đã cài, mà cài đặt trên một thư mục khác (/usr/local/php5).

### Biên dịch từ Source

[compile it yourself][mac-compile].
Bạn cần cài [Xcode][xcode-gcc-substitution] hoặc Apple's substitute
["Command Line Tools for XCode"] tải trên Apple's Mac Developer Center.

### All-in-One Installers

"All-in-one" installers như [MAMP][mamp-downloads] and [XAMPP][xampp] sẽ cài đặt PHP và Apache, Nginx hoặc SQL server.


[Homebrew]: http://brew.sh/
[Homebrew PHP]: https://github.com/Homebrew/homebrew-php#installation
[MacPorts]: https://www.macports.org/install.php
[phpbrew]: https://github.com/phpbrew/phpbrew
[php-osx.liip.ch]: http://php-osx.liip.ch/
[mac-compile]: http://php.net/install.macosx.compile
[xcode-gcc-substitution]: https://github.com/kennethreitz/osx-gcc-installer
["Command Line Tools for XCode"]: https://developer.apple.com/downloads
[mamp-downloads]: http://www.mamp.info/en/downloads/
[xampp]: http://www.apachefriends.org/en/xampp.html
[brew-php-switcher]: https://github.com/philcook/brew-php-switcher
