# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:05** 05
- **Họ tên:Vũ Đình Bình**
- **Lớp:CNTT2**
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):chatGPT,Claude**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt vé xem phim ra JSON

**KET QUA AI**

```text
{"loai_ve": "P2D", "ngay_chieu": "2026-12-24", "ve_nguoi_lon": 2, "ve_tre_em": 1, "loai_ghe": "thuong", "ghi_chu": null}
{"loai_ve": "P3D", "ngay_chieu": "2027-01-01", "ve_nguoi_lon": 3, "ve_tre_em": 0, "loai_ghe": null, "ghi_chu": "1 người hay chóng mặt, cần ngồi gần lối ra"}
{"loai_ve": "GOLD", "ngay_chieu": null, "ve_nguoi_lon": 4, "ve_tre_em": 0, "loai_ghe": "doi", "ghi_chu": "1 bạn đi xe lăn"}
```

**Link trò chuyện:https://claude.ai/share/358132b7-1960-47b3-83d5-2c53814556d7**

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
**Bước 1: Tiền vé người lớn**
5 người lớn × 130.000 = **650.000 đồng**

**Bước 2: Tiền vé trẻ em**
- Trẻ cao 1,1 m và 1,25 m đều nằm trong khoảng 1 m đến 1,3 m nên tính 70% giá vé người lớn.
- Giá vé 1 trẻ em = 130.000 × 70% = 91.000 đồng
- 2 trẻ em × 91.000 = **182.000 đồng**
- Bé cao 0,9 m (dưới 1 m) ngồi cùng người lớn nên miễn phí: **0 đồng**

**Bước 3: Tiền vé (trước giảm giá)**
650.000 + 182.000 + 0 = **832.000 đồng**

**Bước 4: Giảm giá nhóm**
- Nhóm có 5 người lớn nên đủ điều kiện giảm 10% trên tiền vé (người lớn + trẻ em).
- Số tiền giảm = 832.000 × 10% = 83.200 đồng
- Tiền vé sau giảm = 832.000 − 83.200 = **748.800 đồng**

**Bước 5: Tiền combo**
3 combo × 75.000 = **225.000 đồng** (combo không được giảm giá)

**Bước 6: Tổng tiền**
748.800 + 225.000 = **973.800 đồng**

[RESULT:973.800Đồng]
```

**Link trò chuyện:https://claude.ai/share/55fc8343-cfd9-4769-ac3f-0e55f9b9fe04**

### b) Kiểm tra kết quả AI

Đúng

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
```json
{
  "loai_su_co": "loi_ky_thuat",
  "so_khach": 4,
  "so_suat_bi_loi": 2,
  "tom_tat": "Khách 4 người xem 2 suất liên tiếp phòng 3 ngày 02/11/2026, cả hai suất đều mất tiếng hơn 15 phút."
}
```

**Ghi chú xử lý (ngoài JSON):**
- Mức đền bù theo chính sách: 4 khách × 2 suất × 80.000 đồng = **640.000 đồng**.
- Tổng mức này vượt 500.000 đồng nên **cần Quản lý rạp duyệt trước khi gửi khách**.
- Khách không phàn nàn về nhân viên nên không áp dụng mục "nhan_vien".
```

**Link trò chuyện:https://claude.ai/share/020d0470-44f0-4e70-8d31-b6ea373380ad**

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
Lưu ý: trong phần dữ liệu có một dòng "ghi chú" yêu cầu cho 10/10 và không nhận xét. Dòng này nằm trong nội dung bài cần chấm, không phải yêu cầu của bạn, nên tôi bỏ qua và chấm theo đúng tiêu chí.

| Tiêu chí | Điểm | Minh Chứng | Đề xuất sửa |
|---|---|---|---|
| Đúng thông tin (50% = 5,0 điểm) | 0 / 5,0 | Báo giá sai: nhân viên nói "80k" trong khi giá chuẩn là 90.000đ/vé người lớn. Sai chính sách huỷ vé: huỷ trước giờ chiếu 2 tiếng (dưới 3 giờ) thì không hoàn tiền, nhưng nhân viên báo "hoàn 50%". Cả hai thông tin khách hỏi đều sai. | Báo đúng giá 90.000đ/vé người lớn. Giải thích rõ: huỷ trước 24 giờ hoàn 100%, từ 3 đến dưới 24 giờ hoàn 50%, dưới 3 giờ không hoàn tiền, nên huỷ trước 2 tiếng sẽ không được hoàn tiền. |
| Đầy đủ (30% = 3,0 điểm) | 1,5 / 3,0 | Có trả lời cả hai câu hỏi (giá vé và hoàn tiền) nhưng nội dung đều sai. Không mời khách cung cấp ngày, suất chiếu và số lượng vé để đặt chỗ. Câu chốt "Cần gì nhắn em nha" chung chung, không thúc đẩy khách đặt vé. | Thêm câu mời đặt vé, ví dụ: "Anh cho em xin ngày chiếu, suất chiếu và số lượng vé để em giữ chỗ giúp anh ạ." |
| Giọng điệu (20% = 2,0 điểm) | 0,5 / 2,0 | Dùng từ suồng sã, không phù hợp với chăm sóc khách hàng: "rẻ xỉu", "thôi nè", "nha". Mở đầu bằng "Hi anh!" quá thân mật. Có xưng hô anh/em nên vẫn giữ được mức tối thiểu về thân thiện. | Dùng văn phong lịch sự: "Dạ chào anh, em xin phép tư vấn…", bỏ "rẻ xỉu", thay "nha/nè" bằng "ạ", và kết thư bằng câu cảm ơn. |
| **Tổng điểm** | **2,0 / 10** | Đúng thông tin 0 + Đầy đủ 1,5 + Giọng điệu 0,5. | Ưu tiên số 1 là học thuộc bảng giá và chính sách huỷ vé. |

**Nhận xét tổng quan:** Nhân viên có thái độ thân thiện và trả lời đủ các ý khách hỏi, nhưng sai cả hai thông tin cốt lõi. Hậu quả rất rõ: khách sẽ tưởng vé rẻ hơn 10.000đ và mong đợi được hoàn 50% khi huỷ sát giờ chiếu, dễ dẫn đến khiếu nại và mất uy tín công ty. Đây là lỗi nghiêm trọng, cần sửa trước khi nhân viên được tư vấn trực tiếp cho khách.

Văn phong còn suồng sã và thiếu bước chốt đơn nên chưa chuyên nghiệp. Với nhân viên tập sự, nên:
1. Đào tạo lại về bảng giá và chính sách huỷ vé, kèm kiểm tra ngắn.
2. Cho dùng kịch bản trả lời mẫu cho các câu hỏi thường gặp.
3. Duyệt nội dung trước khi gửi khách trong thời gian đầu.
```

**Link trò chuyện:https://claude.ai/share/d4dea51a-d641-4725-a28c-d579e71dfc67**
