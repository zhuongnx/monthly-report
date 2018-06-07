Hôm nay xin giới thiệu với các bạn 5 Laravel Blade directives sử dụng để đơn giản hóa templates của bạn và tìm hiểu về 1 số directives tiện lợi giúp bạn giải quyết các vấn đề cụ thể.Đối với những người mới tiếp cận với **Laravel Framework**,những mẹo này sẽ giúp bạn khám phá những tính năng tuyệt vời của Blade - Laravel's template engine.

Let's get started.

1. Kiểm tra user đã đăng nhập hay chưa
Khi kiểm tra người dùng có đăng nhập hay không, bình thường bạn sẽ dùng:

```
@if(auth()->user())
    // The user is authenticated.
@endif
```

Tuy nhiên, Laravel chung cấp cho bạn 1 derectives để thực hiện việc này 1 cách đươn giản và rõ ràng hơn:

```
@auth
    // The user is authenticated.
@endauth
```

2. Kiểm tra user có là `khách` hay không
Ngược lại của trường hợp trên, khi chung ta muốn check user chưa đăng nhập, thông thường ta sẽ sử dụng phương thực `guest()` trong `auth` helper:

```
@if(auth()->guest())
    // The user is not authenticated.
@endif
```

Tuy nhiên (lại tuy nhiên), Laravel cũng cung cấp cho ta `@guest` directive:

```
@guest
    // The user is not authenticated.
@endguest
```
Chúng ta có thể kết hợp 2 directives trên bằng cách sử dụng `else` statement:

```
@guest
    // The user is not authenticated.
@else
    // The user is authenticated.
@endguest
```

2. Include view khi nó tồn tại hoặc không

Chúng ta đi ngay vào ví dụ cho nó trực quan
```
@if(view()->exists('first-view-name'))
    @include('first-view-name')
@else
    @include('second-view-name')
@endif
```
Với đoạn code trên ta có thể diễn dải thành: include view `first-view-name` nếu nó tồn tại, ngược lại include `second-view-name`

Trông đoạn code trên khá rườm rà và không được clean cho lắm, thay vào đó chúng ta có thể dùng:
```
@includeFirst(['first-view-name', 'second-view-name']);
```

ngắn gọn, súc tính mà vẫn đẩy đủ ^_^.

4. Include view dự trên điều kiện

Thông thường chúng ta sẽ viết với `@if` condition:

```
@if($post->hasComments())
    @include('posts.comments')
@endif
```

Chúng ta có thể làm điều này 1 cách ngắn gọn và rõ ràng hơn với `@includeWhen` directive với chỉ 1 dòng code:
```
@includeWhen($post->hasComments(), 'posts.comments');
```

5. Include view nếu nó tồn tại

Thay vì chúng ta sử dụng:

```
@if(view()->exists('view-name'))
    @include('view-name')
@endif
```

Thay vào đó ta có thể sử dụng directive `@includeIf`:
```
@includeIf('view-name')
```

# Kết luận
Trên đây là 1 số directives hữu ích trong Laravel Blade mà mình sưu tầm được trên mạng cung như kinh nghiệm trong quá trình code.

Nếu bạn có đóng góp gì thêm vào bài viêt, vui lòng để lại comment bên dưới.

Rất cảm hơn các bạn (seeyou) !
