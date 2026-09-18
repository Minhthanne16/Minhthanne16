# Kích hoạt profile

## Đưa thay đổi lên GitHub

Repository public phải giữ tên `Minhthanne16/Minhthanne16`, README ở nhánh mặc định `main`.

Chạy trong PowerShell sau khi kiểm tra nội dung:

```powershell
Set-Location 'C:\Users\thann\.cline\data\workspaces\chat\minhthanne16-profile'
git add README.md SETUP.md assets/night-sky.svg .github/workflows/snake.yml
git commit -m "Style profile with animated night sky and contribution snake"
git push origin main
```

## Contribution snake

1. Mở repository → **Actions**. Cho phép Actions nếu GitHub yêu cầu.
2. Chọn **Generate contribution snake** → **Run workflow** → nhánh `main`.
3. Đợi workflow thành công. Nhánh `output` chứa hai ảnh SVG, README tự sử dụng chúng.
4. Workflow cập nhật mỗi ngày lúc 00:23 UTC (07:23 giờ Việt Nam), có thể chạy trễ do lịch của GitHub.

Lần push đầu tiên có file workflow cũng kích hoạt tạo ảnh. Trước lần chạy thành công đầu tiên, ảnh rắn chưa tồn tại nên có thể hiện lỗi tải ảnh. Không cần bật GitHub Pages hoặc tạo personal access token.

Workflow yêu cầu `contents: write` để xuất ảnh lên nhánh `output`. Nếu lỗi 403, kiểm tra chính sách Actions và branch protection; không tắt bảo vệ nhánh `main`. GitHub có thể tạm dừng lịch chạy trong repository public không hoạt động 60 ngày; bật lại trong Actions khi cần.

Đây là ảnh động mô phỏng dữ liệu contribution, không phải trò chơi tương tác và không thay thế bảng contribution mặc định.

## Spotify

Tính năng này cần chủ tài khoản tự đăng nhập và cấp quyền. Không thể lấy bài đang nghe chỉ từ username GitHub.

1. Đọc thông tin dịch vụ bên thứ ba tại https://github.com/kittinan/spotify-github-profile.
2. Nếu đồng ý sử dụng dịch vụ, mở https://spotify-github-profile.kittinanx.com/api/login và đăng nhập Spotify.
3. Kiểm tra quyền yêu cầu trước khi đồng ý. Theo tài liệu, dịch vụ lưu access token, refresh token và thời điểm hết hạn để lấy trạng thái nghe nhạc. Chỉ dùng nếu bạn tin tưởng dịch vụ.
4. Sao chép đoạn Markdown thẻ nhạc do dịch vụ tạo. Có thể dùng theme `novatorem` hoặc `default`, màu nền `0d1117`, màu thanh nhạc `7ee7c5`, `cover_image=true` và `show_offline=true`.
5. Trong `README.md`, thay phần nội dung nằm giữa `<!-- SPOTIFY:START -->` và `<!-- SPOTIFY:END -->` bằng đoạn Markdown đó, giữ lại hai marker.
6. Commit/push README, phát một bài hát trên Spotify và kiểm tra profile. GitHub cache ảnh nên trạng thái có thể trễ.

Bạn có thể gửi lại **đoạn Markdown ảnh công khai** để mình tích hợp đúng vị trí. Không gửi mật khẩu, access token, refresh token hay client secret. Không đưa thông tin bí mật vào git.

Bài hát đang nghe sẽ được hiển thị công khai. Có thể thu hồi quyền ứng dụng trong trang quản lý ứng dụng của tài khoản Spotify. Dịch vụ bên thứ ba có thể gián đoạn hoặc giới hạn đăng nhập; nếu vậy cần phương án tự host riêng, không dùng thẻ nhạc của tài khoản khác để thay thế.

## Animation và kiểm tra

Banner `assets/night-sky.svg` được lưu ngay trong repository, không cần dịch vụ tạo banner. Các ngôi sao có hiệu ứng nhấp nháy nhẹ và tắt chuyển động khi trình duyệt hỗ trợ `prefers-reduced-motion` trong ảnh SVG. Không có script hoặc font bên ngoài.

Sau khi push, kiểm tra profile ở cả giao diện sáng/tối, ảnh banner, thẻ Spotify và workflow. Preview Markdown của IDE có thể hiển thị SVG động khác với GitHub; cần kiểm tra thực tế trên GitHub sau khi xuất bản.
