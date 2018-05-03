# Design Pattern with Javascript
Một trong những khía cạnh quan trọng nhất của việc viết code dễ dàng maintain là việc phát hiện ra những doạn code lặp lại và có thể tối ưu hóa chúng, đây là trường hợp mà design pattern chứng minh chúng vô giá - **Addy Osmani**.
Kể cả việc chúng ta có thể giải quyết được vấn đề khi viết **Javascript**, nhưng nó cũng có thể dẫn tới một số lỗi nếu chúng ta sử dụng sai **Design Pattern** hoặc áp dụng không đúng cách.
Lập trình viên có xu hướng sử dụng những framework mới nhất và những thư viện được xây dựng cho web app và kết hợp những thư viện đó vào trong một project, mà thường quên đi các ý tưởng cốt lõi đằng sau việc tạo ra các thư viện này.
**Design Pattern** giống như các bản thiết kế về những cách giải quyết vấn đề không phần mềm. Chúng được cấu trúc với các phương pháp hay nhất nhằm giúp tạo ra sự ổn định và trong nhiều trường hợp, chúng còn giúp bảo mật cho những ứng dụng của chúng ta.
Nhìn chung **Javascript** không phải là một ngôn ngữ lập trình truyền thống, vì thế nên việc phát hiện ra các **Design Pattern** trong **Javascript** có vẻ khó hơn nhưng không phải là không thể.

Trong bài viết này chúng ta sẽ tìm hiểu 5 mẫu **Design pattern** khác nhau phổ biến trong JS cũng như cách chúng ta có thể sử dụng chúng.

## Types of Design Patterns
Trong kĩ thuật phần mềm, có rất nhiều các mẫu **Design pattern** tồn tại. Các mẫu này được nhóm theo 3 kiểu dưới đây:

  1. **Creational patterns**: Kiểu pattern này tập trung vào việc tạo ra các đối tượng. Khi tạo đối tượng trong những ứng dụng lớn, có quá nhiều thứ làm cho ứng dụng trở lên phức tạp. **Creational patterns** sẽ giải quyết vấn đề đó bằng cách kiểm soát việc tạo ra các đối tượng.
  2. **Structural patterns**: **Strutural patterns** cup cấp các cách để quản lý các mối quan hệ giữ các đối tượng và cũng tạo ra các cấu trúc lớp. Có một cách để đạt được là sử dụng kế thừa và sắp xếp để tạo ra đối tượng lớn từ các đối tượng nhỏ.
  3. **Behavioral patterns**: **Behavioral patterns** là pattern tập trung vào sự tương tác giữa các đối tượng.

## Creational Patterns
### Module

Được sử dụng rất thường xuyên trong quá trình phát triển phần mềm, module pattern có thể được xem như là một **IIFE** (function thực thi ngay).
```js
(function() {
  // code goes here!
})();
```

Tất cả các **module** tồn tại bên trong [closure](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Closures). Các giá trị được import vào bằng việc truyền các giá trị thông qua function và export ra bằng cách return một object. Việc sử dụng các **module** rất hữu ích khi code hệ thống vượt qua một function Javascript khi chúng giúp giữ cho global scope sạch sẽ và cũng như giữ cho các hàm của bạn có thể import và export được.

Bên dưới là ví dụ của việc một **module** được thực thi:

```js
const options = {
  username: 'abcd',
  server: '127.0.0.1'
};

const ConfigObject = (function(params) {

  // return the publicly available things
  // able to use login function at the top of this module since it is hoisted
  return {
    login: login
  };

  const username = params.username || '',
        server = params.server || '',
        password = params.password || '';

  function checkPassword() {
    if (this.password === '') {
      console.log('no password!');
      return false;
    }
    return true;
  }

  function checkUsername() {
    if (this.username === '') {
      console.log('no username!');
      return false;
    }
    return true;
  }

  function login() {
    if (checkPassword() && checkUsername()) {
      // perform login
    }
  }
})(options);

```

Chú ý rằng những giá trị của **username** và **server** cũng như **password** được import và export liên tục. Sử dụng **module** sẽ đảm bảo cho cấu trúc dự án sạch sẽ, làm cho code dễ đọc và ít lỗi hơn.

