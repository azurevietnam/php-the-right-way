---
isChild: true
anchor:  plain_php_templates
---

## Plain PHP Templates {#plain_php_templates_title}

Plain PHP template là templates được dùng mặc định trong PHP code. 
Nó là lựa chọn tự nhiên vì PHP thật ra là một ngôn ngữ template. 
Có nghĩa là bạn có thể kết hợp PHP với các ngôn ngữ giao diện khác, như HTML. Vì vậy các 
lập trình viên PHP không cần phải học thêm cú pháp mới, họ biết nên dùng các hàm nào, 
và các IDE của họ cũng có các trình nhắc cú pháp. 
Hơn nữa, plain PHP templates nhanh hơn vì không phải biên dịch.

Mỗi PHP framework hiện đại cung cấp một loại hệ thống template, đa số dùng plain PHP như mặc định. 
Bên ngoài framework, các thư viện như [Plates][plates] hay [Aura.View][aura] khiến cho việc làm việc 
với plain PHP templatesdễ dàng hơn bằng cách cung cấp các chức năng template mới như kế thừa, layout, và extension.

### Ví dụ đơn giản của plain PHP template

Sử dụng thư viện [Plates][plates].

{% highlight php %}
<?php // user_profile.php ?>

<?php $this->insert('header', ['title' => 'User Profile']) ?>

<h1>User Profile</h1>
<p>Hello, <?=$this->escape($name)?></p>

<?php $this->insert('footer') ?>
{% endhighlight %}

### Ví dụ plain PHP templates về kế thừa

Sử dụng thư viện [Plates][plates].

{% highlight php %}
<?php // template.php ?>

<html>
<head>
    <title><?=$title?></title>
</head>
<body>

<main>
    <?=$this->section('content')?>
</main>

</body>
</html>
{% endhighlight %}

{% highlight php %}
<?php // user_profile.php ?>

<?php $this->layout('template', ['title' => 'User Profile']) ?>

<h1>User Profile</h1>
<p>Hello, <?=$this->escape($name)?></p>
{% endhighlight %}


[plates]: http://platesphp.com/
[aura]: https://github.com/auraphp/Aura.View
