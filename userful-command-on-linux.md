1. Xem file log realtime

Trong nhiều trường hợp khi `debug` chúng ta cần xem nội dung `logs file` realtime, khi đó chúng ta có thể dùng lệnh
```
tail -f /path/to/file/to/watch
```

2. Xem cấu trúc cây thư mục bằng lệnh tree

Lệnh `tree` cho phép chúng ta xem cấu trúc và cấp thư mục, kiểu như này:
```
$ tree src
src
├── assets
│   ├── css
│   ├── modules
│   └── scss
├── public
│   ├── css
│   ├── modules
│   └── scss
└── store
    ├── css
    ├── modules
    └── scss

12 directories, 0 files
```
Với `src` là thứ mục muốn xem

3. Tạo nhiều thư mục cùng lúc

Như ở trên ta thấy có thư mục cha là src, trong đó có các thư mục con tương ứng là `assets, public, store` trong mỗi thư mục con lại có các thư mục con tương ứng là `scss, css, modules`

Để có thể tạo liền một lúc cấu trúc thu mục như vậy ta có thể dùng lệnh

```
$ mkdir -pv src/{assets,public,store}/{scss,css,modules}
mkdir: created directory 'src'
mkdir: created directory 'src/assets'
mkdir: created directory 'src/assets/scss'
mkdir: created directory 'src/assets/css'
mkdir: created directory 'src/assets/modules'
mkdir: created directory 'src/public'
mkdir: created directory 'src/public/scss'
mkdir: created directory 'src/public/css'
mkdir: created directory 'src/public/modules'
mkdir: created directory 'src/store'
mkdir: created directory 'src/store/scss'
mkdir: created directory 'src/store/css'
mkdir: created directory 'src/store/modules'
```

4. Trở về thư mục trước đó

Ví dụ ta cd tới một đường dẫn rất là dài, sau đó lại cd đi chỗ khác. Nếu quay lại thư mục trước thì phải gõ rất dài, có thể dùng lệnh
```
$ cd -
```
Thực chất là sử dụng biến môi trường OLDPWD
```
$ env | grep -i pwd
PWD=/home/nguyen.xuan.huong/Desktop/study_report
OLDPWD=/var/www/html
```

5. Copy public-key lên server tự động

Thông thường khi muốn `ssh` lên server bằng key, ta thường add `ssh-key` thủ công lên server thủ công như sau:

```
~$ mkdir ~/.ssh
~$ touch ~/.ssh/authorized_keys
~$ # copy public-key to authorized_keys
~$ chmod 700 ~/.ssh
~$ chmod 600  ~/.ssh/authorized_keys
```
Có 1 cách đơn giản hơn đó là sử dụng lệnh `ssh-copy-id user@ip_address`, sau đó nhập `password của user` thì `public-key` sẽ tự được copy lên server. Thư mục `.ssh` và tập tin `authorized_keys` cũng sẽ được tạo đúng quyền chúng ta cần.

6. Thực thi định kì một lệnh và xuất ra màn hình

Ví dụ mình chuyển 1 file 9GB qua một server khác, mình có thói quen kiểm tra xem kích thước của file đó bên server kia tới đâu rồi nên hay phải `ls -lh hera_9GB.mp4` lặp đi lặp lại.

Có một cách khác để tự động thực thi lệnh trên mỗi 2s (mặc định) bằng lệnh watch như sau:

```
~$ watch 'ls -lh hera_9GB.mp4'
```

7. Xem các file log mới nhất

Trong thư mục `/var/log/nginx` có rất nhiều file, có khi cả vài trăm file. Một mẹo ta có thể dùng lệnh ls với các tùy chọn sau để hiển thị file được thay đổi mới nhất nằm ở dưới cùng.

```
$ ls -larht
```

Giải thích:
```
-l: để long list
-a: để hiển thị file ẩn
-h: để hiển thị size dễ đọc
-t: để sort theo modify time
-r: để đảo ngược, nghĩa là file được sửa gần nhất ở cuối
```