### Builder
Có thể bạn đã từng làm với **Builder Pattern** trước đây mà không hề nhận ra. **Builder Pattern** cho phép chúng ta xây dựng các đối tượng mà không cần tạo ra chúng, tất cả những gì chúng ta cần làm là chọn loại đối tượng và giá trị của chúng. Hãy cùng xem ví dụ dưới đây trong jQuery:
```js
const myDiv = $('<div id="myDiv">This is a div.</div>');
// myDiv now represents a jQuery object referencing a DOM node.

const myText = $('<p/>');
// myText now represents a jQuery object referencing an HTMLParagraphElement.

const myInput = $('<input />');
// myInput now represents a jQuery object referencing a HTMLInputElement
```

Trong ví dụ đầu tiên, chúng ta truyền một vài nội dung vào trong thẻ div. Trong ví dụ thứ hai, chúng ta truyền một thẻ p trống. Và trong ví dụ thứ ba, chúng ta truyền vào một thẻ input. Kết quả của cả 3 biến trên là như nhau, chúng đều trả về một jQuery DOM node.

Cần lưu ý rằng biến **$** thông qua **Builder Pattern** trong jQuery. Trong mỗi ví dụ trên, mỗi đối tượng jQuery DOM đều có quyền truy cập vào tất cả các phương thức được cung cấp bởi thư viện jQuery như *hide()* hoặc *show()* mà không cần phải khởi tạo đối tượng bằng *document.createElement()* vì thư viện JS đã xử lý hết tất cả những việc đó.

Tạo ra mỗi phần tử DOM rồi thêm nội dung vào cho nó quả là việc không cần thiết và tốn thời gian. Ví dụ như việc tạo ra **myDiv** trong JS thuần như dưới đây:

```js
const myDiv     = document.createElement('div');
myDiv.id        = 'myDiv';
myDiv.innerText = 'This is a div.';
```

Bằng cách sử dụng **Builder pattern**, chúng ta có khả năng tập trung vào kiểu và nội dung của đối tượng, hơn là tập trung vào cách tạo ra nó.

## Structural Patterns

### Facade

Mục đích của **Facade pattern** là che giấu một lượng lớn code logic phức tạp vào trong một cuộc gọi hàm đơn giản. Các hàm chứa những hàm hoặc những lớp con bên trong đều được ẩn đi và được gọi tới thông qua một lời gọi thực thi hàm. Điều đó làm cho hàm này trở lên an toàn vì lập trình viên sẽ không cần phải để ý đến những logic bên trong nó và sẽ không tạo ra bất cứ thay đổi gì bên trong làm sai đi chức năng của hàm trong lúc làm việc với nó. Có thể bạn đã từng làm việc với nó trước đây mà không hề để ý, xem ví dụ dưới đây để rõ hơn:

```js
$(document).ready(function() {

  // all your code goes here...

});
```

Bất cứ khi nào chúng ta sử dụng phương thức *ready()*, chúng ta thực sự đã thực thi **Facade**. Hãy cùng xem chúng ta thực sự đã thực thi những gì trong lời gọi *ready()* này:

```js
ready: (function() {

  ...

  // Mozilla, Opera, and Webkit
  if (document.addEventListener) {
    document.addEventListener("DOMContentLoaded", idempotent_fn, false);
    ...
  }

  // IE event model
  else if (document.attachEvent) {

    // ensure firing before onload; maybe late but safe also for iframes
    document.attachEvent("onreadystatechange", idempotent_fn);

    // A fallback to window.onload, that will always work
    window.attachEvent("onload", idempotent_fn);

    ...    
  }

})
```

Để đảm bảo *ready()* được thực thi vào lúc thích hợp, thư viện **jQuery** đã giải quyết tất cả các vấn đề về sự không tương thích giữa các trình duyệt. Mozilla, Opera và Webkit sẽ sử dụng sự kiện **DOMContentLoaded** trong khi IE lại không giống vậy. Người dùng không thể nhận ra sự khác biệt đó vì đơn giản nó đã được giải quyết qua lời gọi *ready()*.

### Composites

