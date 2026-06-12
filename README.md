# Phủ Dầy Vân Cát 360° — Tour thực tế ảo

Phần mềm tham quan thực tế ảo (virtual tour) cho **Phủ Vân Cát** — quần thể di tích
Phủ Dầy, xã Kim Thái, huyện Vụ Bản, **nơi Thánh Mẫu Liễu Hạnh
giáng sinh lần thứ hai**.

Người dùng đứng giữa từng điểm trong phủ, kéo nhìn 360°, bấm mũi tên để "đi" sang
điểm khác, bật bảng nội dung để đọc giới thiệu từng toà.

Tour gồm **34 điểm chụp** chia thành **7 nhóm khu**, có 1 ảnh bay flycam toàn cảnh
làm điểm mở đầu.

> Tour này nằm trong bộ sản phẩm **HeritaVault — Kho Số Di Tích**, dùng chung khung
> kỹ thuật với tour [Đền Bà Vũ 360°](https://daothinhuquynh-png.github.io/denbavu360/).

---

## 1. Tính năng

- Ảnh 360° equirectangular xem được trên trình duyệt (desktop, mobile, tablet)
- Mũi tên gắn thumbnail tròn + tên điểm đích để biết trước sẽ "đi" tới đâu
- Bảng nội dung chú thích **tự hiện** khi vào toà có giới thiệu, có nút bật/tắt
- 7 tab nhóm khu: Toàn cảnh · Cổng & Toà Phương Du · Ngũ Vân Lâu & Đại Bái ·
  Lầu Cô · Lầu Cậu · Cung Vua Cha · Cung Giám Sát · Cung Tứ Phủ · Cung Cấm ·
  Sơn Trang · Dải Vũ · Chùa Vân Cát
- Nhạc nền (chầu văn) bật/tắt
- Tự xoay, ẩn/hiện mũi tên, toàn màn hình, gyro xoay theo thiết bị (mobile)
- Màn hình mở đầu "Bắt đầu tham quan"
- Hoàn toàn chạy được offline (không cần mạng sau khi tải)

## 2. Công nghệ

- **Pannellum 2.5.6** (WebGL 360° viewer, MIT) — vendored tại `vendor/`
- Ảnh equirectangular JPG (gốc Insta360 11968×5984, nén web còn ~6000px wide)
- HTML/CSS/JS thuần, không build pipeline

## 3. Cấu trúc thư mục

```
tour/
├── index.html        — bản xem (cho người tham quan)
├── builder.html      — trình dựng tour (cho người soạn nội dung)
├── tour.json         — dữ liệu tour (34 cảnh, 96 hotspots)
├── serve.py          — server local có GET /panos + POST /save
├── panos/            — 34 ảnh 360° đã nén web (.jpg)
├── thumbs/           — 34 thumbnail (420px) cho menu địa điểm
├── audio/            — nhạc nền
├── vendor/           — Pannellum offline
└── backups/          — sao lưu tự động tour.json (gitignored)
```

## 4. Chạy local

```
cd tour
python3 serve.py        # mặc định cổng 8099
```

Mở `http://localhost:8099/` để xem tour, `/builder.html` để chỉnh sửa.

## 5. Quy trình dựng tour mới (cho di tích khác)

Xem [HeritaVault-Engine](https://github.com/daothinhuquynh-png) — khung sạch
dùng chung; mỗi đền là một bản sao độc lập (ảnh + `tour.json` + repo riêng).

---

**Tác giả**: Đào Thị Như Quỳnh — daothinhuquynh@gmail.com
**Bản quyền ảnh**: Tác giả · Bản quyền nội dung: theo lý lịch di tích Phủ Dầy.
