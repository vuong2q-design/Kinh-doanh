# ƯỚC TÍNH: TỰ XÂY OMS/CRM ĐA KÊNH BẰNG CLAUDE CODE — MẤT BAO LÂU, BAO NHIÊU TIỀN

> Tỷ giá quy đổi tạm tính 1 USD ≈ 26.000đ. Các con số lương, phí SaaS là ước tính thị trường để so sánh — cần kiểm tra báo giá thực tế tại thời điểm làm.

---

## 1. LÀM RÕ PHẠM VI TRƯỚC — HAI BÀI TOÁN RẤT KHÁC NHAU

| | Clone đầy đủ "như Nhanh.vn/Sapo" | OMS/CRM nội bộ cho riêng công ty |
|---|---|---|
| Bản chất | Sản phẩm SaaS thương mại: đa khách hàng (multi-tenant), POS bán tại quầy, app mobile, hàng trăm tính năng, kết nối hàng chục đối tác, đội hỗ trợ | Một hệ thống cho một công ty, chỉ ~20% tính năng mình thực dùng: đơn đa kênh, tồn kho, khách hàng, vận chuyển, đối soát |
| Thời gian | 1–2 năm trở lên, kể cả có AI | **6–16 tuần** (chi tiết dưới) |
| Tiền | Nhiều tỷ đồng | **Vài chục triệu đồng** |
| Có nên làm? | ❌ Không — trừ khi muốn đổi nghề sang bán phần mềm | ✅ Đây mới là bài toán của công ty |

Phần còn lại của tài liệu tính cho **bản nội bộ**.

## 2. KHỐI LƯỢNG CÔNG VIỆC — BẢN NỘI BỘ GỒM GÌ

1. **Lõi dữ liệu:** sản phẩm/SKU, đơn hàng, khách hàng, tồn kho (PostgreSQL) + màn hình quản trị web
2. **Kết nối sàn:** Shopee Open Platform, TikTok Shop Partner API, Lazada Open Platform — nhận đơn qua webhook, đồng bộ tồn kho, cập nhật trạng thái
3. **Kết nối vận chuyển/3PL:** GHN / Viettel Post / Boxme — đẩy đơn, nhận vận đơn
4. **CRM & chăm sóc:** hồ sơ khách hợp nhất đa kênh, phân khúc, luồng ZNS (xác nhận, hướng dẫn dùng, nhắc tái mua)
5. **Đối soát & báo cáo:** khớp tiền–đơn (Casso webhook), COD 3PL, P&L theo SKU, dashboard

## 3. THỜI GIAN — VỚI 1 NGƯỜI KỸ THUẬT + CLAUDE CODE

| Giai đoạn | Nội dung | Thời gian |
|---|---|---|
| **MVP** | Lõi dữ liệu + UI quản trị + kết nối **1 sàn** (Shopee) + GHN + webhook tiền về | **6–8 tuần** |
| **Bản đủ** | + TikTok Shop, Lazada + tồn kho đa kho + đối soát tự động + CRM/ZNS + phân quyền + báo cáo | **+4–8 tuần** |
| **Tổng** | | **~3–4 tháng lịch** |

**Hai điểm nằm ngoài tốc độ code — quyết định tiến độ thật:**
- **Chờ duyệt tư cách developer/partner của các sàn: 2–6 tuần mỗi sàn** (Shopee Open Platform, TikTok Shop Partner Center đều phải đăng ký và được duyệt). Chạy song song được, nhưng phải **nộp đơn ngay từ tuần đầu** — đây mới là đường găng, không phải code.
- **Chạy bóng (shadow run) 2–4 tuần:** hệ tự xây chạy song song với Nhanh.vn/Sapo, đối chiếu từng đơn từng đồng trước khi cắt chuyển. Đơn thật là tiền thật — không bỏ bước này.

So sánh: không có Claude Code, cùng phạm vi này cần đội 2–3 lập trình viên trong 6–9 tháng. Claude Code viết phần lớn code tích hợp, màn hình quản trị, test; người kỹ thuật thiết kế, review và chịu trách nhiệm vận hành.

## 4. TIỀN — BA KỊCH BẢN

