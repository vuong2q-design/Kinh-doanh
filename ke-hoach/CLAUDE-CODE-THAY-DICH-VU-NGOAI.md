# RÀ SOÁT: CHỖ NÀO DÙNG CLAUDE CODE TỰ XÂY THAY VÌ THUÊ NGOÀI

Rà lại danh mục công cụ trong `so-do-dong-chay-du-lieu.html` theo nguyên tắc: **tự xây bằng Claude Code khi phần mềm chỉ là "logic + API"; giữ thuê ngoài khi dính pháp lý, hạ tầng vật lý, hoặc giấy phép nền tảng.**

---

## 1. THAY ĐƯỢC NGAY — Claude Code tự xây, bỏ hẳn phí thuê

| Đang dự kiến thuê | Thay bằng | Vì sao thay được |
|---|---|---|
| **Make / Zapier** (trục tự động hóa, phí theo số luồng) | Claude Code viết các script tự động hóa chạy trên server rẻ (VPS ~100–200k/tháng) hoặc serverless gần như miễn phí (Cloudflare Workers, Google Cloud Functions) | Toàn bộ luồng "đơn mới → 3PL → báo khách", "tiền về → khớp đơn", "tồn chạm ngưỡng → PO nháp" chỉ là code gọi API + lịch chạy. Claude Code viết và bảo trì được hết, không giới hạn số luồng |
| **Chatbot SaaS** (AhaChat, Chatfuel... phí tháng theo kênh) | Claude Code xây connector webhook Zalo OA / Messenger / website ↔ Claude API | Phần "nền chatbot" chỉ là nhận tin → gọi Claude API kèm kho kiến thức → trả lời. Tự xây còn kiểm soát được hàng rào tuân thủ tốt hơn SaaS |
| **Landing page / website builder** (phí tháng Haravan Web/Shopify nếu chỉ cần giới thiệu + đặt hàng đơn giản) | Claude Code dựng website tĩnh/Next.js, host miễn phí (Cloudflare Pages, Vercel), form đặt hàng đẩy thẳng vào hệ thống đơn | Website giới thiệu sản phẩm + landing bán hàng là việc Claude Code làm rất nhanh; chỉ cần nền tảng thuê khi muốn giỏ hàng + cổng thanh toán dựng sẵn ngay lập tức |
| **Báo cáo sáng / tổng hợp số liệu** (tính năng trả phí của các nền tảng) | Script Claude Code: gom số từ kho dữ liệu → Claude API viết nhận định → gửi Telegram/Zalo 7h | Đây là mẫu việc "đọc số + viết chữ" — đúng sở trường, chạy cron là xong |
| **Hàng đợi duyệt** (Lark/Trello bản trả phí) | Bot Telegram do Claude Code viết: mỗi việc cần duyệt là 1 tin nhắn kèm nút ✅/❌, bấm là hệ thống chạy tiếp | Miễn phí, duyệt ngay trên điện thoại, log đầy đủ |
| **Kho tri thức Notion** (bản trả phí khi thêm người/AI) | Chính **repo Git này**: SOP, bộ quy tắc tuân thủ, brief sản phẩm, hồ sơ lô — lưu dạng markdown | Cộng hưởng mạnh nhất: Claude Code đọc trực tiếp repo làm "nguồn sự thật", có lịch sử sửa đổi, ai sửa gì khi nào đều truy được |
| **Dashboard** (Metabase cloud trả phí) | Looker Studio (vốn miễn phí) **hoặc** Claude Code dựng dashboard web tự host | Chỉ thay khi cần dashboard tùy biến sâu; Looker Studio miễn phí vẫn là lựa chọn mặc định |

## 2. THAY MỘT PHẦN — tự xây lõi, giữ dịch vụ cho phần khó

