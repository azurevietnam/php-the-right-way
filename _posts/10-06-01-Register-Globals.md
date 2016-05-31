---
isChild: true
anchor:  register_globals
---

## Register Globals {#register_globals_title}

**NOTE:** kể từ PHP 5.4.0 `register_globals` đã bị loại bỏ và không thể sử dụng nữa.

Khi bật `register_globals`, các biến `$_POST`, `$_GET` và `$_REQUEST` có thể được truy cập một cách toàn cục. 
Dẫn tới các vấn đề bảo mật.

Ví dụ: `$_GET['foo']` có thể được truy cấp bằng biến `$foo`.
Nếu đang dùng PHP < 5.4.0 __chắc rằng__  `register_globals` __đã tắt__.

* [Register_globals in the PHP manual](http://php.net/security.globals)
