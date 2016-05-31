---
isChild: true
title:   Lớp Abstraction
anchor:  databases_abstraction_layers
---

## Lớp Abstraction {#databases_abstraction_layers_title}

Nhiều framework cung cấp lớp abstraction của nó có thể hoạc không tốt hơn [PDO][1]. 
Các lớp abstraction này thêm các tính năng còn thiếu của các lớp khác, cho bạn một 
database abstractionthay vì chỉ connection abstraction mà PDO cung cấp. Nó sẽ thêm một số tính năng nâng cao, 
nhưng nó sẽ tốt nếu bạn bạn muốn xây dựng một ứng dụng linh hoạt cần kết nối tới MySQL, PostgreSQL và SQLite

Vài lớp abstraction được xây dựng theo [PSR-0][psr0] 
hoặc [PSR-4][psr4] có thể cài dặt lên bất kỳ ứng dụng nào:

* [Aura SQL][6]
* [Doctrine2 DBAL][2]
* [Propel][7]
* [ZF2 Db][4]


[1]: http://php.net/book.pdo
[2]: http://www.doctrine-project.org/projects/dbal.html
[4]: http://packages.zendframework.com/docs/latest/manual/en/index.html#zend-db
[6]: https://github.com/auraphp/Aura.Sql
[7]: http://propelorm.org/
[psr0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[psr4]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md
