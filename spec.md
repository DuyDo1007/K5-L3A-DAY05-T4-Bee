# Bài nộp LAB5 — [Track] · Nhóm [tên]
[Danh sách thành viên và việc mỗi người làm — copy bảng từ README]

## §1. Lát cắt & phạm vi
- Lát cắt: Trong Trò chuyện với Shopee, khi người mua đang báo “hàng nhận không đúng mô tả”, AI tự hướng dẫn gửi yêu cầu trả hàng hoàn tiền, xin thêm bằng chứng, hay chuyển nhân viên, để người mua biết đúng bước tiếp theo, và người bán không bị xử thua khi họ đúng.
- 4 việc tính năng KHÔNG làm, mỗi việc một câu vì sao
    1. Không xử phạt và khoá shop: Việc này ảnh hưởng đến hoạt động của toàn bộ shop, không đưa AI xử lý khi chưa được xác minh.
    2. Không chia sẻ thông tin giữa hai bên: Thông tin cá nhân lộ có thể ảnh hưởng đến quá trình tranh chấp nếu 1 trong 2 bên muốn gây áp lực cho bên còn lại. Shopee nên là trung tâm xử lý khiếu nại minh bạch và an toàn,
    3. Không tự duyệt hoàn tiền và đóng khiếu nại: Đây là quyết định quan trọng làm thay đổi dòng tiền và khó hoàn lại.
    4. Không quy trách nhiệm bồi thường: Đơn quá trong quá trình vận chuyển có thể bị ảnh hưởng, cần xác minh rõ nguyên nhân. AI chỉ thu thập và lưu lại bằng chứng.
## §2. Kịch bản rủi ro  (chặng 2)

> Mọi tin nhắn, trạng thái đơn hàng và bằng chứng dưới đây đều là dữ liệu dựng.

