# Bản Tin Sáng v2

Trang tin tức tổng hợp tiếng Việt, tự động cập nhật 3 lần/ngày. Miễn phí, không cần server.

## 📰 Nội dung

7 chuyên mục từ 15+ nguồn báo chính thống:

| Chuyên mục | Nguồn |
|---|---|
| Kinh tế vĩ mô & Thị trường | VnExpress, CafeF, Dân Trí, Thanh Niên, Tuổi Trẻ, VietNamNet, VnEconomy |
| Doanh nghiệp & Kinh doanh | CafeBiz, Znews, Người Lao Động, BrandsVietnam |
| Xã hội & Đời sống đô thị | VnExpress, Dân Trí, Znews, Tuổi Trẻ, VietNamNet |
| Tâm lý & Phong cách sống | Tatler, Vietcetera, Dân Trí, Thanh Niên, VnExpress |
| Sự nghiệp & Xu hướng | CafeBiz, Thanh Niên, VnExpress, VnEconomy |
| Công nghệ | VnExpress, Dân Trí, Znews, Thanh Niên, VietNamNet, Tuổi Trẻ, CafeBiz |

**Tính năng đặc biệt:**
- Tab **Tổng hợp** — 12 tin nổi bật nhất, chấm điểm theo độ nóng (nhiều báo cùng đưa)
- **Điểm nhanh** — tóm tắt tự động từ tiêu đề cho từng chuyên mục
- Badge **"N báo cùng đưa"** — biết ngay tin nào đang hot
- **Slider ngang** — 2 trang × 8 tin mỗi chuyên mục
- **Bộ lọc** — tự động loại tin showbiz, thể thao, xổ số
- **Nút cập nhật thủ công** — bấm 1 lần, chờ 30 giây có tin mới

---

## ✅ Đã triển khai (Deployed)

Repo này đã được tạo và cấu hình sẵn cho tài khoản **irisnguyen0411-lgtm**. Các bước còn lại:

1. Vào **Settings → Pages**, mục "Branch" chọn **main** / **(root)**, bấm **Save**.
2. Vào tab **Actions → Cap nhat Ban Tin Sang → Run workflow** để chạy lần đầu.
3. Sau ~30–40 giây, xem trang tại:
```
https://irisnguyen0411-lgtm.github.io/ban-tin-sang/v2.html
```

---

## 📅 Lịch tự động cập nhật

Trang tự cập nhật 3 lần/ngày (giờ Việt Nam):
- **05:30** sáng
- **11:30** trưa
- **17:30** chiều

Hoặc bấm nút **⟳ Cập nhật tin ngay** trên trang bất cứ lúc nào.

> Lưu ý: GitHub Actions có thể trễ 15–60 phút vào giờ cao điểm. Đây là hạn chế của GitHub, không phải lỗi.

---

## 🛠 Tuỳ chỉnh

### Thêm/bớt nguồn tin

Sửa danh sách `SECTIONS` trong file `fetch_news.py`. Mỗi chuyên mục có dạng:
```python
{
    "id": "ten-muc",
    "title": "Tên hiển thị",
    "feeds": [
        ("Tên báo", "https://example.com/rss"),
    ],
}
```

### Thêm từ khóa lọc

Thêm vào danh sách `BLOCKED_KEYWORDS`:
```python
BLOCKED_KEYWORDS = [
    "sao việt", "showbiz",   # đã có sẵn
    "từ khóa mới",           # thêm ở đây
]
```

---

## 📁 Cấu trúc file

```
ban-tin-sang/
├── fetch_news.py                 ← Script chính (lấy RSS, tạo HTML)
├── .github/workflows/update.yml  ← Lịch chạy tự động
├── index.html                    ← Trang v1 (tự tạo khi chạy workflow)
├── v2.html                       ← Trang v2 với tab + điểm nhanh (tự tạo)
└── README.md                     ← File này
```

---

## 💡 Cách hoạt động

1. GitHub Actions chạy `fetch_news.py` theo lịch
2. Script tải RSS từ 15+ báo song song, lọc tin trùng/showbiz/thể thao
3. Tính "độ nóng" — chủ đề xuất hiện trên nhiều báo được ưu tiên
4. Tạo trang HTML tĩnh (`index.html` + `v2.html`) rồi đẩy lên repo
5. GitHub Pages phục vụ trang — không cần server

---

Được tạo bằng Python, GitHub Actions & GitHub Pages. Hoàn toàn miễn phí.
