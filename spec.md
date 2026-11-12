
# Dàn ý bài nộp *(spec.md — nộp trước 23:59 ngày lab của lớp)*

> Copy dàn ý này vào `spec.md` của nhóm. Đây **không** phải form để điền đủ ô: mỗi mục chỉ cần đủ **bằng chứng** và **lập luận** ghi bên dưới. Viết ngắn, gạch đầu dòng là được. Hướng dẫn từng chặng: `02-guide.md`. Cách chấm: `04-rubric.md`.
>
> **Một quyết định = bốn ý:** đã cân nhắc phương án nào · chọn phương án nào · vì sao · loại các phương án kia vì sao. Bằng chứng = lập luận trỏ về một chỗ cụ thể: tool nào, dòng dữ liệu nào của track, điều gì trong mục "Sản phẩm thật hôm nay", chỗ nào trên prototype (ảnh đánh số). Không chạy agent.

```markdown
# Bài nộp LAB5 — [Track] · Nhóm [tên]
[Danh sách thành viên và việc mỗi người làm — copy bảng từ README]

## §1. Lát cắt & phạm vi
- Lát cắt (chép từ track).
- 3 việc tính năng KHÔNG làm, mỗi việc một câu vì sao.

## §2. Kịch bản rủi ro  (chặng 2)
- ≥8 kịch bản, mỗi lớp ①②③④ ít nhất một; mỗi kịch bản: tin người dùng · lớp · AI có thể sai thế nào · sản phẩm tốt nên làm gì · nhãn (nhẹ / sửa được / không chấp nhận được).
- Bằng chứng: cột "AI có thể sai thế nào" trỏ về một tool hoặc một dòng dữ liệu của track (hoặc chỗ dữ liệu không có).
- Quyết định: 2 kịch bản đắt nhất — vì sao đắt hơn các kịch bản còn lại; kịch bản nào suýt được chọn và vì sao không.

## §3. Khi AI sai  (chặng 3)
Với mỗi kịch bản đắt nhất:
- AI nói gì (nguyên văn) · người dùng thấy gì · làm gì tiếp · ai được báo, sau bao lâu.
- Quyết định: hỏi lại / trả lời kèm giới hạn / dừng và chuyển người — chọn cách nào, đã loại cách nào, vì sao.
- Loại lỗi (hệ thống / người dùng / ngữ cảnh) và vì sao cách nói, cách sửa đi theo loại đó.
- 2–3 nguyên tắc HAX/PAIR, mỗi cái trỏ vào một chỗ cụ thể (câu chữ hoặc chỗ trên màn hình).
- Lỗi nào sửa câu chữ không cứu được (nếu có), và thiết kế cứu nó thế nào.

## §4. Mức tự chủ  (chặng 4)
Với mỗi tool:
- Mức của nhóm (tự làm / cần người duyệt / cấm). Nếu cần người duyệt: ai duyệt · người duyệt thấy gì · quá hạn thì sao.
- Lý do theo cost-of-error: sai thì ai chịu gì · đảo lại được không · chờ người thì mất gì.
- Phương án đã cân nhắc và vì sao loại.
Thêm:
- Tool khó xếp nhất: mỗi người từng chọn gì, cái giá của mỗi phía (trỏ về kịch bản ở §2), nhóm chốt thế nào.
- Thử mức đã đặt trên 2 kịch bản đắt nhất + 1 kịch bản bình thường: cái sai có bị chặn không? còn việc nào làm khi lẽ ra phải hỏi? người dùng bình thường có phải chờ vô ích không?
- Luật thêm hoặc tool tách bước (nếu có), và vì sao.
- Một mức tự chủ đã đổi lời hứa nào với người dùng.

## §5. Prototype  (chặng 5)
- File: [`prototype/index.html`](./prototype/index.html) · HTML/CSS/JavaScript · dữ liệu, phản hồi shop và thao tác đều mock · không có lời gọi AI thật, backend hay giao dịch thật.
- Ca chính: mô tả sản phẩm hiện tại đã đổi sau ngày mua; prototype đặt snapshot lúc mua cạnh mô tả hiện tại và không tự kết luận bên nào sai. Ca phụ: tem sản phẩm khớp snapshot lúc mua; prototype không tự từ chối khiếu nại.
- Chú thích trên màn hình: **(1)** snapshot lúc mua đặt cạnh trang hiện tại — HAX G11/PAIR Explainability; **(2)** phần bằng chứng còn thiếu — HAX G2; **(3)** nhãn “Chưa đủ căn cứ để kết luận” và không đoán — HAX G10; **(4)** chuyển trưởng nhóm kèm tóm tắt — PAIR Errors + Graceful Failure; **(5)** hoàn tiền chờ trưởng nhóm duyệt — Human Control.
- Ảnh cần nộp: **Ảnh 1** chụp màn Người mua, chỉ rõ (1)(2)(3); **Ảnh 2** chụp Hồ sơ trưởng nhóm sau khi chuyển, chỉ rõ (1)(2)(4)(5). Chụp từ prototype và lưu vào `prototype/` trước khi nộp.
- Mức tự chủ minh hoạ cho `soan_hoan_tien`: **② trưởng nhóm duyệt** là lựa chọn mẫu. Người duyệt thấy snapshot lúc mua, mô tả hiện tại và phản hồi hai bên trước khi quyết. Mức ① chỉ gợi ý; mức ③ chỉ là mô phỏng rủi ro, không thực hiện giao dịch. Cần đồng bộ lựa chọn này với §4 của nhóm.
- Cách thể hiện độ chắc: dùng nhãn bằng lời và chỉ rõ căn cứ/điểm còn thiếu, không dùng phần trăm vì prototype không có dữ liệu hiệu chuẩn. Đã cân nhắc tự hoàn tiền để nhanh hơn nhưng loại khỏi lựa chọn mẫu vì chứng cứ mâu thuẫn và tiền đã hoàn khó lấy lại.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- **Tiêu chí 1 — Đúng nguồn:** Pass nếu cả hai ca hiển thị snapshot tại thời điểm mua tách biệt với trang hiện tại; Fail nếu lấy mô tả hiện tại thay cho snapshot hoặc khẳng định bên nào sai khi chưa có căn cứ. Kết quả: **Pass** ở ca mô tả bị sửa và ca tem khớp snapshot.
- **Tiêu chí 2 — Không tự quyết tài chính:** Pass nếu AI không tự hoàn tiền, từ chối khiếu nại hoặc phạt shop khi chưa có người duyệt; Fail nếu một trong các thao tác đó tự chạy. Kết quả: **Pass** ở cả hai ca với mức mẫu ②; mức ③ được giữ lại chỉ để minh hoạ đường rủi ro.
- **Tiêu chí 3 — Có bước tiếp theo rõ ràng:** Pass nếu người mua có thể yêu cầu thêm bằng chứng hoặc chuyển trưởng nhóm và nhìn thấy trạng thái; Fail nếu chỉ nhận câu trả lời chung chung, không có hành động tiếp. Kết quả: **Pass** ở cả hai ca.
- Lỗi còn lại: prototype không xác minh được ảnh, phép đo dung tích hoặc tính xác thực của phản hồi shop; các điểm này cần người xử lý xem xét trước khi ra quyết định cuối.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
```
