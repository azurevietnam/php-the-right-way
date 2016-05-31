# Đóng góp cho PHP The Right Way

Nếu bạn muốn đóng góp cho [PHP The Right Way](https://github.com/nhaancs/php-the-right-way/), 
bạn có thể đóng góp bằng nhữ hình thức sau:

Hãy cho chúng tôi biết cảm nhận của bạn về tài liệu này. Nó sẽ hữu ích với người mới.

Tuân theo những huống dẫn trong tài liệu, thể hiện sự tôn trọng của bạn đối với công
sức và thời gian của các tác giả, và bạn cũng sẽ nhận dược những chỉ dẫn tốt nhất.


## Thảo luận

Thảo luận tại [issue tracker của Github](https://github.com/codeguy/php-the-right-way/issues) 
(bản tiếng Anh)hay [issue tracker bản tiếng Việt](https://github.com/nhaancs/php-the-right-way/issues). 
Khi thảo luận vui lòng tuân theo một số nguyên tắt sau:

* Vui lòng **không** hỏi các vấn đề quá cá nhân (bạn có thể sử dụng
  [Stack Overflow](http://stackoverflow.com/questions/tagged/php) hay IRC).

* Vui lòng **không** bàn luận các chủ đề không liên quan, tôn trogn5 ý kiến của người khác.


<a name="pull-requests"></a>

## Pull Requests

Pull requests là cách tốt nhất để thêm nội dung mới vào PHP The Right Way hay sửa các lỗi.
Các thay đổi mang tính xây dựng sẽ dc chấp nhận.

Qui trình:

1. [Fork](http://help.github.com/fork-a-repo/) dự án, clone fork của bạn,
   và chỉnh sử các remote:

   ```bash
   # Clone your fork of the repo into the current directory
   git clone https://github.com/<your-username>/php-the-right-way.git
   # Navigate to the newly cloned directory
   cd php-the-right-way
   # Assign the original repo to a remote called "upstream"
   git remote add upstream https://github.com/codeguy/php-the-right-way.git
   ```

2. Nấu bạn đã clone rồi, cập nhật các thay đổi mới nhất tại remote upstream:

   ```bash
   git checkout gh-pages
   git pull upstream gh-pages
   ```

3. Tạo một branch mới để chứa các thay đổi và sử chửa của bạn:

   ```bash
   git checkout -b <topic-branch-name>
   ```

4. Cài đặt [Jekyll](https://github.com/jekyll/jekyll/) gem và dependencies 
để xem các thay đổi trên máy cục bộ:

    ```bash
    # Install the needed gems through Bundler
    bundle install
    # Run the local server
    bundle execute jekyll s
    ```

5. Commit thay đổi của bạn. Dựa theo [hướng dẫn viết git commit message](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html)
   or your content is unlikely be merged into the main project. Sử dụng tính năng
   [interactive rebase](https://help.github.com/articles/interactive-rebase) để làm sạch các commit của bạn trước khi công khai.

6. Merge (or rebase) upstream development branch vào branch của bạn trên máy cục bộ:

   ```bash
   git pull [--rebase] upstream gh-pages
   ```

7. Push branch của bạn lên fork của bạn:

   ```bash
   git push origin <topic-branch-name>
   ```

8. [Mở một Pull Request](https://help.github.com/articles/using-pull-requests/)
    với tiêu đề và ghi chú rõ ràng.


## Điều khoản

Khi submit một pull request, bạn đồng ý cấp phép công việc của mình theo điều khoản của
[Creative Commons Attribution-NonCommercial-ShareAlike
3.0 Unported License](http://creativecommons.org/licenses/by-nc-sa/3.0/).

Giống với nội dung về cấp phép của các nội dung trên PHP The Right Way,
bao gồm - nhưng không giới hạn đối với:

* [phptherightway.com](http://phptherightway.com)
* Các bản dịch của phptherightway.com
* [LeanPub: PHP The Right Way](https://leanpub.com/phptherightway/)
* Các bản dịch của "LeanPub: PHP The Right Way"

Tất cả nội dung sẽ luôn miễn phí.

## Qui chuẩn đóng góp

1. Dùng tiếng Anh Mỹ (*Chỉ dùng cho bản tiếng Anh*)
2. Dùng 4 khoảng trắng thay cho tab
3. Các văn bản tối đa 120 ký tự
4. Code ví dụ tuân theo chuẩn PSR-1 hay cao hơn.
5. Dùng [GitHub Flavored Markdown](http://github.github.com/github-flavored-markdown/)cho tất cà các nội dung.
6. Tuân theo [php.net](http://php.net/urlhowto.php) khi trỏ tới một liên kết ngoài.