**Composites** là các đối tượng bao gồm nhiều phần, và chúng chỉ tạo ra một thực thể duy nhất. Thực thể duy nhất này được coi như là một điểm truy cập cho tất cả các phần. Chúng có thể đơn giản hóa mọi thứ hoặc cũng có thể gây nhầm lẫn vì chúng ta có thể không biết thực sự thực thể này là điểm truy cập của bao nhiêu phần. Xem ví dụ bên dưới về **Composites Pattern**:

```js
$('.myList').addClass('selected');
$('#myItem').addClass('selected');

// dont do this on large tables, it's just an example.
$('#dataTable tbody tr').on('click', function(event) {
  alert($(this).text());
});

$('#myButton').on('click', function(event) {
  alert("Clicked.");
});
```

Như chúng ta có thể thấy, jQuery sử dụng **Composites Pattern** để cung cấp cho chúng ta một giao diện đơn giản. Sự kiện **onClick** được sử dụng trên nhiều phần tử DOM hoặc chỉ một phần tử DOM và chỉ có **event** đại diện cho tất cả chúng. Khi làm việc với **Composites Pattern**, chúng ta cần phải để ý đến việc chúng ta đang làm việc với một hay nhiều phần tử vì **Composites Pattern** sử dụng chung một giao diện cho cả hai. Nếu không để ý, chúng ta có thể bị nhầm lẫn và xảy ra những lỗi không mong muốn.

## Behavioral Patterns

### Observer

**Observer Pattern** thực thi một đối tượng duy nhất và duy trì tham chiếu đến nhiều đối tượng khác và phát ra thông báo khi có sự thay đổi trạng thái của những đối tượng đó. Khi chúng ta không muốn theo dõi một đối tượng, chúng ta có thể dễ dàng thay đổi nó. Ngoài việc thực hiện tốt với các đối tượng tách rời, các thành phần tái sử dụng, **Observer Pattern** giúp chúng ta xác định các phụ thuộc và yêu cầu sâu hơn về mối quan hệ giữa nhiều thành phần nhỏ trong một ứng dụng. Ở trong ví dụ dưới đây, chúng ta sẽ thực thi **Observer** bằng việc sử dụng ba phương thức:

+ **publish(data)**: được gọi bởi đối tượng khi có thông báo
+ **subscribe(observer)**: được gọi bởi đối tượng để thêm **observer** vào danh sách các **observer** của nó
+ **unsubscribe(observer)**: được gọi bởi đối tượng để xóa **observer** ra khỏi danh sách các **observer** của nó

Đa phần các thư việc JS ngày nay đều hỗ trợ cả ba phương thức trên như là một phần trong nền tảng của chúng. Những phương thức đó thường là:

+ **on()**
+ **attach()**
+ **trigger()**
+ **fire()**
+ **off()**
+ **detach()**

```js
var a         = $({});
$.subscribe   = a.on.bind(a);
$.unsubscribe = a.off.bind(a);
$.publish     = a.trigger.bind(a);

// Usage
document.on('recordsReceived', function(records) {
  // perform some actions, then fire an event

  $.publish('recordsShow', records);
});

// We can subscribe to this event and then fire our own event.
$.subscribe('recordsShow', function() {
  // display the records somehow
  ..

  // publish an action after they are shown.
  $.publish('recordsDisplayed');
});

$.subscribe('recordsDisplayed, function() {
    ...
});
```

Có thể thấy ở ví dụ trên, **Observer Pattern** rất dễ để sử dụng và cũng rất mạnh. Do thực tế là nó dựa trên những sự kiện tự nhiên, vậy nên JS rất phù hợp để sử dụng mẫu này. Chúng ta nên thận trọng trong việc sử dụng mẫu này khi có nhiều **observer** và đối tượng cùng được lắng nghe cùng lúc.

## Conclusion

Với các **mẫu thiết kế** bên trên, công bằng mà nói thì không có bất cứ một mẫu nào là hoàn hảo cả. Có nhiều mẫu giúp chúng ta tiếp cận và áp dụng vào những ứng dụng web hiện đại. Nếu muốn đọc nhiều hơn về các **Design Pattern**, có thể tham khảo cuốn [Learning JavaScript Design Patterns](https://addyosmani.com/resources/essentialjsdesignpatterns/book/) của [Addy Osmani](https://twitter.com/addyosmani).