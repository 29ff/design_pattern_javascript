# Design Pattern Javascript
<h1>Design Pattern with Javascript</h1>
<p>Một trong những khía cạnh quan trọng nhất của việc viết code dễ dàng maintain là việc phát hiện ra những doạn code lặp lại và có thể tối ưu hóa chúng, đây là trường hợp mà design pattern chứng minh chúng vô giá - Addy Osmani</p>
<p>Kể cả việc chúng ta có thể giải quyết được vấn đề khi viết Javascript, nhưng nó cũng có thể dẫn tới một số lỗi nếu chúng ta sử dụng sai design pattern hoặc áp dụng không đúng cách</p>
<p>Lập trình viên có xu hướng sử dụng những framework mới nhất và những thư viện được xây dựng cho web app và kết hợp những thư viện đó vào trong một project, mà thường quên đi các ý tưởng cốt lõi đằng sau việc tạo ra các thư viện này</p>
<p>Design pattern giống như các bản thiết kế về những cách giải quyết vấn đề không phần mềm. Chúng được cấu trúc với các phương pháp hay nhất nhằm giúp tạo ra sự ổn định và trong nhiều trường hợp, chúng còn giúp bảo mật cho những ứng dụng của chúng ta</p>
<p>Nhìn chung Javascript không phải là một ngôn ngữ lập trình truyền thống, vì thế nên việc phát hiện ra các Design pattern trong Javascript có vẻ khó hơn nhưng không phải là không thể</p>

<p>Trong bài viết này chúng ta sẽ tìm hiểu và các mẫu Design pattern khác nhau cũng như cách chúng ta có thể sử dụng chúng. Và chúng ta sẽ chỉ nói về 5 mẫu được sử dụng nhiều nhất trong bài viết này</p>

<h2>Types of Design Patterns</h2>
<p>Trong kĩ thuật phần mềm, có rất nhiều các mẫu Design pattern tồn tại. Các mẫu này được nhóm theo 3 kiểu dưới đây:</p>
<ul>
  <li>1. <strong>Creational patterns</strong>: Kiểu pattern này tập trung vào việc tạo ra các đối tượng. Khi tạo đối tượng trong những ứng dụng lớn, có quá nhiều thứ làm cho ứng dụng trở lên phức tạp. <strong>Creational patterns</strong> sẽ giải quyết vấn đề đó bằng cách kiểm soát việc tạo ra các đối tượng </li>
  <li>2. <strong>Structural patterns</strong>: <strong>Strutural patterns</strong> cup cấp các cách để quản lý các mối quan hệ giữ các đối tượng và cũng tạo ra các cấu trúc lớp. Có một cách để đạt được là sử dụng kế thừa và sắp xếp để tạo ra đối tượng lớn từ các đối tượng nhỏ</li>
  <li>3. <strong>Behavioral patterns</strong>: <strong>Behavioral patterns</strong> là sự tập trung vào sự tương tác giữa các đối tượng. Trong trường hợp <strong>Behavioral patterns</strong> mô tả một khoảng thời gian và <strong>Structural patterns</strong> mô tả một hoặc nhiều những cấu trúc tĩnh, <strong>Behavioral patterns</strong> mô tả một quá trình</li>
</ul>

<h2>Creational Patterns</h2>
<h3>Module</h3>

<p>Được sử dụng rất thường xuyên trong quá trình phát triển phần mềm, module pattern có thể được xem như là một IIFE (Function thực thi ngay)</p>
```javascript
(function() {
  // code goes here!
})();
```
