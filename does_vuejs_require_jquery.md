Nếu bạn đã code front-end Javascript được 1 thời gian, chăc có lẽ jQuery không còn xa lạ gì với bạn nữa. Bạn sẽ không thể tưởng tượng được project của bạn sẽ ra sao nếu không có nó. 

Nhưng đã đến lúc bạn nên bỏ thói quen đó của bạn, **bạn không cần jQuery ở mọi nơi nữa**

Hãy bắt đầu cuộc hành trình của bạn với Vuejs, tôi chắc rằng nhiều bạn đều có suy nghĩ "Tôi có thể làm điều đó dễ dàng với jQuery". Điều đó đúng, nhưng mọi chuyện đều có cách khác để giải quyết.

## Access the DOM
Chắc hẳn các bạn đều biết cách đơn giản để `hide/show` element với `v-show`. Vậy ngoài cách đó ra, bạn sẽ làm thế nào để chúng ta có thể access vào DOM element bây giờ?

Với jQuery bạn có thể sử dụng `var myElement = $('#my-element')`. Phải thừa nhận rằng nó rất `cool`, đó là cách ưu thích để xử lý với CSS selectors. Nhưng với thư viện API của jQuery, bạn không thể sử dụng hết được nó. Điều này khiến website của bạn phải luôn tải thư viện jQuery để bạn có thẻ sử dụng nó ở bất cứ đâu, điều này không cần thiết.

Bạn có thể làm điều nếu sử dụng `document.getElementById('my-element')` nhưng điều đó không phù hợp với cơ chế `DOM ảo` của Vue bởi vì các element có thể được render bất cứ lúc nào.

May mắn thay, Vue cung cấp API để truy xuất vào DOM element nhất định. Bạn có thể tham khỏa đoạn code HTML dưới đây:

```
<template>
  <div>
    ...
    <p ref="myElement">This is the content of my element.</p>
    ...
  </div>
</template>

<script>
export default {
  mounted () {
    console.log(this.$refs.myElement)
  }
}
</script>
```

Các bạn có thể thao khảo thêm [tại đây](https://vuejs.org/v2/api/#ref)

# Helper functions

Chúng ta đều sử dụng `$.each` function để loop array trong jQuery. Nhưng bây giờ với ES2015 và hàng tấn helper libraries bạn có thể include, ví dụ như `lodash`

Hãy làm 1 ví dụ nhỏ nhé !

Ta có mảng dữ liệu sau:

```
var myArray = ['we', 'love', 'javascript'];
```
Yêu cầu: Trả ra 1 mảng với các giá trị được chuyển thảnh uppercase:
 
```
 // jQuery
$.each(myArray, function(value, index) {
  myArray[index] = value.toUppercase();
});

// ES2015
myArray.forEach((value, index) => {
  myArray[index] = value.toUppercase()
})

// ES2015 (using map method)
myArray = myArray.map(value => value.toUppercase())

// lodash
var _ = require('lodash');
myArray = _.map(myArray, function(value) {
  return value.toUppercase();
});
```

# Kết luận

Bạn có trường hợp nào mà bạn tin rằng bạn cần jQuery? Hãy để lại comment để chúng ta cùng thảo luận nhé !


