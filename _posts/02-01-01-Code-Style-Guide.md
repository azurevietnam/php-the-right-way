---
title: Các Chuẩn viết code
anchor: code_style_guide
---

# Các Chuẩn viết code {#code_style_guide_title}


Cộng đồng PHP rất là rộng lớn và năng động, đóng góp rất nhiều thư viện, framework hay component. Các lập 
 trình viên PHP có thể áp dụng nhiều thư viện hay component, ... khác nhau cho cùng một project. 
 Vì vậy, để tránh xung đột, việc viết code tuân theo một chuẩn là cần thiết.
[Framework Interop Group][fig] cung cấp các bộ quy chuẩn khi viết code được đông đảo lập trình viên áp dụng.
Không phải tất cả các bộ qui chuẩn này đều nói về các quy tắc khi viết code, bạn có thể tham khảo các phần sau:
 [PSR-0][psr0], [PSR-1][psr1], [PSR-2][psr2] và [PSR-4][psr4].
Các dự án như Drupal, Zend, Symfony, CakePHP, phpBB, AWS SDK,
FuelPHP, Lithium, ... cũng viết code theo các nguyên tắt này. Nhưng nếu bạn không thích bạn vẫn có thể code theo cách của mình.

* [Read about PSR-0][psr0]
* [Read about PSR-1][psr1]
* [Read about PSR-2][psr2]
* [Read about PSR-4][psr4]
* [Read about PEAR Coding Standards][pear-cs]
* [Read about Symfony Coding Standards][symfony-cs]

Sử dụng [PHP_CodeSniffer][phpcs] để kiểm tra code, hay dùng plugins cho 
các trình soạn thảo code như [Sublime Text 2][st-cs].

Chỉnh sửa code theo chuẩn với [PHP Coding Standards Fixer][phpcsfixer], 
hay [php.tools][phptools], là plugin của 
[sublime-phpfmt][sublime-phpfmt].

Bạn có thể chạy phpcs bằng lệnh:

    phpcs -sw --standard=PSR2 file.php

Nó sẽ hiện các lỗi và mô tả làm thế nào để sửa. Sẽ rất có ích nếu bạn thêm lệnh này vào Git hook.
Những branch nào chứa code không theo chuẩn không thể thêm vào repository.

Nên sử dụng tiếng anh. 
Comments có thể viết theo thống nhất của team, yêu cầu của khách hàng, ...


[fig]: http://www.php-fig.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md
[psr2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
[pear-cs]: http://pear.php.net/manual/en/standards.php
[symfony-cs]: http://symfony.com/doc/current/contributing/code/standards.html
[phpcs]: http://pear.php.net/package/PHP_CodeSniffer/
[st-cs]: https://github.com/benmatselby/sublime-phpcs
[phpcsfixer]: http://cs.sensiolabs.org/
[phptools]: https://github.com/phpfmt/php.tools
[sublime-phpfmt]: https://github.com/phpfmt/sublime-phpfmt
