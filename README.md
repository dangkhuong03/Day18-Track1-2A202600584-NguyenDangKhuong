# TripPilot Hà Giang — AI Travel Planner
### Human-Centered AI Design Prototype — Day 18, Track 1

**Học viên:** Nguyễn Thành Đạt — MãHV: 2A202600944; Nguyễn Đăng Khương — MãHV: 2A202600584
**Khoá:** VinUni AI20k · Batch 02

---

## 🔗 Link Prototype

**[Xem prototype tại đây](https://dangkhuong03.github.io/Day18-Track1-2A202600584-NguyenDangKhuong/trippilot-ha-giang-prototype.html)**

Chạy trực tiếp trên trình duyệt, không cần cài đặt. Dùng phím mũi tên ← → hoặc nút "Trở lại / Tiếp theo" để chuyển slide.

---

## 1. Bối cảnh & Lát cắt tính năng

**Hướng đã chọn:** AI Travel Planner

**Lát cắt:** AI hỗ trợ lập và điều chỉnh lịch trình chuyến đi Hà Giang (3 ngày 2 đêm) — không xây dựng toàn bộ ứng dụng du lịch, không tích hợp đặt phòng/thanh toán thật.

**Người dùng:** Khách du lịch lần đầu đến Hà Giang, chưa biết AI hỗ trợ được gì, cần lập kế hoạch cho cung đường đèo núi có độ rủi ro cao về thời gian và an toàn di chuyển.

---

## 2. Sơ đồ Luồng Trải nghiệm (Flow Map)

Nằm tại **Slide 2** trong cùng tệp prototype, thể hiện luồng:

```
Onboarding → Ask trước khi lập kế hoạch → Khởi tạo lịch trình →
Giải thích đề xuất → Phục hồi lỗi quá tải → Hành động tự chủ (Act) →
Xử lý dữ liệu không chắc chắn → Biên giới hành động (Act/Ask/Don't Act) →
Ma trận Feedback 2×2
```

---

## 3. Danh sách Kịch bản (5 kịch bản + Onboarding)

| Slide | Kịch bản | Loại |
|---|---|---|
| 3 | Onboarding lần đầu sử dụng | Bắt buộc |
| 4 | Hỏi 3 câu trước khi lập kế hoạch (Ask) | Trong tương tác |
| 5 | Explainability — giải thích & tái cấu hình trọng số xếp hạng homestay | Trong tương tác · Explainability |
| 6 | Lịch trình quá tải — phát hiện lỗi và khôi phục có Undo | Sai sót & Khôi phục |
| 7 | Hành động tự chủ rủi ro thấp (Pure Act) — AI tự chèn buffer thời gian, không hỏi trước | Agency (Act) |
| 8 | Dữ liệu lỗi thời — cảnh báo độ tin cậy thấp, đề xuất phương án thay thế | Sai sót & Khôi phục · Explainability |
| 9 | Biên giới Act / Ask / Don't Act trong việc đặt phòng | Agency |

---

## 4. Mức độ tự chủ: Act / Ask / Don't Act

- **Act:** AI tự chèn thời gian đệm an toàn vào lịch trình (Slide 7) và tự đóng gói bản tóm tắt đặt phòng (Slide 9) — rủi ro thấp, dễ phát hiện, dễ hoàn tác.
- **Ask:** AI hỏi 3 câu quan trọng trước khi lập kế hoạch (Slide 4); xin xác nhận trước khi mở trang nhà cung cấp (Slide 9).
- **Don't Act:** AI không tự thực hiện thanh toán hoặc xác nhận đặt phòng cuối cùng (Slide 9) — rủi ro tài chính cao, khó hoàn tác.

---

## 5. Vòng phản hồi & Khôi phục (Feedback Loop)

**Kịch bản đầy đủ — Slide 6 (Lịch trình quá tải):**
1. AI tạo lịch trình quá dày
2. Người dùng bấm "Lịch trình quá dày! Hãy giãn cách giúp tôi"
3. AI xác nhận đã hiểu vấn đề (thời gian đệm cho đường đèo)
4. AI đề xuất lịch trình mới đã giãn cách
5. Người dùng có thể Hoàn tác (Undo) hoặc Chấp nhận
6. AI nêu rõ điều gì đã thay đổi (các điểm dời sang Ngày 2)

**Ma trận Feedback 2×2 — Slide 10**, đủ 4 loại tín hiệu (User↔System × Explicit↔Implicit), kèm lưu ý: tín hiệu ngầm định (implicit) chỉ là tham số tham khảo, không phải xác nhận ý định chính thức của người dùng.

---

## 6. Explainability (Lớp bằng chứng/giải thích)

- **Slide 5:** Hiển thị trọng số xếp hạng homestay (Tiện đường 45% • Giá 30% • View 25%), cho phép người dùng đổi ưu tiên và xem lại kết quả thay đổi theo thời gian thực.
- **Slide 8:** Hiển thị nhãn "Mức tin cậy: Thấp" và "Dữ liệu cập nhật 8 tháng trước" cho thông tin quán ăn, kèm cảnh báo trước khi người dùng tin dùng.

---

## 7. Design Rationale

Mỗi slide từ 3 đến 9 có thẻ **Cơ sở Thiết kế (Design Rationale)** đặt ngay cạnh flow, trả lời: AI biết gì / chưa biết gì, giả định nào đang dùng, rủi ro nếu sai, ai chịu ảnh hưởng, và vì sao chọn Act/Ask/Don't Act cho tình huống đó.

---

## 8. Demo Path — 5 phút

| Thời gian | Nội dung |
|---|---|
| 0:00–0:25 | Giới thiệu người dùng, bối cảnh Hà Giang, lát cắt tính năng |
| 0:25–1:05 | Onboarding và thiết lập kỳ vọng |
| 1:05–1:50 | Hỏi trước khi lập kế hoạch + lịch trình dự thảo có giả định |
| 1:50–2:25 | Explainability — đổi trọng số xếp hạng homestay |
| 2:25–3:05 | Lỗi lịch trình quá tải + khôi phục |
| 3:05–3:30 | AI hành động tự chủ (Act) — chèn buffer, có Undo |
| 3:30–4:10 | Cảnh báo dữ liệu cũ + phương án thay thế an toàn |
| 4:10–5:00 | Biên giới Act/Ask/Don't Act + ma trận feedback |

---

## 9. Công nghệ sử dụng

Một file HTML/CSS/JavaScript độc lập, không phụ thuộc thư viện ngoài, chạy trực tiếp trên trình duyệt. Dữ liệu và phản hồi AI trong prototype là dữ liệu mẫu mô phỏng (mock), không kết nối API hay hệ thống đặt phòng thật.