### Chi phí công cụ & hạ tầng (mọi kịch bản đều cần)
| Khoản | Mức | Thành tiền 4 tháng |
|---|---|---|
| Claude gói **Max** (dùng Claude Code cường độ cao cả ngày) | $100–200/tháng ≈ 2,6–5,2 triệu đ/tháng | ~10–21 triệu đ |
| VPS + PostgreSQL managed + domain + backup | ~0,5–1,5 triệu đ/tháng | ~2–6 triệu đ |
| **Cộng** | | **~12–27 triệu đ** |

(Gói Pro $20/tháng ≈ 520.000đ dùng được cho cường độ vừa; dự án dồn dập 3–4 tháng nên tính gói Max cho chắc. Sau khi xây xong, duy trì chỉ cần Pro + VPS ≈ **1–1,5 triệu đ/tháng**.)

### Kịch bản A — Giám đốc/người nhà rành kỹ thuật tự làm cùng Claude Code
- Tiền mặt: **~12–27 triệu đ tổng**, không tốn lương
- Đổi lại: 3–4 tháng đó người làm bị "khóa" vào dự án này

### Kịch bản B — Thuê 1 kỹ thuật (mức phổ biến 15–30 triệu đ/tháng × 4 tháng)
- Lương: 60–120 triệu đ + công cụ 12–27 triệu đ → **~75–150 triệu đ tổng**
- Người này sau đó chính là "phòng Công nghệ & Dữ liệu" trong kế hoạch — không phải chi phí chỉ cho riêng OMS

### Kịch bản C — Cứ thuê Nhanh.vn/Sapo (để so sánh)
- Gói OMS đa kênh phổ biến: ~0,3–2 triệu đ/tháng tùy gói → **~4–25 triệu đ/năm**
- Có ngay trong 1 ngày, không rủi ro kỹ thuật

## 5. KẾT LUẬN — TÍNH THUẦN TIỀN THÌ THUÊ VẪN RẺ HƠN 2–3 NĂM ĐẦU

Nhìn thẳng con số: nếu phải trả lương kỹ thuật (kịch bản B), tự xây đắt hơn thuê SaaS vài năm liền. Tự xây chỉ thắng khi tính đủ các giá trị mà SaaS không bán:

1. **Dữ liệu khách hàng là của mình 100%** — nền cho mọi AI (chatbot, tái mua, dự báo) mà SaaS không cho chạm sâu
2. **Không giới hạn** người dùng, số đơn, số luồng tự động — phí SaaS tăng theo quy mô, code tự xây thì không
3. **Tùy biến vô hạn** — chính là điều kiện để đạt mô hình "tự động hóa tối đa" đã vạch ra; SaaS chỉ cho tự động hóa trong khuôn của họ
4. **Tài sản tích lũy** — hệ thống + người kỹ thuật này dùng chung cho mọi automation khác của công ty

## 6. KHUYẾN NGHỊ — GIỮ LỘ TRÌNH 2 BƯỚC, THÊM 3 VIỆC LÀM NGAY

Giữ nguyên kế hoạch đã chốt: **thuê OMS để bán ngay từ tuần 2–3, tự xây khi vượt ~100–200 đơn/ngày** (lúc đó phí SaaS theo quy mô bắt đầu đắt, và dữ liệu đã đủ để đáng sở hữu). Ba việc nên làm ngay từ bây giờ để ngày tự xây rút ngắn còn một nửa:

1. **Nộp đơn developer Shopee / TikTok Shop / Lazada ngay tuần 1** — chờ duyệt là đường găng, không tốn tiền
2. **Xây trước lớp CRM/chăm sóc + đối soát bằng Claude Code** (các script đã nằm trong kế hoạch tự động hóa) — phần SaaS làm yếu nhất, rủi ro thấp nhất, dùng được ngay cả khi vẫn thuê OMS
3. **Mọi dữ liệu từ OMS thuê phải đổ về kho dữ liệu của mình mỗi ngày** — khi chuyển sang hệ tự xây thì lịch sử không mất

Rủi ro cần quản khi tự xây: API sàn đổi phiên bản (cần người bảo trì — đã có trong vai trò phòng Công nghệ), lỗi xử lý đơn thật (giải bằng shadow run), bảo mật dữ liệu khách (phân quyền + backup từ ngày 1).
