---
isChild: true
anchor:  behavior_driven_development
---

## Behavior Driven Development {#behavior_driven_development_title}

BDD (Behavior Driven Development) là một quá trình phát triển phần mềm dựa trên phương pháp Agile
(phát triển phần mềm linh hoạt).
BDD là sự mở rộng của TDD (Test driven development). Thay vì tập trung vào phát triển phần mềm theo hướng 
kiểm thử, BDD tập trung vào phát triển phần mềm theo hướng hành vi.
Dựa vào requirement các kịch bản test (Scenarios) sẽ được viết trước dưới dạng ngôn ngữ tự nhiên và 
dễ hiểu nhất sau đó mới thực hiện cài đặt source code đễ pass qua tất cả các stories đó.
Những kịch bản test này được viết dưới dạng các feature file và đòi hỏi sự cộng tác từ tất cả các 
thành viên tham gia dự án hay stakeholder.

Có hai loại BDD là: SpecBDD and StoryBDD. 
SpecBDD tập trung vào các hành vi kỹ thuật của code, StoryBDD tập trung vào các chức năng hay tương tác. PHP có các framework cho cả hai loại này.

Với StoryBDD, bạn viết các story dễ hiểu mô tả các hành động của ứng dụng. 
Các story này có thể dược dùng để test. Framework PHP cho StoryBDD là [Behat], được truyền cảm hứng từ 
project Ruby [Cucumber]  và thực thi Gherkin DSL để mô tả các tính năng.

Với SpecBDD, các đặc diểm kỹ thuật mô tả cách hành đông thực tế của code. 
Thay vì kiểm tra hàm hay phương thức, bạn có thể mô tả thực tế các hàm hay phương thức đó hoạt động như thế nào. 
PHP cung cấp framework [PHPSpec] cho SpecBDD. Framework này được truyền cảm hứng từ [RSpec project][Rspec] cho Ruby.



### Tham khảo BDD

* [Behat], the StoryBDD framework for PHP, inspired by Ruby's [Cucumber] project;
* [PHPSpec], the SpecBDD framework for PHP, inspired by Ruby's [RSpec] project;
* [Codeception] is a full-stack testing framework that uses BDD principles.


[Behat]: http://behat.org/
[Cucumber]: http://cukes.info/
[PHPSpec]: http://www.phpspec.net/
[RSpec]: http://rspec.info/
[Codeception]: http://codeception.com/
