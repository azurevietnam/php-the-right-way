---
title: Khái niệm cơ bản
isChild: true
anchor:  basic_concept
---

## Khái niệm cơ bản {#basic_concept_title}

Chúng ta có thể giải thích khái niệm một cách đơn giản như sau:

Ta có một class `Database` cần một adapter để giao tiếp với database. 
Ta khởi tạo (instantiate) adapter trong constructor và tạo một hard dependency, 
làm cho việc testing khó khăn và có nghĩa là class `Database` "dính chặt" với adapter.


{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct()
    {
        $this->adapter = new MySqlAdapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}

Đoạn code này có thể được cấu trúc lại để dùng Dependency Injection và vì thế nới lỏng dependency.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(MySqlAdapter $adapter)
    {
        $this->adapter = $adapter;
    }
}

class MysqlAdapter {}
{% endhighlight %}


Bây giờ chúng ta tạo dependency của class `Database` hơn là tạo nên chính nó. Chúng ta cũng nên tạo một 
phương thức chấp nhận tham số của dependency và cài dặt nó, hoặc nếu thuộc tính `$adapter`  là public 
chúng ta có thể cài đặt nó trực tiếp.
