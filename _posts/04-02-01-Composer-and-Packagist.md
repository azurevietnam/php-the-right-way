---
title: Composer và Packagist
isChild: true
anchor:  composer_and_packagist
---

## Composer và Packagist {#composer_and_packagist_title}

Composer là dependency manager cho PHP. Liệt kê các dependencies trong project của bạn tại  
file `composer.json` và,
với vài lệnh đơn giản, Composer sẽ tự động tải dependencies về và cài đặt autoload cho bạn. 
Composer tương tự như NPM của node.js, hay Bundler của Ruby.

Có nhiều thư viện PHP tương thích với Composer, chúng được liệt kê tại [Packagist].

### Cài đặt Composer

Cài đặt trực tiếp trong thư mục làm việc của bạn (locally) hoặc cài đặt toàn cục (globally) 
(ví dụ. /usr/local/bin, khuyến khích).
Để cài Composer globally:

{% highlight console %}
curl -sS https://getcomposer.org/installer | php
mv composer.phar /usr/local/bin/composer
{% endhighlight %}

**Chú ý:** nếu không thành công, thực thi lệnh `mv` một lần nữa với `sudo`.

Nó sẽ download file `composer.phar` (là file PHP binary archive). Bạn có thể chạy file này với `php` 
để quản lý các dependencies.

**Vui lòng chú ý:** nếu bạn đưa code trực tiếp vào trình phiên dịch, vui lòng đọc code online trước để đảm bào an toàn.

#### Cài đặt trên Windows

Các dễ nhất là tải file cài đặt [ComposerSetup], nó sẽ cài đặt globally và cài đặt biến `$PATH` 
của bạn và  bạn có thể gọi `composer` ở mọi nới bằng command line.

### Cài đặt Composer thủ công

Manually installing Composer is an advanced technique; however, there are various reasons why a 
developer might prefer this method vs. using the interactive installation routine. The interactive
installation checks your PHP installation to ensure that:

Cài đặt Composer thủ công là một kỹ thuật nân cao; tuy nhiên có nhiều lý do để một lập trình viên chọn cách này 
thay vì cài đặt tự động vì nó sẽ kiểm tra xem:

- phiên bản PHP hiện tại
- file `.phar` có được thực thi đúng cách
- kiểm tra quyền của thư mục
- chắc rằng các problematic extensions không được load.
- chắc rằng các cài đặt trong file `php.ini` đã được bật.

Trong khi cài đặt thủ công không thực hiện các bước kiểm tra đó, bạn phải quyết định xem sự đánh đổi đó  
có xứng đáng không. 
Cách cài đặt thủ công:

{% highlight console %}
curl -s https://getcomposer.org/composer.phar -o $HOME/local/bin/composer
chmod +x $HOME/local/bin/composer
{% endhighlight %}

Đường dẫn `$HOME/local/bin` (hay thư mục khác mà bạn chọn) nên có trong biến môi trường `$PATH`.

Khi trong documentation nói cài Composer bằng lệnh `php composer.phar install`, bạn có thể thay thế bằng:

{% highlight console %}
composer install
{% endhighlight %}

Phần này giả sử bạn cài đặt composer globally.

### Khai báo và cài đặt Dependencies

Composer quản lý các dependency trong dự án của bạn trong file `composer.json`. Bạn có thể quản lý nó bằng 
tay nếu muốn, hoặc sử dụng composer. Lệnh `composer require` để thêm dependency, nếu bạn không có file `composer.json`, 
một file mới sẽ được tạo. Ví dụ muốn thêm dependency [Twig] vào project:

{% highlight console %}
composer require twig/twig:~1.8
{% endhighlight %}

Một các thay thế, lệnh `composer init` sẽ hướng dẫn bạn tạo một file `composer.json`. 
Trong hai cách, bạn đều phải tạo file `composer.json` để thông báo cho Composer 
tải và cài đặt các dependencies vào thư mục `vendor/`. Nó cũng áp dụng cho project 
bạn đã download có file `composer.json` rồi:

{% highlight console %}
composer install
{% endhighlight %}

Tiếp theo, thêm dòng này vào file chính của ứng dụng để nói cho PHP dùng autoloader của Composer  
cho các dependencies của project.

{% highlight php %}
<?php
require 'vendor/autoload.php';
{% endhighlight %}

Bây giờ bạn đã có thể sử dụng các dependencies, và chúng sẽ được load tự động khi cần.

### Nâng cấp các dependencies

Composer tạo file tên là `composer.lock` để chứa chính xách phiên bản của mỗi package đã download khi bạn 
chạy lệnh `composer install`lần đầu. Nếu bạn chia sẻ project của mình với người khác và file 
`composer.lock` cũng được chia sẻ, khi họ chạy lệnh `composer install`, họ sẽ tải về cùng phiên bản với bạn. 
để update các dependencies, chạy lệnh `composer update`.

Sẽ hữu ích hơn nếu bạn khai báo phiên bản một cách linh hoạt. Ví dụ, `~1.8` có nghĩa "tất cả mọi thứ 
mới hơn bản `1.8.0` nhưng cũ hơn `2.0.x-dev`". Bạn có thể dùng `*` như sau `1.8.*`. Bây giờ, `composer update` 
sẽ nâng cấp tất cả các dependency lên phiên bản mới nhất phù hợp với khai báo của bạn.

### Thông báo Update

Để nhận thông báo về phiên bản mới bạn có thể đăng ký [VersionEye], một dịch vụ có thể ghi lại tài khoản 
Github hay BitBucket của bạn cho file `composer.json` và gửi email cho bạn.

### Kiểm tra các vấn đề bảo mật vủa các dependencies

[Security Advisories Checker] là một web service và công cụ command-line, cả hai will kiểm tra file `composer.lock`
và thông báo cho bạn nếu bạn cần nâng cấp bất kỳ dependency nào.

### Quản lý global dependencies với Composer

Tất cả bạn cần là thêm vào trước lệnh bằng `global`. 
Ví dụ bạn muốn cài đặt PHPUnit globally:

{% highlight console %}
composer global require phpunit/phpunit
{% endhighlight %}

Nó sẽ tạo thư mục `~/.composer` nơi global dependencies thuộc về. Để có các gói cài đặt hữu dụng ở 
mọi nơi, bạn cần thêm thư mục `~/.composer/vendor/bin` vào biến `$PATH`.

* [Learn about Composer]

[Packagist]: http://packagist.org/
[Twig]: http://twig.sensiolabs.org
[VersionEye]: https://www.versioneye.com/
[Security Advisories Checker]: https://security.sensiolabs.org/
[Learn about Composer]: http://getcomposer.org/doc/00-intro.md
[ComposerSetup]: https://getcomposer.org/Composer-Setup.exe
