---
layout: page
title:  Lập trình chức năng trong PHP
sitemap: true
---

# Lập trình chức năng trong PHP

PHP hỗ trợ first-class functions, có nghĩa là bạn có thể gán hàm vào biến (các hàm có sẵn và các hàm được xây dựng). 
Hàm có thể được truyền như tham số cho hàm khác và hàm có thể trả về hàm khác (higher-order functions).

Đệ qui được PHP hỗ trợ nhưng đa số code PHP tập trung vào sự lặp lại.

Hàm vô danh (with support for closures) được hỗ trợ trong phiên bản PHP 5.3 (2009).

PHP 5.4 đã thêm chức năng bắt buộc closure nằm trong phạm vi object và cũng cải thiện hỗ trợ cho
 callables như nó có thể dùng để thay thế anonymous functions trong hầu hết các tình huống.

Công dụng phổ biến nhất của higher-order functions là khi thực thi strategy pattern. Hàm có sẵn `array_filter()` 
đòi hỏi cả array input (dữ liệu) và hàm (trategy hay callback) được dùng như là hàm filter trên mỗi phần tử array.

{% highlight php %}
<?php
$input = array(1, 2, 3, 4, 5, 6);

// Creates a new anonymous function and assigns it to a variable
$filter_even = function($item) {
    return ($item % 2) == 0;
};

// Built-in array_filter accepts both the data and the function
$output = array_filter($input, $filter_even);

// The function doesn't need to be assigned to a variable. This is valid too:
$output = array_filter($input, function($item) {
    return ($item % 2) == 0;
});

print_r($output);
{% endhighlight %}

Closure là một hàm vô danh có thể truy cập các biến được nhập từ bên ngoài mà không cần dùng tới biến toàn cục. 
Về mặt lý thuyết, closure là một hàm với vài tham số bị đóng bởi môi trường khi nó được khai báo. 
Closure có thể hoạt động trong các phạm vi biến hạn chế một cách "gọn gàn".

Trong ví dụ tiếp theo, chúng ta dùng closures để khai báo hàm trả về một hàm filter cho hàm `array_filter()`, 

{% highlight php %}
<?php
/**
 * Creates an anonymous filter function accepting items > $min
 *
 * Returns a single filter out of a family of "greater than n" filters
 */
function criteria_greater_than($min)
{
    return function($item) use ($min) {
        return $item > $min;
    };
}

$input = array(1, 2, 3, 4, 5, 6);

// Use array_filter on a input with a selected filter function
$output = array_filter($input, criteria_greater_than(3));

print_r($output); // items > 3
{% endhighlight %}

Mỗi hàm filter trong hệ thống chỉ chấp nhận các phần tử lớn hơn giá trị tối thiểu. 
Hàm filter trả về bởi 
`criteria_greater_than` là một closure với tham số `$min` bị đóng bởi giá trị trong phạm vi. 
(đưa ra một tham số khi `criteria_greater_than` được gọi).

* [Đọc thêm về hàm vô danh][anonymous-functions]
* [Đọc thêm về Closures RFC][closures-rfc]
* [Gọi hàm với `call_user_func_array()`][call-user-func-array]


[anonymous-functions]: http://php.net/functions.anonymous
[closures-rfc]: https://wiki.php.net/rfc/closures
[call-user-func-array]: http://php.net/function.call-user-func-array
