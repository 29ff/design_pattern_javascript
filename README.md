# Design Pattern with Javascript
Một trong những khía cạnh quan trọng nhất của việc viết code dễ dàng maintain là việc phát hiện ra những doạn code lặp lại và có thể tối ưu hóa chúng, đây là trường hợp mà design pattern chứng minh chúng vô giá - Addy Osmani
Kể cả việc chúng ta có thể giải quyết được vấn đề khi viết **Javascript**, nhưng nó cũng có thể dẫn tới một số lỗi nếu chúng ta sử dụng sai design pattern hoặc áp dụng không đúng cách
Lập trình viên có xu hướng sử dụng những framework mới nhất và những thư viện được xây dựng cho web app và kết hợp những thư viện đó vào trong một project, mà thường quên đi các ý tưởng cốt lõi đằng sau việc tạo ra các thư viện này
Design pattern giống như các bản thiết kế về những cách giải quyết vấn đề không phần mềm. Chúng được cấu trúc với các phương pháp hay nhất nhằm giúp tạo ra sự ổn định và trong nhiều trường hợp, chúng còn giúp bảo mật cho những ứng dụng của chúng ta
Nhìn chung **Javascript** không phải là một ngôn ngữ lập trình truyền thống, vì thế nên việc phát hiện ra các Design pattern trong **Javascript** có vẻ khó hơn nhưng không phải là không thể

Trong bài viết này chúng ta sẽ tìm hiểu và các mẫu **Design pattern** khác nhau cũng như cách chúng ta có thể sử dụng chúng. Và chúng ta sẽ chỉ nói về 5 mẫu được sử dụng nhiều nhất trong bài viết này

## Types of Design Patterns
Trong kĩ thuật phần mềm, có rất nhiều các mẫu **Design pattern** tồn tại. Các mẫu này được nhóm theo 3 kiểu dưới đây:

  1. **Creational patterns**: Kiểu pattern này tập trung vào việc tạo ra các đối tượng. Khi tạo đối tượng trong những ứng dụng lớn, có quá nhiều thứ làm cho ứng dụng trở lên phức tạp. **Creational patterns** sẽ giải quyết vấn đề đó bằng cách kiểm soát việc tạo ra các đối tượng
  2. **Structural patterns**: **Strutural patterns** cup cấp các cách để quản lý các mối quan hệ giữ các đối tượng và cũng tạo ra các cấu trúc lớp. Có một cách để đạt được là sử dụng kế thừa và sắp xếp để tạo ra đối tượng lớn từ các đối tượng nhỏ
  3. **Behavioral patterns**: **Behavioral patterns** là sự tập trung vào sự tương tác giữa các đối tượng. Trong trường hợp **Behavioral patterns** mô tả một khoảng thời gian và **Structural patterns** mô tả một hoặc nhiều những cấu trúc tĩnh, **Behavioral patterns** mô tả một quá trình

## Creational Patterns
### Module

Được sử dụng rất thường xuyên trong quá trình phát triển phần mềm, module pattern có thể được xem như là một **IIFE** (Function thực thi ngay)
```javascript
(function() {
  // code goes here!
})();
```
