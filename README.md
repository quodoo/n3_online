# D_MORI N3 Static Site

Repository này được publish trực tiếp lên GitHub Pages từ branch `master` hoặc `main` qua GitHub Actions.

## Cách deploy

1. Push toàn bộ nội dung repo này lên GitHub.
2. Vào `Settings -> Pages`.
3. Ở mục `Build and deployment`, chọn `Source = GitHub Actions`.
4. Chờ workflow `Deploy GitHub Pages` chạy xong.

## Custom domain

Nếu dùng domain riêng, có 2 cách:

1. Khai báo repo variable `GH_PAGES_CUSTOM_DOMAIN` với giá trị là domain cần dùng. Workflow sẽ tự tạo file `CNAME` khi deploy.
2. Hoặc tự tạo file `CNAME` ở root repo nếu muốn cố định trực tiếp trong mã nguồn.

DNS cần trỏ đúng về GitHub Pages:

- Với subdomain như `n3.example.com`: tạo `CNAME` trỏ về `<owner>.github.io`.
- Với apex/root domain như `example.com`: tạo các bản ghi `A` tới dải IP GitHub Pages.

## Các lỗi hay gặp

- Repo đang để `Private` và gói GitHub hiện tại không hỗ trợ Pages cho private repo.
- Chưa bật `Source = GitHub Actions` trong `Settings -> Pages`.
- Domain đã map DNS nhưng chưa có `CNAME` trong artifact deploy.
- Chưa chờ DNS propagate sau khi đổi domain.

## Lưu ý hiện trạng site

Site này đã sẵn `index.html` để redirect vào khoá học. Tuy nhiên nhiều trang con hiện vẫn tham chiếu tới các asset như `/css`, `/plugin`, `/cdn` mà repo này chưa chứa đầy đủ. Việc đó không chặn GitHub Pages publish, nhưng có thể làm một số trang hiển thị thiếu CSS/JS hoặc ảnh sau khi deploy.
