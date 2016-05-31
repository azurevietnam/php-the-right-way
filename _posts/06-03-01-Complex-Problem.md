---
title: Vấn đề phức tạp
isChild: true
anchor:  complex_problem
---

## Vấn đề phức tạp (Complex Problem) {#complex_problem_title}

Nếu bạn đã nghe về Dependency Injection chắc bạn cũng biết qua các khái niệm 
*"Inversion of Control"* hoặc 
*"Dependency Inversion Principle"*. Đó là những vầm đề phức tạp mà Dependency Injection giải quyết.

### Inversion of Control

Inversion of Control là giành quyền kiểm soát hệ thống bằng cách giữ các organisational control 
hoàn toàn tách biệt với đối tượng. Trong khái niệm Dependency Injection, có nghĩa là nới lỏng các dependency  
bằng cách điều khiển và khởi tạo nó nơi náo khác trong hệ thống.

Qua nhiều năm, các PHP framework đã hoàn thiện Inversion of Control, tuy nhiên, vấn đề là phần nào và ở đâu.
Ví dụ, các MVC framework cung cấp một siêu đối tượng hay controller nền để các controller khác kế thừa 
và truy cập tới các dependency của nó. Đó là Inversion of Control, tuy nhiên thay vì nới lỏng các 
dependency, phương thức này đơn giản di chuyển chúng.

Dependency Injection cho phép chúng giải quyết vấn đề này chỉ bằng injecting các
dependencies ta cần, khi ta cần chúng, không cần phải hard coded dependencies.

### Dependency Inversion Principle

Dependency Inversion Principle là ký tự "D" trong nguyên tắc S.O.L.I.D của lập trình hướng đối tượng 
phát biểu một class nên *"phụ thuộc vào Abstractions. Không nên phụ thuộc vào concretions."*. Đơn giản có nghĩa  
các dependency nên là các interfaces/contracts hay abstract classes hơn là các concrete implementations 
Chúng ta có thể dễ dàng tái cấu trúc ví dụ trên theo nguyên tắc này.

{% highlight php %}
<?php
namespace Database;

class Database
{
    protected $adapter;

    public function __construct(AdapterInterface $adapter)
    {
        $this->adapter = $adapter;
    }
}

interface AdapterInterface {}

class MysqlAdapter implements AdapterInterface {}
{% endhighlight %}

Có vài lợi ích cho class `Database`bây giờ phụ thuộc vào interface hơn là concretion.

Suy nghĩ nếu bạn đang làm việc với team và adapter đang được làm việc bởi đồng nghiệp. Trong ví dụ đầu tiên, 
chúng ta phải đợi đồng nghiệp hoàn thành adapter trước khi có thể dùng nó cho Unit tests. Bây giờ, dependency đó 
là một interface/contract, chúng ta có thể dùng interface đó, biết rằng đồng nghiệp của chúng ta sẽ xây 
dựng adapter dựa trên đó.

Lợi ích lớn hơn của phương thức này là code của chúng ta sẽ dễ dàng mở rộng hơn rất nhiều. 
Nếu bạn muốn dùng một loại database khác, chúng ta có thể viết một adapter kế thừa interface gốc 
và dùng nó.