| Đang dự kiến thuê | Phần Claude Code tự xây | Phần vẫn giữ thuê / vì sao |
|---|---|---|
| **OMS/CRM Nhanh.vn / Sapo** (phí tháng) | Giai đoạn sau: hệ quản lý đơn + CRM riêng (Shopee, TikTok Shop, Lazada đều có Open API) | Giai đoạn đầu **giữ thuê**: kết nối sàn cần duyệt tư cách đối tác API, tốn thời gian; thuê sẵn để bán được ngay. Khi >100–200 đơn/ngày, tự xây sẽ rẻ hơn và tùy biến sâu hơn — Claude Code làm được vì đây là CRUD + đồng bộ API thuần túy |
| **Metric.vn** (nghiên cứu số liệu sàn, phí thuê bao) | Claude Code viết crawler thu dữ liệu công khai (giá, lượt bán hiển thị, review đối thủ) + Claude API phân tích | Giữ Metric khi cần số liệu lịch sử dài và quy mô toàn sàn — crawler tự xây dễ bị chặn, tốn công bảo trì; dùng crawler cho theo dõi sâu 10–20 đối thủ trực tiếp |
| **Casso / SePay** (đối soát tiền về, phí tháng) | Claude Code xử lý file sao kê/email báo có + tự khớp đơn | Giữ Casso/SePay giai đoạn đầu: webhook realtime ổn định đáng tiền; tự xây khi ngân hàng mở API trực tiếp cho doanh nghiệp (một số ngân hàng đã có) |
| **Canva / CapCut** (phí bản Pro) | Claude Code sinh hình ảnh bài đăng hàng loạt từ template HTML → PNG (giá, khuyến mãi, quote review) | Giữ CapCut cho video — dựng video vẫn cần tay người/công cụ chuyên; hình tĩnh số lượng lớn thì tự động hóa được |

## 3. KHÔNG NÊN THAY — pháp lý, vật lý, hoặc nền tảng độc quyền

| Dịch vụ | Vì sao không thay bằng Claude Code |
|---|---|
| **Hóa đơn điện tử (meInvoice/SInvoice)** | Nhà cung cấp HĐĐT phải được Tổng cục Thuế chấp thuận — không tự xây được theo luật |
| **Phần mềm kế toán (MISA) + dịch vụ kế toán** | Chuẩn mực kế toán, kê khai thuế, chữ ký người chịu trách nhiệm — rủi ro pháp lý, chi phí thuê rẻ |
| **3PL, vận chuyển** | Kho bãi, xe, người giao — tài sản vật lý |
| **Zalo OA / ZNS, Meta, TikTok, sàn TMĐT** | Là kênh độc quyền nền tảng, chỉ có thể tích hợp qua API của họ, không thay thế |
| **Lab kiểm nghiệm, luật sư, OEM** | Giấy phép, con dấu, trách nhiệm chuyên môn |

---

## 4. KIẾN TRÚC SAU KHI RÀ — "XƯƠNG SỐNG TỰ XÂY"

Trục tự động hóa đổi từ *"n8n/Make + Claude API"* thành:

```
  KHO MÃ NGUỒN (repo Git này)
  ├── automations/      ← các script luồng: đơn hàng, đối soát, PO, báo cáo sáng
  ├── chatbot/          ← connector Zalo OA / Messenger ↔ Claude API
  ├── website/          ← landing page + trang sản phẩm (host miễn phí)
  ├── bot-duyet/        ← bot Telegram hàng đợi duyệt ✅/❌
  ├── tri-thuc/         ← SOP, quy tắc tuân thủ, brief SP (nguồn sự thật cho mọi AI)
  └── ke-hoach/         ← bộ tài liệu chiến lược (đã có)
```

- **Claude Code vừa là người xây vừa là người bảo trì**: lỗi luồng nào → mở phiên Claude Code sửa ngay; cần luồng mới → mô tả bằng tiếng Việt, Claude Code viết và triển khai.
- n8n tự host (miễn phí) vẫn là lựa chọn giữ lại nếu muốn **nhìn luồng bằng sơ đồ** thay vì đọc code — chọn 1 trong 2, đừng chạy song song cả hai.
- Chi phí phần mềm cố định hằng tháng sau khi rà: chỉ còn **OMS thuê (giai đoạn đầu) + HĐĐT + kế toán + Casso + 1 VPS nhỏ** — phần còn lại là code của chính công ty, tài sản tích lũy chứ không phải phí thuê mất đi.

## 5. THỨ TỰ TRIỂN KHAI PHẦN TỰ XÂY (bám lịch 12 tuần)

1. **Tuần 2–3:** website/landing + repo tri thức (thay Notion) — nền có ngay.
2. **Tuần 3–4:** chatbot connector + bot Telegram hàng đợi duyệt — hai món dùng suốt đời công ty.
3. **Tuần 4–5:** script báo cáo sáng + các luồng tự động hóa đơn hàng (thay Make/Zapier ngay từ đầu, không cần chuyển đổi sau).
4. **Tuần 5–6:** khớp tiền-đơn (đọc từ Casso webhook), luồng PO nháp.
5. **Sau launch, khi >100–200 đơn/ngày:** cân nhắc tự xây OMS/CRM thay Nhanh.vn/Sapo.
