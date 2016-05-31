---
isChild: true
anchor:  test_driven_development
---

## Test Driven Development {#test_driven_development_title}

[Wikipedia](http://en.wikipedia.org/wiki/Test-driven_development):

TDD (Test Driven Development) là một phương thức làm việc, hay một quy trình viết mã hiện đại. 
Lập trình viên sẽ thực hiện thông qua các bước nhỏ (BabyStep) và tiến độ được đảm bảo liên tục 
bằng cách viết và chạy các bài test tự động (automated tests). Quá trình lập trình trong TDD 
cực kỳ chú trọng vào các bước liên tục sau:
> Viết 1 test cho hàm mới. Đảm bảo rằng test sẽ fail.
> Chuyển qua viết code sơ khai nhất cho hàm đó để test có thể pass.
> Tối ưu hóa đoạn code của hàm vừa viết sao cho đảm bảo test vẫn pass và tối ưu nhất cho việc lập trình 
kế tiếp.
> Lặp lại cho các hàm khác từ bước 1.

Một số loại testing:

### Unit Testing


Unit test là một cách tiếp cận trong lập trình để đảm bào các hàm, class, phương thức hoạt động như mong đợi 
trong suốt quá trình phát triển. Bằng cách kiểm tra giá trị đầu vào và giá trị đầu ra của các hàm, phương thức, 
bạn có thể đảm bảo các logic bên trong vẫn hoạt động tốt. Bằng cách sử dụng Dependency Injection và xây dựng 
các class "mock" và stub bạn có thể xác minh rằng các dependency được dùng đúng cách.

Khi bạn, tạo một class hay một hàm, bạn cũng nên tạo unit test cho mỗi chức năng của nó. Ở cấp độ cơ bản nhất 
bạn cần đảm bảo nó phát sinh lỗi nếu bạn truyền vào tham số không mong đợi và không phát sinh lỗi nếu bạn truyền 
vào một tham số chuẩn. Việc này sẽ chắc rằng trong tương lai nếu bạn thay đổi class hay hàm thì chức năng cũ vẫn 
hoạt động như mong đợi.

Một công dụng khác của Unit Test là hỗ trợ việc đóng góp cho mã nguồn mở. Nếu bạn có thể viết một test cho 
thấy một chức năng bị vỡ, sau đó sửa nó thì dễ được chấp nhận hơn. Nếu project của bạn cho phép pull request 
thì bạn nên đề nghị việc viết test như là một yêu cầu.

[PHPUnit](http://phpunit.de) là một testing framework để viết unit tests cho ứng dụng PHP, có một số lựa chọn khác như: 

* [atoum](https://github.com/atoum/atoum)
* [Kahlan](https://github.com/crysalead/kahlan)
* [Peridot](http://peridot-php.github.io/)
* [SimpleTest](http://simpletest.org)

### Test tích hợp (Integration Testing)

[Wikipedia](http://en.wikipedia.org/wiki/Integration_testing):

> Integration testing (hay Integration and Testing, viết tắt là "I&T") là một giai đoạn của testing
> mà mỗi module của ứng dụng được kết hợp và test như một nhóm. Nó diễn ra sau Unit test và trước 
> validation testing. Integration testing lấy giá trị đầu vào của module đã được Unit test, nhóm chúng trong các 
> test lớn hơn, được khai báo trong một integration test plan to those aggregates, và trả về out put
> sẵn sàng cho testing.

Hay đơn giản: 
 Là kiểu test kiểm tra liệu tất cả các module đã được kết hợp hoặc chưa kết hợp lại cùng với nhau 
 thực hiện công việc có đạt được kết quả như yêu cầu đã được xác định (do mỗi lập trình 
 viên thực hiện trên các module khác nhau. Khi họ hoàn thành đoạn code của họ, nhóm quản lý cấu 
 hình ráp chúng lại với nhau và chuẩn bị biên dịch. Các tester cần chắc rằng các module này bây giờ 
 đã được kết hợp và làm việc theo như yêu cầu - tức là phải test theo như yêu cầu).

Nhiều công cụ dùng cho unit test có thể được dùng cho integration testing.

### (Test chức năng) Functional Testing

Đôi khi được gọi là (acceptance testing), bao gồm sử dụng công cụ để tạo các test tự động thực chất là sử dụng ứng dung thay vì 
chỉ xác minh từng unit có hoạt động tốt không và mội unit có thể giao tiếp với nhau một các chính xác. 
Các công cụ này sử dụng các dữ liệu thực và mô phỏng người dùng thật của ứng dụng.

#### Công cụ test chức năng

* [Selenium](http://seleniumhq.com)
* [Mink](http://mink.behat.org)
* [Codeception](http://codeception.com) is a full-stack testing framework.
* [Storyplayer](http://datasift.github.io/storyplayer) is a full-stack testing framework that 
includes support for creating and destroying test environments on demand.
