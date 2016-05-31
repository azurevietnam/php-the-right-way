---
isChild: true
anchor:  vagrant
---

## Vagrant {#vagrant_title}

[Vagrant] giúp bạn xây dựng một môi trường ảo và sẽ thiết đặt dựa trên các file thiết đặt. 
Những môi trường này có thể được cài đặt thủ công, hay bạn có thể dùng các phần mềm 
như [Puppet] hoặc [Chef]. Chuẩn bị sẵn các môi trường ảo chuẩn là cách tốt để đảm bảo nhiều môi trường ảo 
được cài đặt đồng nhất. Bạn cũng có thể xây dựng lại môi trường ảo mà không cần các bước thủ công.

Vagrant tạo các thư mục để chia sẻ code của bạn giữ host và  môi trường ảo, có nghĩa là bạn có thể tạo và chỉnh sửa 
các file trên host và chạy trên môi trường ảo.

### Trợ giúp

Nếu bạn cần vài trợ giúp để bắt đầu sử dụng Vagrant, có vài dịch vụ hữu ích:

- [Rove][Rove]: cho phép bạn tạo trước các gói Vagrant điể hình, 
PHP trong các tùy chọn. Provisioning tạo với Chef.
- [Puphpet][Puphpet]: Giao diện đồ họa (GUI) đơn giản để cài đặt môi truong2 ảo cho PHP. 
**tập trung vào PHP**. Bên cạnh VMs, nó có thể được dùng để triển khai lên các dịch vụ đám mây. 
Provisioning được tạo với Puppet.
- [Protobox][Protobox]: là tần trên cùng của vagrant và web GUI để cài đặt môi trường ảo cho phát triển web. 
Một tài liệu YAML điều khiển mọi thứ đươc cài đặt trêm môitrường ảo.
- [Phansible][Phansible]: cung cấp một giao diện dễ sử dụng giúp bạn tạo Ansible Playbooks cho các project PHP.


[Vagrant]: http://vagrantup.com/
[Puppet]: http://www.puppetlabs.com/
[Chef]: https://www.chef.io/
[Rove]: http://rove.io/
[Puphpet]: https://puphpet.com/
[Protobox]: http://getprotobox.com/
[Phansible]: http://phansible.com/
