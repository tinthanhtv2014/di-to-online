# Đi Tò Online 3D — gói deploy public

Game phòng giam chibi chơi online nhiều người qua Firebase (project di-to-44436).

File trong gói:
- index.html — toàn bộ game (đã gắn sẵn firebaseConfig của project di-to-44436)
- assets/three.min.js — thư viện 3D
- firebase.json, .firebaserc — cấu hình Firebase Hosting
- firestore.rules — luật bảo vệ database (chỉ người chơi đã đăng nhập ẩn danh mới đọc/ghi được)

Repo GitHub của game: https://github.com/tinthanhtv2014/di-to-online (đã tạo sẵn, public).

## Bước 1 — Up code lên GitHub
Cách không cần git: mở https://github.com/tinthanhtv2014/di-to-online/upload
-> kéo thả TẤT CẢ file trong gói này vào (giữ nguyên thư mục assets) -> Commit changes.
Ai quen git thì clone repo rồi chép file đè vào:
     git clone https://github.com/tinthanhtv2014/di-to-online.git
     (chép toàn bộ file trong gói này vào thư mục vừa clone, giữ nguyên cấu trúc)
     git add .
     git commit -m "Di To Online"
     git push

## Bước 2A — Deploy lên Firebase Hosting (link di-to-44436.web.app)
Cài Node.js trước, rồi mở terminal trong thư mục repo (nơi có firebase.json):
     npm install -g firebase-tools
     firebase login
     firebase deploy
Xong! Link public: https://di-to-44436.web.app

## Bước 2B — Hoặc deploy lên Render (tự cập nhật mỗi lần push GitHub)
1. Vào https://dashboard.render.com -> New -> Static Site -> nối GitHub -> chọn repo di-to-online.
2. Build Command: để trống. Publish Directory: . (gốc repo).
3. Create Static Site -> Render cấp 1 link dạng ten-game.onrender.com.

## Bước 2C — Hoặc bật GitHub Pages (nhanh nhất để test)
1. Mở repo -> Settings -> Pages -> Source: Deploy from a branch -> branch main, thư mục / (root) -> Save.
2. Link public: https://tinthanhtv2014.github.io/di-to-online/

## Lưu ý
- Mọi bản deploy đều dùng chung database Firebase di-to-44436: bạn bè mở link nào cũng vô chung phòng được bằng mã phòng 6 ký tự.
- firebaseConfig trong game là cấu hình web công khai của Firebase (không phải mật khẩu) nên để trong code public là bình thường; dữ liệu được bảo vệ bằng firestore.rules + đăng nhập ẩn danh.
- Project Firebase cần đã bật Authentication (Anonymous) và Firestore — bộ đôi này đã được bật sẵn cho project di-to-44436.
