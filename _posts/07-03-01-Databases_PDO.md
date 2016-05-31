---
isChild: true
title:   PDO Extension
anchor:  pdo_extension
---

## PDO Extension {#pdo_extension_title}

[PDO] là một thư viện database connection abstraction; có sẵn trong PHP 5.1.0 
&mdash; cung cấp các interface thông dụng để làm việc với nhiều loại database khác nhau. 
Ví dụ, bạn có thể dùng một hàm duy nhất để tương tác với MySQL hay SQLite:

{% highlight php %}
<?php
// PDO + MySQL
$pdo = new PDO('mysql:host=example.com;dbname=database', 'user', 'password');
$statement = $pdo->query("SELECT some_field FROM some_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);

// PDO + SQLite
$pdo = new PDO('sqlite:/path/db/foo.sqlite');
$statement = $pdo->query("SELECT some_field FROM some_table");
$row = $statement->fetch(PDO::FETCH_ASSOC);
echo htmlentities($row['some_field']);
{% endhighlight %}

PDO sẽ không dịch SQL query; Nó chỉ đơn giản kết nối với nhiều loại database 
với cùng một API.

Quan trọng hơn, `PDO` cho phép bạn nhập các input bên ngoài một cách an toàn 
vào SQL queries mà không phải lo lắng bị tấn công SQL injection.

Giả sử PHP nhận một biến số ID như là tham số của query. ID nên được dùng để tìm thông tin của user 
từ database. Cách làm sau đây là cách không đúng:

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$pdo->query("SELECT name FROM users WHERE id = " . $_GET['id']); // <-- NO!
{% endhighlight %}

Bạn đang đưa một tham số chưa qua xử lý vào SQL query. 
Nó sẽ khiến bạn bị tấn công [SQL Injection]. Nếu hacker truyền vào một ID không hợp lệ bằng cách gọi một URL như sau:
`http://domain.com/?id=1%3BDELETE+FROM+users`. Lúc đó giá trị của biến `$_GET['id']` sẽ là `1;DELETE FROM users` 
là câu lệnh sẽ xóa hết tất cả user! Vì vậy, xử lý qua ID bằng chức năng bind parameter của PDO.

{% highlight php %}
<?php
$pdo = new PDO('sqlite:/path/db/users.db');
$stmt = $pdo->prepare('SELECT name FROM users WHERE id = :id');
$id = filter_input(INPUT_GET, 'id', FILTER_SANITIZE_NUMBER_INT); // <-- filter your 
data first (see [Data Filtering](#data_filtering)), especially important for INSERT, UPDATE, etc.
$stmt->bindParam(':id', $id, PDO::PARAM_INT); // <-- Automatically sanitized for SQL by PDO
$stmt->execute();
{% endhighlight %}

Đây là đoạn code đúng. Nó dùng bind parameter trong câu lệnh PDO. Nó sẽ escape ID trước khi nhập vào database.

Để INSERT hay UPDATE database, cần đặt biệt chú ý 
[lọc dữ liệu của bạn](#data_filtering) trước khi làm việc với database  
(gỡ các thẻ HTML, JavaScript, ...).  PDO chỉ xử lý data cho SQL, không phải cho ứng dụng của bạn.

* [Tìm hiểu về PDO]

Sử dụng PDO bạn có thể đóng các kết nối bằng cách hủy bỏ các đối tượng. Hoặc PHP sẽ tự động đóng kết nối nếu 
khi đoạn mã kết thúc.


* [Tìm hiểu về PDO connections]

[pdo]: http://php.net/pdo
[SQL Injection]: http://wiki.hashphp.org/Validation
[Learn about PDO]: http://php.net/book.pdo
[Learn about PDO connections]: http://php.net/pdo.connections