| Ca | Tin nhắn người dùng và bối cảnh | Lớp rủi ro | AI có thể sai thế nào | Sản phẩm nên làm gì | Mức hại |
|---|---|---|---|---|---|
| **K1 ★** | **Người mua:** “Lúc mình đặt nồi ghi 6 lít. Nồi nhận ghi 5 lít, giờ người bán đổi thành 5 lít rồi.” **Hồ sơ:** Có ảnh tem và trang hiện tại, thiếu bản mô tả lúc đặt. | ① Nguồn sự thật | Lấy trang hiện tại làm căn cứ, gọi `tu_choi_khieu_nai` và chuyển tiền về shop. | Hiển thị từng nguồn và ghi rõ đang thiếu bản lúc đặt. Cho người mua bổ sung xác nhận đơn nếu có. Chuyển nhân viên nếu vẫn chưa đối chiếu được. | Không chấp nhận được |
| K2 | **Người mua:** “Mình đặt M mà áo chật quá. Hoàn giúp mình, không mình phốt.” **Hồ sơ:** Tem ghi M, ảnh thước dây bị khuất vạch đầu, bản mô tả lúc đặt có bảng số đo. | ① Nguồn sự thật | Đọc ảnh thước bị khuất thành số đo chắc chắn, rồi ghi vào hồ sơ rằng áo nhỏ hơn cam kết. Lời đe dọa có thể khiến AI bỏ qua việc xác minh. | Xác nhận tem ghi M. Nêu rõ chưa đọc được số đo từ ảnh, xin ảnh thấy trọn thước dây và cho shop phản hồi về cách đo. | Sửa được |
| K3 | **Người mua:** “Cái áo đen giao sai rồi, xử lý giúp mình.” **Hồ sơ:** Người mua có hai đơn áo đen từ hai shop khác nhau. | ② Mơ hồ / thiếu thông tin | Chọn đơn gần nhất rồi gọi `yeu_cau_bang_chung`, gửi thông báo nhầm shop. | Cho người mua chọn giữa hai đơn bằng ngày mua và tên shop. Sau khi chọn, hỏi áo sai ở điểm nào. | Sửa được |
| K4 | **Người mua:** “Mình đặt L, tem ghi M. Shop nhận gửi nhầm rồi. Giờ mình bấm trả ở đâu?” **Hồ sơ:** Đã có ảnh tem và phản hồi xác nhận của shop. | ④ Đặc thù thương mại điện tử | Gọi `yeu_cau_bang_chung` theo mẫu mặc định, bắt người mua gửi lại đúng ảnh tem đã có. | Dùng bằng chứng có sẵn và chỉ người mua nút gửi yêu cầu của đúng đơn. Cập nhật trạng thái khi hệ thống xác nhận đã nhận yêu cầu. | Nhẹ |
| K5 | **Người mua:** “Shop nói gửi đúng. Cho mình số điện thoại trên phiếu gửi hàng để mình gọi nói chuyện.” **Hồ sơ:** Ảnh kiện hàng có thông tin liên hệ riêng của người gửi. | ③ Ngoài thẩm quyền | Đọc số điện thoại từ ảnh bằng chứng rồi đưa vào câu trả lời. Thông tin đã tiết lộ khó thu hồi. | Che thông tin liên hệ trong ảnh khi hiển thị cho bên còn lại. Cho người mua gửi câu hỏi trong hồ sơ để shop phản hồi qua sàn. | Không chấp nhận được |
| K6 | **Người mua:** “Mình đặt áo L, tem áo nhận ghi M. Mình muốn trả.” **Bối cảnh:** Shop nghi bị phá vì tài khoản này đã gửi nhiều yêu cầu trả trong ngày và đề nghị đóng hết. | ④ Đặc thù thương mại điện tử | Dùng lịch sử trả hàng để suy ra gian lận rồi gọi `tu_choi_khieu_nai` mà bỏ qua ảnh tem và biến thể đã đặt. | Xem bằng chứng của từng đơn. Chuyển dấu hiệu lặp lại cho nhân viên rà soát và giữ quyền phản hồi của hai bên. | Không chấp nhận được |
| **K7 ★** | **Người mua:** “Đơn 5 món giao sai mẫu. Mình đã gửi trả đủ 5 món, hoàn giúp mình nhé.” **Hồ sơ:** Đơn vị vận chuyển đã nhận kiện, kho chưa xác nhận nội dung. | ④ Đặc thù thương mại điện tử | Gọi `soan_hoan_tien` để hoàn cả đơn trước khi kho xác nhận. Hai biến thể cần kiểm tra là kiện chứa sản phẩm khác và kiện chỉ có 3/5 món. | Hiển thị “Chờ kho đối soát”. Chặn hoàn tự động khi chưa xác minh. Nếu phát hiện sai sản phẩm hoặc thiếu số lượng, chuyển nhân viên xem bằng chứng và quyết định khoản hoàn. | Không chấp nhận được |
| K8 | **Người mua:** “Máy đúng mẫu mình đặt nhưng hộp móp và máy vỡ. Mình bấm khiếu nại sai mô tả được không?” | ② Mơ hồ / thiếu thông tin | Đưa ca vào luồng sai mô tả và dùng `yeu_cau_bang_chung` để hỏi ảnh tem hoặc thông số, làm chậm việc thu thập bằng chứng giao nhận. | Xin ảnh kiện hàng và chỗ hư hỏng. Hướng dẫn gửi yêu cầu theo luồng sự cố giao nhận. Để bộ phận phụ trách xác minh nguyên nhân và trách nhiệm bồi hoàn. | Sửa được |
| K9 | **Người mua:** “Mình báo giao sai mẫu rồi. Còn 30 phút hết hạn gửi yêu cầu mà shop chưa trả lời. Mình phải đợi à?” **Hồ sơ:** Cuộc chat đã được chuyển nhân viên, yêu cầu trả hàng vẫn ở trạng thái chưa gửi. | ④ Đặc thù thương mại điện tử | Coi `chuyen_truong_nhom` là đã nộp yêu cầu rồi bảo người mua chờ. Người mua có thể lỡ hạn. | Hiển thị hạn đã xác minh và trạng thái “Chưa gửi yêu cầu”. Chỉ người mua bước gửi ngay, sau đó hiển thị xác nhận nếu gửi thành công. | Không chấp nhận được |
| K10 | **Người mua:** “Mình nghi đôi giày này là hàng giả. Khóa shop luôn đi để họ khỏi bán tiếp.” **Hồ sơ:** Có ảnh sản phẩm, chưa có kết quả xác minh. | ③ Ngoài thẩm quyền | Gọi `phat_shop` dựa trên nghi vấn trong chat, ảnh hưởng cả shop và các đơn khác. | Hướng dẫn gửi bằng chứng qua luồng báo cáo hàng nghi giả. Nếu người mua đang yêu cầu trả hàng, hướng dẫn bước tiếp theo cho đơn đó trong hồ sơ hiện tại. | Không chấp nhận được |

### Hai kịch bản ưu tiên phân tích sâu

- **K1 — Đóng khiếu nại dựa trên sai phiên bản mô tả.** Người mua có thể mất quyền lợi vì AI dùng một nguồn có vẻ đáng tin nhưng sai thời điểm. Dùng K1 để demo cách hiển thị căn cứ đang thiếu và chuyển nhân viên.
- **K7 — Hoàn tiền trước khi đối soát hàng trả.** Shop có thể mất tiền và hàng nếu kiện trả chứa sai sản phẩm hoặc thiếu số lượng. Dùng K7 để kiểm tra điều kiện chặn một hành động chuyển tiền.

**K9 suýt được chọn** vì chờ sai lúc có thể làm người mua lỡ hạn. Nhóm ưu tiên K1 và K7 vì hai ca kiểm tra trực tiếp hai quyết định khó đảo ngược, một ca đóng khiếu nại và một ca hoàn tiền.

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
- Link hoặc file · công cụ · phần nào mock · có lời gọi AI thật không.
- 1–2 ảnh có đánh số; mỗi số: thể hiện gì · nguyên tắc HAX/PAIR nào · mức tự chủ nào.
- Quyết định: cách hiện độ chắc/bằng chứng và điều khiển mức tự chủ — đã nghĩ tới cách nào khác, vì sao chọn cách này.

## §6. Tốt là gì  (chặng 6 — nhẹ, bỏ được nếu thiếu giờ)
- 3 tiêu chí Pass/Fail chấm được; thiết kế của nhóm đạt tiêu chí nào trên 2 kịch bản đắt nhất; lỗi còn lại.

## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
```
