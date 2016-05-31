---
title: Băm password
isChild: true
anchor:  password_hashing
---

## Băm password (Password Hashing) {#password_hashing_title}


Trong các ứng dụng có chức năng đăng nhập, username và password được lưu trong database và được dùng để xác thcu75  
khi đăng nhập.

Điều quan trọng là bạn cần [_băm_][3] password trước khi lưu nó vào database. Password hashing là quá trình 
một chiều, không thể đảo ngược để giấu mật khẩu thực của người dùng. Nó cung cấp một chuỗi có chiều dài cố định , 
không thể truy ngược, và hai chuỗi giống nhau sau khi băm sẽ trả về cùng một chuỗi. Nếu password không được băm, 
và database của bạn có thể được truy cập bởi bên thứ ba, khi đó tất cả user của bạn có thể bị mất tải khoản. 

**Hashing passwords with `password_hash`**

In PHP 5.5 `password_hash()` was introduced. At this time it is using BCrypt, 
the strongest algorithm currently
supported by PHP. It will be updated in the future to support more algorithms 
as needed though. The `password_compat`
library was created to provide forward compatibility for PHP >= 5.3.7.

bên dưới là ví dụ băm chuỗi, và kiểm tra hàm băm lần nữa với chuỗi mới. 
Bởi vì hai chuỗi gốc khác nhau ('secret-password' vs. 'bad-password') nên login thất bại.

{% highlight php %}
<?php
require 'password.php';

$passwordHash = password_hash('secret-password', PASSWORD_DEFAULT);

if (password_verify('bad-password', $passwordHash)) {
    // Correct Password
} else {
    // Wrong password
}
{% endhighlight %}  


* [Learn about `password_hash()`] [1]
* [`password_compat` for PHP >= 5.3.7 && < 5.5] [2]
* [Learn about hashing in regards to cryptography] [3]
* [PHP `password_hash()` RFC] [4]


[1]: http://php.net/function.password-hash
[2]: https://github.com/ircmaxell/password_compat
[3]: http://en.wikipedia.org/wiki/Cryptographic_hash_function
[4]: https://wiki.php.net/rfc/password_hash
