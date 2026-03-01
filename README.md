# Chú Đại Bi — PWA

Trang web PWA hiển thị bài kinh **Chú Đại Bi** (Đại Bi Tâm Đà La Ni), được xây dựng hoàn toàn bằng HTML5 và CSS3 thuần — không dùng framework hay thư viện bên ngoài.

---

## Tính năng

- **PWA** — Cài được lên màn hình chính (Add to Home Screen), hoạt động offline
- **Responsive** — Hỗ trợ mọi kích thước màn hình từ 320px đến 2560px+
- **Giao diện tối – vàng** — Phong cách Phật giáo cổ điển, dễ đọc trong bóng tối
- **Phân nhóm 10 đoạn** — Cấu trúc bài kinh được chia theo truyền thống
- **Kiểu chữ phân biệt** — "Nam mô" / "Án" (vàng đậm), "ta bà ha" (vàng nhạt, nghiêng)
- **Scroll-to-top** — Nút ▲ xuất hiện khi cuộn xuống
- **In ấn** — CSS riêng cho chế độ print (nền trắng, chữ đen)
- **Giảm chuyển động** — Tôn trọng `prefers-reduced-motion`

---

## Cấu trúc

```
chudaibi/
├── index.html      # Trang chính — nội dung bài kinh + toàn bộ CSS
├── manifest.json   # PWA manifest (tên, icon, màu nền)
├── sw.js           # Service Worker — cache offline (cache-first)
├── icon.svg        # Icon hoa sen vàng trên nền tối
├── chu-dai-bi.md   # Nguồn văn bản gốc
└── README.md
```

---

## Chạy cục bộ

Vì PWA yêu cầu Service Worker chạy trên HTTP (không phải `file://`), cần dùng local server:

```bash
# Dùng Node.js (npx)
npx serve .

# Hoặc Python
python -m http.server 8080

# Hoặc VS Code → Live Server (chuột phải index.html → Open with Live Server)
```

Sau đó mở trình duyệt tại `http://localhost:3000` (hoặc port tương ứng).

---

## Kiểm tra PWA

Mở **DevTools** (`F12`) → tab **Application**:

| Mục | Trạng thái mong đợi |
|-----|---------------------|
| Manifest | Hiển thị tên, icon, màu theme |
| Service Workers | Status: activated and running |
| Cache Storage | `chu-dai-bi-v1` chứa 4 file |

**Test offline:** Network tab → chọn `Offline` → reload trang — trang vẫn hiển thị bình thường.

---

## Cấu trúc bài kinh (10 đoạn)

| Đoạn | Dòng | Nội dung |
|------|------|----------|
| I | 1–3 | Mở đầu |
| II | 4–6 | Nam mô hắc ra |
| III | 7–12 | Nam mô a rị da |
| IV | 13–14 | Án, tát bà ra phạt duệ |
| V | 15–18 | Nam mô tất kiết |
| VI | 19–27 | Nam mô na ra cẩn trì |
| VII | 28–29 | Án a bà lô hê |
| VIII | 30–45 | Ma ha bồ đề tát đỏa |
| IX | 46–56 | Hô lô hô lô |
| X | 57–87 | Ta bà ha (phần kết) |

---

## Công nghệ

- **HTML5** — Semantic markup, PWA meta tags
- **CSS3** — Custom properties, `clamp()`, Flexbox, media queries, `@media print`
- **Service Worker API** — Cache-first strategy, offline support
- **Web App Manifest** — Installable PWA
