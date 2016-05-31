---
title: Các mô hình lập trình
isChild: true
anchor:  programming_paradigms
---

## Các mô hình lập trình (Programming Paradigms) {#programming_paradigms_title}

PHP là một ngôn ngữ linh hoạt, mạnh mẽ, hỗ trợ nhiều kỹ thuật lập trình khác nhau. PHP được phát 
triển và bổ sung nhiều tính năng mới như lập trình hướng đối tượng trong PHP 5.0 (2004), hàm vô danh
 (anonymous function) và namspace trong PHP 5.3 (2009), trait trong PHP 5.4 (2012).

### Lập trình hướng đối tượng (Object-oriented Programming)

PHP có đầy đủ các tính năng của lập trình hướng đối tượng như hỗ trợ class, 
abstract class,interfaces, kế thừa, constructors, cloning, exceptions, ...

* [Tìm hiểu thêm về Object-oriented PHP][oop]
* [Tìm hiểu thêm về Traits][traits]

### Lập trình hàm (Functional Programming)

PHP hỗ trợ first-class functions, có nghĩa là là bạn có thể gán hàm vào biến. 
Các hàm do lập trình viên khai báo và các hàm có sẵn có thể liên kết tới một biến và được gọi khi cần.
Recursion, a feature that allows a function to call itself, is supported by the language, và một hàm có thể
trả về (return) một hàm khác.

Hàm vô danh (with support for closures) được hỗ trợ trong phiên bản PHP 5.3 (2009).

PHP 5.4 đã thêm chức năng bắt buộc closure nằm trong phạm vi object và cũng cải thiện hỗ trợ cho
 callables như nó có thể dùng để thay thế anonymous functions trong hầu hết các tình huống.
 
* Tiếp tục tìm hiểu về [Functional Programming in PHP](./pages/Functional-Programming.html)
* [Tìm hiểu về Anonymous Functions][anonymous-functions]
* [Tìm hiểu về Closure class][closure-class]
* [Tìm hiểu về Closures RFC][closures-rfc]
* [Tìm hiểu về Callables][callables]
* [Tìm hiểu về dynamically invoking functions with `call_user_func_array()`][call-user-func-array]

### Lập trình Meta (Meta Programming)

PHP Hỗ trợ nhiều dạng của lập trình meta thông qua các kỹ thuật như Reflection API 
và Magic Methods. Một số Magic Methods như `__get()`, `__set()`, `__clone()`, `__toString()`, `__invoke()`, ... 
cho phép các lập trình viên có thể tác động tới các hành vi (behavior) của class. 
Các lập trình viên Ruby developers thường nói PHP thiếu `method_missing`, như thật ra đó là
 `__call()` và `__callStatic()`.

* [Tìm hiểu về Magic Methods][magic-methods]
* [Tìm hiểu về Reflection][reflection]
* [Tìm hiểu về Overloading][overloading]


[oop]: http://php.net/language.oop5
[traits]: http://php.net/language.oop5.traits
[anonymous-functions]: http://php.net/functions.anonymous
[closure-class]: http://php.net/class.closure
[closures-rfc]: https://wiki.php.net/rfc/closures
[callables]: http://php.net/language.types.callable
[call-user-func-array]: http://php.net/function.call-user-func-array
[magic-methods]: http://php.net/language.oop5.magic
[reflection]: http://php.net/intro.reflection
[overloading]: http://php.net/language.oop5.overloading

