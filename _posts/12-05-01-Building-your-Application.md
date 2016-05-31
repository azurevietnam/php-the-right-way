---
title: Xây dựng và triển khai ứng dụng
isChild: true
anchor:  building_and_deploying_your_application
---

## Xây dựng và triển khai ứng dụng {#building_and_deploying_your_application_title}

If you find yourself doing manual database schema changes or running your tests 
manually before updating your files
(manually), think twice! With every additional manual task needed to deploy a new 
version of your app, the chances for
potentially fatal mistakes increase. Whether you're dealing with a simple update, 
a comprehensive build process or even
a continuous integration strategy, [build automation][buildautomation] is your friend.

Nếu bạn đang làm theo cách thủ công các công việc sau: thay đổi sơ đồ database, testing trước khi cập nhật file, 
hãy nghĩ lại! Khi có nhiều việc duco759 làm thủ công thì nguy cơ xuất hiện lỗi sẽ gia tăng. Cho dù việc đó 
đơn giản hay phức tạp, [tự dộng hóa][buildautomation] là cần thiết.

Một số công việc bạn sẽ muốn tự động hóa:

* Quản lý dependency
* Biên dịch, nén các tài nguyên (css, js, ...)
* Testing
* Tạo documentation
* Đóng gói
* Triển khai (Deployment)


### Xây dựng các công cụ tự động

Xây dựng các công cụ tự động có thể diễn tả là tập hợp các đoạn mã quản lý ac1c tác vụ phổ biến trong quá trình 
triển khai ứng dụng. Cây dựng công cụ không phải là một phần của ứng dụng, nó tương tác với ứng dụng từ bên ngoài.
Có nhiều công cụ mã nguồn mở hỗ trợ bạn xây dựng các tác vụ tự động. Một số viết bằng PHP, số khác thì không:

[Phing] là cách dễ nhất để bắt đầ với triển khai tự động trong thế giới PHP. 
Với Phing bạn có thể điều khiển các package, khiển khai hay quá trình testing từ một file XML đơn giản. 
Phing (dựa trên [Apache Ant])
cung cấp nhiều bộ tác vụ thường cần cho cài đặt hay nâng cấp ứng dụng Web và có thể mở rộng với các tác vụ khác, được viết bằng PHP. 

[Capistrano] là hệ thống cho *các lập trình viên từ trung cấp-tới-cao-cấp* để thực thi các câu lệnh 
một cách có cấu trúc và có thể lặp lại trên một hay nhiều remote machine. Nó được thiết đặt cho triển khai ứng dụng 
viết bằng Ruby on Rails, tuy nhiên chúng ta có thể triển khai hệ thống PHP với nó. Lập trình viên cần biết 
Ruby and Rake.

Blog post của Dave Gardner [triển khai PHP với Capistrano][phpdeploy_capistrano].

[Chef] còn hơn cả deployment framework, nó là một hệ thống Ruby based rất mạnh mẽ, không chỉ triển khai ứng dụng 
của bạn mà còn có thể xây dựng toàn bộ môi trường server hay virtual box.

[Deployer] là một công cụ triển khahi viết bằng PHP. 
Chạy các tác vụ song song, atomic deployment, duy trì sự nhất quán của các server. 
Là phương pháp tự động các tác vụ thông dụng cho Symfony, Laravel, Zend Framework và Yii.

#### Chef resources cho lập trình viên PHP:

* [Ba phần của blog series về triển khai ứng dụng LAMP với  Chef, Vagrant, and EC2][chef_vagrant_and_ec2]
* [Chef Cookbook which installs and configures PHP and the PEAR package management system][Chef_cookbook]
* [Chef video tutorial series][Chef_tutorial]

#### Tham khảo:

* [Tự động hóa project của bạn với Apache Ant][apache_ant_tutorial]

### Continuous Integration

> Continuous Integration là một software development practice khi các thành viên của team kết hợp công việc của 
một các thường xuyên.
> thông thường mỗi người thực hiện kết hợp ít nhất một lần mỗi ngày — dẫn tới nhiều lần kết hợp mỗi ngày. 
Và nhiều team nhận thấy 
> các tiếp cận này dẫn đến giảm đi đáng kể các vấn đề khi kết hợp và cho phép team phát triển ứng dụng nhanh chóng.

*-- Martin Fowler*

Có nhiều các thực hiện continuous integration cho PHP. [Travis CI] là một dịch vụ được host cộng đồng mã nguồn mở. 
Nó được hết hợp với GitHub và cung cấp first class support cho nhiều ngôn ngữ bao gồm PHP.

#### Tham khảo:

* [Continuous Integration with Jenkins][Jenkins]
* [Continuous Integration with PHPCI][PHPCI]
* [Continuous Integration with Teamcity][Teamcity]


[buildautomation]: http://en.wikipedia.org/wiki/Build_automation
[Phing]: http://www.phing.info/
[Apache Ant]: http://ant.apache.org/
[Capistrano]: https://github.com/capistrano/capistrano/wiki
[phpdeploy_capistrano]: http://www.davegardner.me.uk/blog/2012/02/13/php-deployment-with-capistrano/
[Chef]: https://www.chef.io/
[chef_vagrant_and_ec2]: http://www.jasongrimes.org/2012/06/managing-lamp-environments-with-chef-vagrant-and-ec2-1-of-3/
[Chef_cookbook]: https://github.com/chef-cookbooks/php
[Chef_tutorial]: https://www.youtube.com/playlist?list=PL11cZfNdwNyPnZA9D1MbVqldGuOWqbumZ
[apache_ant_tutorial]: http://net.tutsplus.com/tutorials/other/automate-your-projects-with-apache-ant/
[Travis CI]: https://travis-ci.org/
[Jenkins]: http://jenkins-ci.org/
[PHPCI]: http://www.phptesting.org/
[Teamcity]: http://www.jetbrains.com/teamcity/
[Deployer]: https://github.com/deployphp/deployer
