---
isChild: true
anchor:  compiled_templates
---

## Biên dịch Template {#compiled_templates_title}

Trong khi PHP ngày càng phát triển, trở thành ngôn ngữ hướng đối tượng, nó vẫn
[không cải thiện nhiều][article_templating_engines] như là một ngôn ngữ template
Các template dược biên dịch như [Twig], [Brainy], 
hay [Smarty]*, lắp đầy khoảng trống đó bằng các cung cấp các cú pháp mới dành riêng cho template. 
Từ tự động escape, tới kế thừa và rút gọn cấu trúc điều khiển,
các template được biên dịch được thiết kế để dễ viết, sạch hơn, dễ đọc hơn an toàn khi dùng. 
Các template được biên dịch có thể được chia sẻ qua nhiều ngôn ngữ, ví dụ [Mustache]. 
Khi các template được biên dịch, hiệu năng sẽ bị giảm đôi chút, nhưng nếu sử dũng caching hợp lý 
đó không còn là vấn đề lớn.

**Smarty có tính năng tự động escape, nhưng không được bật mặc định.*

### Ví dụ đơn giản của template được biên dịch

Sử dụng thư viện [Twig].

{% highlight html+jinja %}
{% raw %}
{% include 'header.html' with {'title': 'User Profile'} %}

<h1>User Profile</h1>
<p>Hello, {{ name }}</p>

{% include 'footer.html' %}
{% endraw %}
{% endhighlight %}

### Ví dụ của template được biên dịch về kế thừa

Sử dụng thư viện [Twig].

{% highlight html+jinja %}
{% raw %}
// template.html

<html>
<head>
    <title>{% block title %}{% endblock %}</title>
</head>
<body>

<main>
    {% block content %}{% endblock %}
</main>

</body>
</html>
{% endraw %}
{% endhighlight %}

{% highlight html+jinja %}
{% raw %}
// user_profile.html

{% extends "template.html" %}

{% block title %}User Profile{% endblock %}
{% block content %}
    <h1>User Profile</h1>
    <p>Hello, {{ name }}</p>
{% endblock %}
{% endraw %}
{% endhighlight %}


[article_templating_engines]: http://fabien.potencier.org/article/34/templating-engines-in-php
[Twig]: http://twig.sensiolabs.org/
[Brainy]: https://github.com/box/brainy
[Smarty]: http://www.smarty.net/
[Mustache]: http://mustache.github.io/
