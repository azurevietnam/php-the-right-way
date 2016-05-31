---
title: Ngày tháng và thời gian
isChild: true
anchor:  date_and_time
---

## Ngày tháng và thời gian (Date and Time) {#date_and_time_title}

PHP cung cấp class DateTime với nhiều hàm hữu ích giúp bạn làm việc với ngày tháng và thời gian. 

Để bắt đầu làm việc với DateTime, chuyển đổi chuỗi ngày tháng và thời gian thành đối tượng với hàm factory `createFromFormat()` 
hoặc `new DateTime` để nhận thời gian và ngày tháng hiện tại. Hàm `format()` chuyển đổi DateTime trở về 
chuỗi cho output.

{% highlight php %}
<?php
$raw = '22. 11. 1968';
$start = DateTime::createFromFormat('d. m. Y', $raw);

echo 'Start date: ' . $start->format('Y-m-d') . "\n";
{% endhighlight %}

Thực hiện tính toán với DateTime với class DateInterval. DateTime có các phương thức như `add()` và `sub()` 
nhận DateInterval như một tham số. Đừng viết code để mong đợi có được cùng số giây cho mỗi ngày 
Giờ mùa hè (daylight saving)(1) và sự thay đổi timezone alterations sẽ phá vỡ sự tính toán. Thay vào đó sử dụng interval thay thế. 
Tính toán sự khác biệt ngày tháng bằng hàm `diff()`, trả về DateInterval.

{% highlight php %}
<?php
// create a copy of $start and add one month and 6 days
$end = clone $start;
$end->add(new DateInterval('P1M6D'));

$diff = $end->diff($start);
echo 'Difference: ' . $diff->format('%m month, %d days (total: %a days)') . "\n";
// Difference: 1 month, 6 days (total: 37 days)
{% endhighlight %}

Đối tượng DateTime bạn có thể sử dụng so sánh chuẩn:

{% highlight php %}
<?php
if ($start < $end) {
    echo "Start is before end!\n";
}
{% endhighlight %}

Một ví dụ cuối cùng để giải thích class DatePeriod. Nó được dùng để lặp lại các sự kiện tuần hoàn. 
Nó có thể nhận hai đối tượng DateTime, bắt đầu và kết thúc, và khoảng thời gian sẽ trả về tất cả các sự kiện trong khoảng đó.


{% highlight php %}
<?php
// output all thursdays between $start and $end
$periodInterval = DateInterval::createFromDateString('first thursday');
$periodIterator = new DatePeriod($start, $periodInterval, $end, DatePeriod::EXCLUDE_START_DATE);
foreach ($periodIterator as $date) {
    // output each date in the period
    echo $date->format('Y-m-d') . ' ';
}
{% endhighlight %}

* [Đọc thêm về DateTime][datetime]
* [Đọc thêm về date formatting][dateformat] (accepted date format string options)

(1)Giờ mùa Hè – hay còn được biết với tên DST (Daylight Saving Time) là một kiểu quy ước chỉnh thời gian 
theo khoảng thời gian thực tế mà trời sáng trong ngày. Với những nước áp dụng quy ước này, 
vào thời gian từ khoảng giữa mùa Xuân (cuối tháng 3) tới đầu mùa Đông (cuối tháng 10, đầu tháng 11), 
đồng hồ sẽ được chỉnh nhanh hơn 1 tiếng. Khoảng thời gian còn lại, đồng hồ sẽ được chỉnh về như cũ.

[datetime]: http://php.net/book.datetime
[dateformat]: http://php.net/function.date
