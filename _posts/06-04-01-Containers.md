---
isChild: true
anchor:  containers
---

## Containers {#containers_title}

Điều đầu tiên bạn cần hiểu về Dependency Injection Containers là nó không giống với Dependency Injection. 
Container là một tiện ích giúp chúng ta thi hành Dependency Injection, tuy nhiên, chúng có thể thường xuyên được 
dùng để thực thi một anti-pattern, Service Location. 
Injecting DI container như là Service
Locator trong các class của bạn người ta có thể cho rằng tạo một harder dependency trên container 
hơn dependency bạn đang thay thế.
Nó làm cho code của bạn ít rõ ràng và khó để test hơn.

Hầu hết các frameworks hiện đại đều có Dependency Injection Container của mình cho phép bạn 
bao bọc các dependencies với nhau qua cấu hình. Điều đó có nghĩa bạn có thể viết code ứng dụng 
rõ ràng và tách biệt như các framework.
