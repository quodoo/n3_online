# D_MORI N3 Static Site

Repository này được publish trực tiếp bằng GitHub Pages từ branch `master` hoặc `main`, không dùng GitHub Actions.

## Cách deploy

1. Push toàn bộ nội dung repo này lên GitHub.
2. Vào `Settings -> Pages`.
3. Ở mục `Build and deployment`, chọn `Source = Deploy from a branch`.
4. Chọn branch `master` hoặc `main`, thư mục `/(root)`.
5. Lưu cấu hình và chờ GitHub Pages publish.

## Custom domain

Nếu dùng domain riêng, cách đơn giản nhất là tạo file `CNAME` ở root repo.

Ví dụ:

```text
learn.example.com
```

DNS cần trỏ đúng về GitHub Pages:

- Với subdomain như `n3.example.com`: tạo `CNAME` trỏ về `<owner>.github.io`.
- Với apex/root domain như `example.com`: tạo các bản ghi `A` tới dải IP GitHub Pages.

## Các lỗi hay gặp

- Repo đang để `Private` và gói GitHub hiện tại không hỗ trợ Pages cho private repo.
- Chưa bật `Source = Deploy from a branch` trong `Settings -> Pages`.
- Domain đã map DNS nhưng chưa có file `CNAME` ở root repo.
- Chưa chờ DNS propagate sau khi đổi domain.

## Lưu ý hiện trạng site

Site này đã sẵn `index.html` để redirect vào khoá học. Tuy nhiên nhiều trang con hiện vẫn tham chiếu tới các asset như `/css`, `/plugin`, `/cdn` mà repo này chưa chứa đầy đủ. Việc đó không chặn GitHub Pages publish, nhưng có thể làm một số trang hiển thị thiếu CSS/JS hoặc ảnh sau khi deploy.
