---
layout: page
title:  Phần cơ bản
sitemap: true
---

# Phần cơ bản

## Toán tử so sánh

{% highlight php %}
<?php
$a = 5;   // 5 as an integer

var_dump($a == 5);       // compare value; return true
var_dump($a == '5');     // compare value (ignore type); return true
var_dump($a === 5);      // compare type/value (integer vs. integer); return true
var_dump($a === '5');    // compare type/value (integer vs. string); return false

/**
 * Strict comparisons
 */
if (strpos('testing', 'test')) {    // 'test' is found at position 0, which is 
interpreted as the boolean 'false'
    // code...
}

// vs.

if (strpos('testing', 'test') !== false) {    // true, as strict comparison was made (0 !== false)
    // code...
}
{% endhighlight %}

* [Comparison operators](http://php.net/language.operators.comparison)
* [Comparison table](http://php.net/types.comparisons)
* [Comparison cheatsheet](http://phpcheatsheets.com/index.php?page=compare)

## Câu lệnh điều kiện

### Câu lệnh điều kiện If

Khi dùng câu lệnh 'if/else' bên trong hàm hay class, có 1 quan niệm sai là phải dùng 'else'. Tuy nhiên 
nếu hàm trả về một giá trị, 'else' không cần thiết bởi vì 'return' sẽ kết thúc hàm.

{% highlight php %}
<?php
function test($a)
{
    if ($a) {
        return true;
    } else {
        return false;
    }
}

// vs.

function test($a)
{
    if ($a) {
        return true;
    }
    return false;    // else is not necessary
}

// or even shorter:

function test($a)
{
    return (bool) $a;
}

{% endhighlight %}

* [If statements](http://php.net/control-structures.if)

### Câu lệnh Switch

Câu lệnh switch là cách tốt để tránh gõ quá nhiều lần if và elseif, có vài điều bạn cần lưu ý:

- Câu lệnh switch chỉ so sánh giá trị, không so sánh kiểu dữ liệu (giống như '==')
- Nó sẽ lặp lại qua trình so sánh cho tới khi tìm được giá trị đúng. Nếu không tìm được giá trị đúng, giá 
trị default sẽ được thực thi, nếu đã được khai báo.
- Không có lệnh 'break', nó sẽ tiếp tục thực thi mỗi trường hợp cho đế khi nào có lệnh break hay return.
- Bên trong hàm, dùng 'return' làm giảm bớt nhu cầu của  'break' khi nó kết thúc hàm.

{% highlight php %}
<?php
$answer = test(2);    // the code from both 'case 2' and 'case 3' will be implemented

function test($a)
{
    switch ($a) {
        case 1:
            // code...
            break;             // break is used to end the switch statement
        case 2:
            // code...         // with no break, comparison will continue to 'case 3'
        case 3:
            // code...
            return $result;    // within a function, 'return' will end the function
        default:
            // code...
            return $error;
    }
}
{% endhighlight %}

* [Switch statements](http://php.net/control-structures.switch)
* [PHP switch](http://phpswitch.com/)

## Global namespace (namespace toàn cục)

Khi dùng namespace, bạn có thể thấy rằng các hàm có sẵn trong PHP sẽ bị ẩn bởi các function bạn đã viết.
Để khắc phục, lên kết tới global function bằng cách sử dụng đấu xuyệt ngược trước tên hàm.

{% highlight php %}
<?php
namespace phptherightway;

function fopen()
{
    $file = \fopen();    // Our function name is the same as an internal function.
                         // Execute the function from the global space by adding '\'.
}

function array()
{
    $iterator = new \ArrayIterator();    // ArrayIterator is an internal class. Using its name 
    without a backslash
                                         // will attempt to resolve it within your namespace.
}
{% endhighlight %}

* [Global space](http://php.net/language.namespaces.global)
* [Global rules](http://php.net/userlandnaming.rules)

## Chuỗi

### Nối chuỗi

- Nếu chuỗi dài quá 120 ký tự mỗi dòng, bạn nên dùng nối chuỗi.
- Để cho code dễ đọc, bạn nên dùng toán tử '.=' cho phép gán.
- Khi nối chuỗi trên nhiều dòng cần canh chỉnh lề cho các dòng tiếp theo.


{% highlight php %}
<?php
$a  = 'Multi-line example';    // concatenating assignment operator (.=)
$a .= "\n";
$a .= 'of what not to do';

// vs

$a = 'Multi-line example'      // concatenation operator (.)
    . "\n"                     // indenting new lines
    . 'of what to do';
{% endhighlight %}

* [String Operators](http://php.net/language.operators.string)

### Các kiểu chuỗi

Chuỗi là một tập hợp các ký tự, và có một số kiểu chuỗi khác nhau, nó cung cấp cú pháp hơi khác nhau, với các trạng thái khác nhau.

#### Dấu nháy đơn

Dấu nháy đơn biểu thị chuỗi bình thường, không bao gồm các ký tự đặc biệt hay là biến.

Nếu dùng dấu nháy đơn thì `echo 'some $thing'` sẽ xuất ra màn hình `some $thing`. 
Dấu nháy đôi thì PHP sẽ tìm giá trị của biến `$thing` và hiển thị lỗi nếu biến không được tìm thấy.


{% highlight php %}
<?php
echo 'This is my string, look at how pretty it is.';    // no need to parse a simple string

/**
 * Output:
 *
 * This is my string, look at how pretty it is.
 */
{% endhighlight %}

* [Single quote](http://php.net/language.types.string#language.types.string.syntax.single)

#### Dấu nháy đôi

Dấu nháy đôi không chỉ phân tích biến như đề cập ở trên, mà còn cả các ký tự đặt biệt, như `\n`, `\t`,...

{% highlight php %}
<?php
echo 'phptherightway is ' . $adjective . '.'     // a single quotes example that uses multiple concatenating for
    . "\n"                                       // variables and escaped string
    . 'I love learning' . $code . '!';

// vs

echo "phptherightway is $adjective.\n I love learning $code!"  // Instead of multiple concatenating, double quotes
                                                               // enables us to use a parsable string
{% endhighlight %}


{% highlight php %}
<?php
$juice = 'plum';
echo "I like $juice juice";    // Output: I like plum juice
{% endhighlight %}

Dùng câp dấu ngoặc nhọn cho tên biến để tránh nhầm lẫn `echo "I drank some juice made of {$juice}s";`.

{% highlight php %}
<?php
$juice = 'plum';
echo "I drank some juice made of $juices";    // $juice cannot be parsed

// vs

$juice = 'plum';
echo "I drank some juice made of {$juice}s";    // $juice will be parsed

/**
 * Complex variables will also be parsed within curly brackets
 */

$juice = array('apple', 'orange', 'plum');
echo "I drank some juice made of {$juice[1]}s";   // $juice[1] will be parsed
{% endhighlight %}

* [Double quotes](http://php.net/language.types.string#language.types.string.syntax.double)

#### Cú pháp Nowdoc

Cú pháp Nowdocv được giới thiệu trong 5.3 hoạt động giống như dấu nháy đơn nhưng có thể viết chuỗi nhiều dòng và không cần 
phải nối chuỗi.

{% highlight php %}
<?php
$str = <<<'EOD'             // initialized by <<<
Example of string
spanning multiple lines
using nowdoc syntax.
$a does not parse.
EOD;                        // closing 'EOD' must be on it's own line, and to the left most point

/**
 * Output:
 *
 * Example of string
 * spanning multiple lines
 * using nowdoc syntax.
 * $a does not parse.
 */
{% endhighlight %}

* [Nowdoc syntax](http://php.net/language.types.string#language.types.string.syntax.nowdoc)

#### Cú pháp Heredoc

Cú pháp Heredoc được giới thiệu trong 5.3 hoạt động giống như dấu nháy đôi nhưng có thể viết chuỗi nhiều dòng và không cần 
phải nối chuỗi.

{% highlight php %}
<?php
$a = 'Variables';

$str = <<<EOD               // initialized by <<<
Example of string
spanning multiple lines
using heredoc syntax.
$a are parsed.
EOD;                        // closing 'EOD' must be on it's own line, and to the left most point

/**
 * Output:
 *
 * Example of string
 * spanning multiple lines
 * using heredoc syntax.
 * Variables are parsed.
 */
{% endhighlight %}

* [Heredoc syntax](http://php.net/language.types.string#language.types.string.syntax.heredoc)

### Cái nào nhanh hơn?

Có một sai lầm là người ta thường nghĩ rằng dấu nháy đơn sẽ nhanh hơn nháy đôi, điều đó không đúng.

Nếu bạn chỉ khai báo một chuỗi đơn giản, không có nối biến và không có gì phức tạp thì cả hai cách là như nhau.

Nếu bạn nối nhiều loại chuỗi khác nhau, hay nối biến vào nháy đôi thì kết quả sẽ khác nhau. Nếu làm việc với ít giá trị 
, phép nối chuỗi sẽ nhanh hơn, nếu làm việc với nhiều giá trị, dấu nhay đôi sẽ nhanh hơn.

* [Disproving the Single Quotes Performance Myth](http://nikic.github.io/2012/01/09/Disproving-the-Single-Quotes-Performance-Myth.html)


## Toán tử tam nguyên (Ternary operators)

Toán tử tam nguyên làm cho code thêm súc tích, nhưng thường bị lạm dụng. 

{% highlight php %}
<?php
$a = 5;
echo ($a == 5) ? 'yay' : 'nay';
{% endhighlight %}



{% highlight php %}
<?php
echo ($a) ? ($a == 5) ? 'yay' : 'nay' : ($b == 10) ? 'excessive' : ':(';    // excess nesting, 
sacrificing readability
{% endhighlight %}


{% highlight php %}
<?php
$a = 5;
echo ($a == 5) ? return true : return false;    // this example will output an error

// vs

$a = 5;
return ($a == 5) ? 'yay' : 'nope';    // this example will return 'yay'

{% endhighlight %}

Không cần dùng toán tử tam nguyên để trả về giá trị `true/false`

{% highlight php %}
<?php
$a = 3;
return ($a == 3) ? true : false; // Will return true or false if $a == 3

// vs

$a = 3;
return $a == 3; // Will return true or false if $a == 3

{% endhighlight %}

Tương tự với `===, !==, !=, ==, ...`.

#### Sử dụng ngoặc đơn cho toán tử tam nguyên

Sử dụng ngoặc đơn cho toán tử tam nguyên giúp code dễ đọc hơn.

{% highlight php %}
<?php
$a = 3;
return ($a == 3) ? "yay" : "nope"; // return yay or nope if $a == 3

// vs

$a = 3;
return $a == 3 ? "yay" : "nope"; // return yay or nope if $a == 3
{% endhighlight %}

{% highlight php %}
<?php
return ($a == 3 && $b == 4) && $c == 5;
{% endhighlight %}

{% highlight php %}
<?php
return ($a != 3 && $b != 4) || $c == 5;
{% endhighlight %}

Từ PHP 5.3, có thể bỏ đi phần giữ của toán tử tam nguyên.
Biểu thức "expr1 ?: expr3" trả về expr1 nếu expr1 là TRUE, và ngược lại trả về expr3.

* [Toán tử tam nguyên](http://php.net/language.operators.comparison)

## Khai báo biến

Để giữ cho code "sạch sẽ" các lập trình viên thường khai báo các biến đã được định nghĩa với các tên khác nhau. Điều 
đó làm tăng gấp đôi dung lượng bộ nhớ sử dụng.

{% highlight php %}
<?php
$about = 'A very long string of text';    // uses 2MB memory
echo $about;

// vs

echo 'A very long string of text';        // uses 1MB memory
{% endhighlight %}

* [Các thủ thuật cải thiện hiệu năng](http://web.archive.org/web/20140625191431/https://developers.google.com/speed/articles/optimizing-php)
