---
isChild: true
title:   Tương tác với Databases
anchor:  databases_interacting
---

## Tương tác với Databases {#databases_interacting_title}

Khi các lập trình viên mới học PHP, họ thường kết hợp các tương tác với database với code giao điện như sau:

{% highlight php %}
<ul>
<?php
foreach ($db->query('SELECT * FROM table') as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>";
}
?>
</ul>
{% endhighlight %}

Cách viết code như vậy rất khó debug, khó test, khó đọc read nó sẽ xuất ra rất nhiều field nếu bạn không giới hạn.

Có vài giải pháp cho vấn đề này - tùy thuộc bạn thích [OOP](./#object-oriented-programming) hay
[functional programming](./#functional-programming) hơn.

Theo một số bước cơ bản sau:

{% highlight php %}
<?php
function getAllFoos($db) {
    return $db->query('SELECT * FROM table');
}

foreach (getAllFoos($db) as $row) {
    echo "<li>".$row['field1']." - ".$row['field1']."</li>"; // BAD!!
}
{% endhighlight %}

Đặt hai đoạn trên vào hai file khác nhau, code của bạn sẽ trông gọn gàng và tách biệt hơn.

Tạo một class và đặt phương thức trên vào, và bạn có một "Model". Tạo một file `.php` đơn giản để đặt phần code giao diện 
và bạn có một "View" gần giống với mô hình [MVC] - một mô hình phổ biến cho hầu hết các [frameworks](/#frameworks).

**foo.php**

{% highlight php %}
<?php
$db = new PDO('mysql:host=localhost;dbname=testdb;charset=utf8', 'username', 'password');

// Make your model available
include 'models/FooModel.php';

// Create an instance
$fooModel = new FooModel($db);
// Get the list of Foos
$fooList = $fooModel->getAllFoos();

// Show the view
include 'views/foo-list.php';
{% endhighlight %}


**models/FooModel.php**

{% highlight php %}
<?php
class FooModel
{
    protected $db;

    public function __construct(PDO $db)
    {
        $this->db = $db;
    }

    public function getAllFoos() {
        return $this->db->query('SELECT * FROM table');
    }
}
{% endhighlight %}

**views/foo-list.php**

{% highlight php %}
<?php foreach ($fooList as $row): ?>
    <?= $row['field1'] ?> - <?= $row['field1'] ?>
<?php endforeach ?>
{% endhighlight %}

Điều này rất giống với frameworks hiện đại, mặc dù có chút thủ công. Làm như vậy sẽ giúp bạn 
tránh được một số rắc rối khi [unit-test](./#unit-testing) ứng dụng.

[PHPBridge] có môt bài rất hay về [tạo class Data] rất tốt cho các lập trình viên mới quen với khái niệm 
tương tác với database.


[MVC]: http://code.tutsplus.com/tutorials/mvc-for-noobs--net-10488
[PHPBridge]: http://phpbridge.org/
[Creating a Data Class]: http://phpbridge.org/intro-to-php/creating_a_data_class
