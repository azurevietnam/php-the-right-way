---
layout: page
title:  Design Patterns
sitemap: true
---

# Design Patterns

Có nhiều các để cấu trúc code và project cho ứng dụng web. Nhưng cách tốt là tuân theo các pattern thông 
dụng vì nó là cho code dễ quản lý và dễ hiểu hơn.

* [Architectural pattern on Wikipedia](https://en.wikipedia.org/wiki/Architectural_pattern)
* [Software design pattern on Wikipedia](https://en.wikipedia.org/wiki/Software_design_pattern)
* [Collection of implementation examples](https://github.com/domnikl/DesignPatternsPHP)

## Factory

Mộ trong các Design patterns phổ biến nhất là factory pattern. Trong pattern này, 
một class dùng để tạo một đối tượng mà bạn muốn dùng. ví dụ:

{% highlight php %}
<?php
class Automobile
{
    private $vehicleMake;
    private $vehicleModel;

    public function __construct($make, $model)
    {
        $this->vehicleMake = $make;
        $this->vehicleModel = $model;
    }

    public function getMakeAndModel()
    {
        return $this->vehicleMake . ' ' . $this->vehicleModel;
    }
}

class AutomobileFactory
{
    public static function create($make, $model)
    {
        return new Automobile($make, $model);
    }
}

// have the factory create the Automobile object
$veyron = AutomobileFactory::create('Bugatti', 'Veyron');

print_r($veyron->getMakeAndModel()); // outputs "Bugatti Veyron"
{% endhighlight %}

Đoạn code trên dùng factory pattern để tạo đối tượng Automobile. Lợi ích khi sử dụng cách này là: 
- Bạn có thể thay đổi, rename hay thay thế class Automobile sau này và bạn chỉ cần chỉn sửa code trong factory,
thay vì tất cả mọi nơi trong class sử dụng class Automobile.
- Nếu tạo đối tượng là một việc phức tạp, bạn có thể làm việc đó trong factory, thay vì lặp lại nó mỗi khi tạo một đối tượng mới.

Sử dụng factory không phải lúc nào cũng cần thiết và thông minh. Đoạn code ví dụ ở đây rất đơn giản, factory 
chỉ tạo thêm sự phức tạp không cần thiết. Tuy nhiên nếu bạn xây dựng một dự án lớn hay phức tạp, dùng factory có thể 
tránh khỏi nhiều rắc rối.

* [Factory pattern on Wikipedia](https://en.wikipedia.org/wiki/Factory_pattern)

## Singleton

Khi thiết kế một ứng dụng web, Thường bạn chỉ muốn cho phép truy cập tới một và chỉ một đối tượng của class cụ thể. 
Singleton pattern sẽ giúp bạn làm điều đó.

{% highlight php %}
<?php
class Singleton
{
    /**
     * @var Singleton The reference to *Singleton* instance of this class
     */
    private static $instance;
    
    /**
     * Returns the *Singleton* instance of this class.
     *
     * @return Singleton The *Singleton* instance.
     */
    public static function getInstance()
    {
        if (null === static::$instance) {
            static::$instance = new static();
        }
        
        return static::$instance;
    }

    /**
     * Protected constructor to prevent creating a new instance of the
     * *Singleton* via the `new` operator from outside of this class.
     */
    protected function __construct()
    {
    }

    /**
     * Private clone method to prevent cloning of the instance of the
     * *Singleton* instance.
     *
     * @return void
     */
    private function __clone()
    {
    }

    /**
     * Private unserialize method to prevent unserializing of the *Singleton*
     * instance.
     *
     * @return void
     */
    private function __wakeup()
    {
    }
}

class SingletonChild extends Singleton
{
}

$obj = Singleton::getInstance();
var_dump($obj === Singleton::getInstance());             // bool(true)

$anotherObj = SingletonChild::getInstance();
var_dump($anotherObj === Singleton::getInstance());      // bool(false)

var_dump($anotherObj === SingletonChild::getInstance()); // bool(true)
{% endhighlight %}

Đọan code trên thực thi singleton pattern sử dụng [biến *static*](http://php.net/language.variables.scope#language.variables.scope.static) và  
phương thức static `getInstance()`.
Note the following:

* Hàm constructor [`__construct()`](http://php.net/language.oop5.decon#object.construct) được khai báo protected 
để ngăn chặn tạo đối tượng mới bên ngoài class bằng toán tử `new`.
* Phương thức magic [`__clone()`](http://php.net/language.oop5.cloning#object.clone) được khai báo  
 private để ngăn chặn sao chép đối tượng của class bằng toán tử [`clone`](http://php.net/language.oop5.cloning). 
* Phương thức magic [`__wakeup()`](http://php.net/language.oop5.magic#object.wakeup) 
được khai báo private để ngăn không cho unserializing đối tượng của class từ hàm global [`unserialize()`](http://php.net/function.unserialize)
.
* Một đối tượng mới sẽ được tạo từ một [liên kết static trễ](http://php.net/language.oop5.late-static-bindings) 
trong phương thức static `getInstance()` với từ khóa `static`, cho phép sự phân lớp của class `Singleton` trong ví dụ.

Singleton pattern hữu ích khi chỉ một đối tượng được tạo từ một class trong toàn thời gian của một request 
trong một ứng dụng web. Đặc trưng là khi bạn có các đối tượng toàn cục (như class Config) hay các tài nguyên được chia sẻ. 

Bạn nên cẩn thận khi dùng Singleton bởi vì nó nó làm giảm khả năng test. Trong nhiều trường hợp dependency injection có thể (và nên) được dùng taại vị trí của class singleton. 
Sử dụng dependency injection có nghĩa bạn không giới thiệu coupling không cần thiết vào thiết kế của ứng dụng, bởi vì đối 
tượng sử dụng các tài nguyên toàn cục hay tài nguyên được chia sẻ không cần sự hiểu biết của class được khai báo cụ thể.
                                                                                                
* [Singleton pattern on Wikipedia](https://en.wikipedia.org/wiki/Singleton_pattern)

## Strategy

Đây là pattern cho phép các giải thuật khác nhau có thể được lựa chọn trong thời-gian-chạy (run-time). 
Hay nói cách khác, Strategy định nghĩa một họ các giải thuật khác nhau, mỗi giải thuật được triển khai bởi một lớp 
(class) cụ thể và chúng có thể hoán đổi cho nhau tùy vào ngữ cảnh. Strategy giúp các giải thuật khác nhau 
độc lập với client sử dụng nó. Ví dụ, một lớp thực hiện nhiệm vụ so sánh dữ liệu đầu vào có thể sử dụng mẫu 
thiết kế Strategy để tự động lựa chọn giải thuật cho việc này dựa trên loại dữ liệu, nguồn gốc của chúng, 
lựa chọn của người dùng hay các yếu tố khác. Những yếu tố này không được biết cho tới thời-gian-chạy (runtime) 
và khi đó tùy vào loại dữ liệu mà hệ thống lựa chọn cách thức so sánh khác nhau. Các giải pháp so sánh được đóng 
gói trong các đối tượng riêng biệt sẽ được sử dụng bởi những đối tượng thực hiện việc này tại các phân vùng khác nhau 
của hệ thống (hoặc thậm chí ở những hệ thống khác nhau) mà không gây ra sự trùng lặp về mã lệnh.
Có một vài dạng của strategy pattern, đơn giản nhất là ví dụ sau:

Đoạn code đẩu tiên thuộc về các giải thuật; bạn có thể muốn serialized mảng, dùng JSON hoặc chỉ cần một mảng dữ liệu:

{% highlight php %}
<?php

interface OutputInterface
{
    public function load();
}

class SerializedArrayOutput implements OutputInterface
{
    public function load()
    {
        return serialize($arrayOfData);
    }
}

class JsonStringOutput implements OutputInterface
{
    public function load()
    {
        return json_encode($arrayOfData);
    }
}

class ArrayOutput implements OutputInterface
{
    public function load()
    {
        return $arrayOfData;
    }
}
{% endhighlight %}

Bằng cách tóm lược các thuật toán ở trên, các lập trình viên khác có thể dễ dàng thêm một kiểu output mới mà không ảnh hướng tới client code.

Bạn có thể thấy mỗi 'output' class cụ thể thự thi OutputInterface - nhằm hai mục đích, mục dích chính là cung cấp một 
giao ước đư giản cái nào sẽ được tuân bởi bất kỳ sự thực thi cụ thể mới nào. 
Thứ hai,  bằng cách thực thi interface chung, bạn sẽ thấy trong phần tiếp theo rằng, bạn có thể dùng [Type Hinting](http://php.net/language.oop5.typehinting) 
để chắc rằng các client sử dụng những hành xử này dùng đúng kiểu trong trường hợp 'OutputInterface'.

The next snippet of code outlines how a calling client class might use one of 
these algorithms and even better set the
behaviour required at runtime:

{% highlight php %}
<?php
class SomeClient
{
    private $output;

    public function setOutput(OutputInterface $outputType)
    {
        $this->output = $outputType;
    }

    public function loadOutput()
    {
        return $this->output->load();
    }
}
{% endhighlight %}

The calling client class above has a private property which must be set at runtime and 
be of type 'OutputInterface'
once this property is set a call to loadOutput() will call the load() method in the 
concrete class of the output type
that has been set.

{% highlight php %}
<?php
$client = new SomeClient();

// Want an array?
$client->setOutput(new ArrayOutput());
$data = $client->loadOutput();

// Want some JSON?
$client->setOutput(new JsonStringOutput());
$data = $client->loadOutput();

{% endhighlight %}

* [Strategy pattern on Wikipedia](http://en.wikipedia.org/wiki/Strategy_pattern)

## Front Controller

Front controller pattern là nơi bạn có một lối vào cho ứng dụng web (ví dụ index.php) và 
quản lý tất cả request. Cho phép load tất cả các dependency, thực hiện các request và gửi phản hồi tới trình duyệt. 
Front controller pattern khuyến khích mô-đun hóa code.
* [Front Controller pattern on Wikipedia](https://en.wikipedia.org/wiki/Front_Controller_pattern)

## Model-View-Controller

Mô hình model-view-controller (MVC)và các mô hình liên quan như HMVC và MVVM cho phép bạn chia code 
thành các đối tượng logic thực hiện các mục đích khác nhau. Model hoạt động như là lớp truy cập dữ liệu 
, nơi dữ liệu được fetch và trả về trong định dạng có thể sử dụng trong ứng dụng. Controller quản lý các 
request, tiến trình dữ liệ được trả về từ Model và load View. View hiển thị template (markup, xml, ...).

MVC là pattern phổ biến nhất được dùng  trong các [PHP framework](https://github.com/codeguy/php-the-right-way/wiki/Frameworks).

Tìm hiểu thêm về MVC và các mô hình liên quan:

* [MVC](https://en.wikipedia.org/wiki/Model%E2%80%93View%E2%80%93Controller)
* [HMVC](https://en.wikipedia.org/wiki/Hierarchical_model%E2%80%93view%E2%80%93controller)
* [MVVM](https://en.wikipedia.org/wiki/Model_View_ViewModel)
