---
isChild: true
anchor:  opcode_cache
---

## Opcode Cache {#opcode_cache_title}

Khi file PHP được thực thi, đầu tiên nó được biên dịch sang opcode và, chỉ sau đó, 
opcode được thực thi.
Nếu file PHP không được thay đổi, opcode cũng không đổi.

Opcode cache giúp tránh biên dịch không cần thiết bằng cách lưu trữ opcode trong bộ nhớ và dùng lại khi được gọi. 
Cài dặt opcode cần một khoản thời gian, và ứng dụng của bạn sẽ được tăng tốc đáng kể.



Trong PHP 5.5, có sẵn opcode cache được gọi là [OPcache][opcache-book]. 
Nó cũng có torng các phiên bản trước.

Xem thêm về opcode cache:

* [OPcache][opcache-book] (built-in since PHP 5.5)
* [APC] (PHP 5.4 and earlier)
* [XCache]
* [Zend Optimizer+] (part of Zend Server package)
* [WinCache] (extension for MS Windows Server)
* [list of PHP accelerators on Wikipedia][PHP_accelerators]


[opcache-book]: http://php.net/book.opcache
[APC]: http://php.net/book.apc
[XCache]: http://xcache.lighttpd.net/
[Zend Optimizer+]: http://www.zend.com/en/products/zend_server
[WinCache]: http://www.iis.net/download/wincacheforphp
[PHP_accelerators]: http://en.wikipedia.org/wiki/List_of_PHP_accelerators
