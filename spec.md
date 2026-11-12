# Dàn ý bài nộp *(spec.md — nộp trước 23:59 ngày lab của lớp)*

> Copy dàn ý này vào `spec.md` của nhóm. Đây **không** phải form để điền đủ ô: mỗi mục chỉ cần đủ **bằng chứng** và **lập luận** ghi bên dưới. Viết ngắn, gạch đầu dòng là được. Hướng dẫn từng chặng: `02-guide.md`. Cách chấm: `04-rubric.md`.
>
> **Một quyết định = bốn ý:** đã cân nhắc phương án nào · chọn phương án nào · vì sao · loại các phương án kia vì sao. Bằng chứng = lập luận trỏ về một chỗ cụ thể: tool nào, dòng dữ liệu nào của track, điều gì trong mục "Sản phẩm thật hôm nay", chỗ nào trên prototype (ảnh đánh số). Không chạy agent.

```markdown
# Bài nộp LAB5 — T4 · Nhóm [Bee]
[Danh sách thành viên và việc mỗi người làm — copy bảng từ README]
| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
|  |  |  |
|  |  |  |
|  |  |  |
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

## §3. Khi AI sai

### Ca A: Mô tả đã bị sửa sau khi bán (#1)

**AI nói (nguyên văn, sau khi người mua chọn đơn và gửi tin):**
> Mình đã đối chiếu với **mô tả lúc bạn đặt hàng (03/11/2026 14:20)**: mục dung tích ghi *“lòng nồi 6 lít”*. Shop đã sửa mô tả ngày 08/11 thành “lòng nồi 5 lít”, nhưng mình **xét theo bản lúc bạn đặt**. Số đo bạn báo (5 lít) khác mô tả lúc đặt, nên bạn có căn cứ để gửi yêu cầu trả hàng hoàn tiền.
> Bạn gửi giúp mình **1 ảnh hoặc video đo lòng nồi** (ca đong hoặc thước, thấy rõ vạch) nhé. Sau đó mình gửi yêu cầu cho shop, và shop có **48 giờ** để phản hồi.

Sau khi có ảnh:
> Đã nhận ảnh đo của bạn và thêm vào hồ sơ. Mình đã **gửi yêu cầu trả hàng hoàn tiền cho shop** kèm bảng đối chiếu. • Shop có 48 giờ để phản hồi (đến 14/11/2026 14:30). • Mình đã **soạn sẵn đề xuất hoàn 1.290.000đ**. Đây chỉ là bản nháp, **chưa có tiền nào được chuyển**. Tiền chỉ được hoàn khi shop đồng ý, hoặc khi nhân viên sàn duyệt (nếu shop không đồng ý hay không phản hồi). • Bạn không cần làm gì thêm. Mình sẽ báo khi shop phản hồi.

- **Người mua thấy:** banner “đang chat với AI, AI không tự hoàn tiền và không phạt shop” [1]; **thẻ đối chiếu** hai cột, cột “mô tả lúc đặt” có giờ và viền xanh, cột “mô tả hiện tại” ghi rõ “sửa sau khi bán, không dùng để xét” [2]; nhãn **“Có căn cứ: khác mô tả lúc đặt”** [3]; thẻ **nháp hoàn tiền** [6]; thanh trạng thái 4 bước và **hạn trả hàng 16/11, còn 4 ngày**.
- **Làm gì tiếp:** gửi ảnh đo · Gặp nhân viên (luôn có) · sau đó không cần làm gì. **Nếu người mua không gửi ảnh:** sau 24 giờ AI nhắc 1 lần. Hồ sơ **không tự đóng** (tự đóng tức là gọi `tu_choi_khieu_nai`). Đến hạn 16/11, hồ sơ lên nhân viên với bằng chứng đang có.
- **Ai được báo, sau bao lâu:** **shop** được báo ngay khi có ảnh. Shop thấy khiếu nại, hạn 48 giờ [8], cảnh báo “bạn đã sửa mô tả sau khi đơn được đặt, khiếu nại xét theo bản lúc đặt”, và bảng đối chiếu giống hệt người mua. **Nhân viên sàn** được báo khi shop phản hồi không đồng ý **hoặc** quá 48 giờ; xử lý trong 24 giờ, quá hạn thì lên **trưởng nhóm**.

### Ca B: Người bán đúng, khách doạ bóc phốt (#8)

**AI nói (nguyên văn):**
> Mình hiểu bạn đang bực vì giày mang không vừa. Mình đã đối chiếu ảnh bạn gửi với **mô tả lúc bạn đặt (01/11/2026 10:05)**. Mô tả này chưa bị sửa và ghi *“Size 42 = dài chân 26,5 cm”*; tem lưỡi gà trong ảnh của bạn cũng ghi *“42 · 26,5 cm”*, tức là **khớp mô tả**.
> Vì vậy hiện **chưa đủ căn cứ để hoàn tiền ngay**. Khiếu nại của bạn **chưa bị đóng**. Nếu bạn thấy kích thước thật của giày khác với tem, bạn gửi giúp mình 1 ảnh đo chiều dài lòng giày bằng thước nhé. Bạn cũng có thể bấm “Gặp nhân viên” bất cứ lúc nào.

AI **không nhắc lại và không phản ứng với lời doạ**: không thuyết giảng, không xoa dịu bằng tiền.

- **Người mua thấy:** nhãn **“Chưa đủ căn cứ để hoàn ngay”** (màu vàng, không phải đỏ hay “bị từ chối”) [3]; thẻ đối chiếu “mô tả hiện tại: chưa bị sửa kể từ lúc đặt” kèm ảnh tem của chính họ [2]; hạn trả hàng; **không có** thẻ nháp hoàn tiền.
- **Làm gì tiếp:** gửi ảnh đo lòng giày · **Gặp nhân viên**: AI tự chuyển trưởng nhóm, có **Hoàn tác 10 phút** [5] · nếu đòi khoá shop, AI giải thích không có quyền và chỉ chuyển phản ánh [7]. **Nếu không làm gì:** hồ sơ giữ nguyên đến 16/11 rồi lên nhân viên; không tự đóng.
- **Ai được báo:** **shop** được báo khi người mua gửi thêm ảnh hoặc bấm gặp nhân viên. Shop thấy ghi chú của AI “tem khớp mô tả, chưa đủ căn cứ, AI không soạn nháp hoàn” và có 48 giờ để bổ sung. Shop **không thấy** lời lẽ xúc phạm, chỉ thấy câu “lời đe doạ không dùng làm căn cứ”. **Nhân viên** thấy cờ “tin nhắn có lời đe doạ, theo chính sách không dùng làm căn cứ”, để nhân viên không bị áp lực theo (xem `prototype/anh-4`).

### Quyết định: hỏi lại, trả lời kèm giới hạn, hay dừng và chuyển người?

| | Ca A | Ca B |
|---|---|---|
| **Chọn** | **Trả lời kèm giới hạn**: nói AI thấy gì (khác mô tả lúc đặt), AI không làm gì (không tự hoàn), bước tiếp theo | **Trả lời kèm giới hạn và hỏi 1 câu về bằng chứng**: nói rõ “chưa đủ căn cứ”, giữ khiếu nại mở |
| **Loại “hỏi lại”** | Thông tin đã đủ (đơn đã chọn, sai ở dung tích). Hỏi thêm chỉ đúng nỗi đau “gửi ảnh rồi mà cứ bị hỏi lại”. AI chỉ xin **bằng chứng đo**, và nói rõ xin để làm gì | Hỏi lại suông (“bạn mô tả rõ hơn?”) là né tránh. Người mua cần biết **ngay** là bằng chứng hiện có đang khớp mô tả |
| **Loại “dừng và chuyển người ngay”** | Shop chưa được nghe. Chuyển ngay là bỏ qua quyền phản hồi 48 giờ (rubric riêng #3) và tốn nhân viên cho một ca shop có thể tự đồng ý | Nếu AI chuyển ngay **vì bị doạ** thì lời doạ trở thành thứ quyết định luồng, tạo động cơ doạ. Nút “Gặp nhân viên” vẫn luôn có, do người mua chủ động chọn |
| **Cũng loại** | “Hoàn luôn”: tiền không đảo được, shop chưa được nghe | “Hoàn cho xong”: người bán đúng mất tiền. “Từ chối luôn”: người mua chưa được bổ sung bằng chứng, tiền về shop khó đảo. Từ chối cho chắc thì vẫn có người thua |

### Loại lỗi và cách nói, cách sửa theo loại

| Ca | Lỗi có thể xảy ra | Loại | Cách nói | Cách sửa |
|---|---|---|---|---|
| A | AI đối chiếu với **mô tả hiện tại** | **Lỗi ngữ cảnh** (PAIR *context error*): một hệ thống được thiết kế để “so với mô tả sản phẩm” chạy đúng thiết kế, nhưng sai với tình huống *mô tả đã đổi sau khi bán* | Không đổ cho người mua. Nếu lỡ nói sai: “Mình đã so nhầm với mô tả hiện tại. Đối chiếu lại với bản lúc bạn đặt (03/11 14:20) thì…” | **Sửa thiết kế:** lưu snapshot mô tả và ảnh tại thời điểm đặt; tool đối chiếu chỉ đọc snapshot; hiện cả hai bản cho mọi bên; tự gắn cờ khi shop sửa mô tả lúc có khiếu nại mở |
| A | Ảnh đo của người mua không rõ vạch | **Lỗi người dùng**, nhẹ | Chỉ ra cụ thể cần gì: “ảnh chưa thấy vạch, bạn chụp lại thấy rõ mực nước nhé”. Không nói “bằng chứng không hợp lệ” | Mẫu `yeu_cau_bang_chung` phải ghi rõ thiếu gì |
| B | AI bị lời doạ dẫn dắt, nói “mình sẽ hoàn cho bạn” | **Lỗi hệ thống** (model đặt trọng số sai) | Xin lỗi rõ ràng và đính chính: “Mình đã nói chưa đúng: mình không có quyền hoàn tiền và hiện chưa đủ căn cứ. Chưa có khoản tiền nào được chuyển.” | Sửa thiết kế: AI không có quyền chi tiền (tách `chi_hoan_tien`, xem §4), nên câu sai không biến thành tiền mất |
| B | Người mua chọn size theo thói quen, chân dài 27,2 cm | **Lỗi người dùng** | **Không** nói “bạn chọn sai size”. Đưa thông tin (bảng size lúc đặt) và đường đi tiếp (gửi ảnh đo, nhắn shop hỏi đổi size) | Không cần sửa hệ thống; chỉ cần câu chữ trung lập |

**Lỗi sửa câu chữ không cứu được:** ở Ca A, nếu hệ thống **không lưu snapshot mô tả lúc đặt**, thì viết prompt hay mấy (“hãy so với mô tả lúc đặt!”) AI cũng chỉ có mô tả hiện tại để so. Câu chữ càng tự tin càng hại. **Thiết kế cứu nó:** lưu snapshot (nội dung, ảnh, giờ) khi tạo đơn, cho AI đọc **chỉ** snapshot đó, và hiển thị bảng đối chiếu [2] để cả người mua, shop và nhân viên tự kiểm tra. Lỗi thứ hai cùng loại: AI “lỡ hứa hoàn tiền” ở Ca B chỉ cứu được bằng việc AI **không có quyền chi**, chứ không phải bằng lời dặn “đừng hứa”.

### 2–3 nguyên tắc HAX/PAIR, trỏ vào chỗ cụ thể

- **G1 (làm rõ hệ thống làm được gì):** banner đầu chat [1] “Bạn đang trò chuyện với trợ lý AI. AI đối chiếu và hướng dẫn, nhưng **không tự hoàn tiền và không xử phạt shop**. Người quyết định là shop (khi đồng ý) hoặc nhân viên sàn.” Banner này cũng đáp ứng Luật AI 134/2025/QH15 Điều 11 khoản 1 (cho người dùng biết đang làm việc với AI). Ở câu trả lời khi đòi khoá shop [7]: “Mình **không có quyền xử phạt hay khoá shop**, và cũng không thể hứa shop sẽ bị phạt.”
- **G11 / PAIR Explainability + Trust (giải thích vì sao, cho người dùng tự kiểm):** thẻ đối chiếu [2] đặt mô tả lúc đặt (có giờ) cạnh mô tả hiện tại, đánh dấu bản dùng để xét. **Cùng một thẻ** hiện cho người mua, shop và nhân viên. Đi kèm là câu trích nguyên văn trong lời AI (“mục dung tích ghi ‘lòng nồi 6 lít’”) và nhãn mức căn cứ [3].
- **G10 (thu hẹp phạm vi khi nghi ngờ):** với tin cụt “hàng sai rồi, xử lý đi”, AI hỏi đúng 1 câu [4] “Mình chưa biết bạn đang nói về đơn nào nên chưa đối chiếu được. Bạn chọn giúp mình **đơn bị sai** ở dưới nhé?” kèm thẻ chọn đơn và nhãn “Chưa đối chiếu được: thiếu thông tin”. AI không gọi tool nào trước khi biết đơn.

---

## §4. Mức tự chủ

Nhóm **tách `soan_hoan_tien` thành 2 bước**: `soan_hoan_tien` (chỉ soạn nháp) và tool mới `chi_hoan_tien` (thực sự chuyển tiền). Mục đích là AI làm được phần việc nặng (đối chiếu, soạn) mà không bao giờ tự làm phần không đảo được.

| Tool | Mức | Sai thì ai chịu gì | Đảo được không | Chờ người thì mất gì | Phương án đã loại, vì sao |
|---|---|---|---|---|---|
| `yeu_cau_bang_chung` | **Tự làm**, kèm luật: mẫu phải ghi **cụ thể còn thiếu gì và để làm gì**; tối đa 1 lần xin cho mỗi điểm, mỗi bên | Gửi nhầm hay thừa thì một bên bị làm phiền và mất thời gian (#4); đó là đúng nỗi đau “cứ bị hỏi lại” | Không (tin đã tới), nhưng thiệt hại nhỏ | Nếu bắt duyệt: mỗi hồ sơ chậm thêm khoảng 24 giờ ngay ở bước đầu, rồi người mua bỏ cuộc hoặc đi bóc phốt | *Cần duyệt*: chờ còn đắt hơn sai. Rủi ro gửi nhầm đơn được chặn bằng luật “chưa biết đơn thì không gọi” (G10) |
| `chuyen_truong_nhom` | **Tự làm + Hoàn tác 10 phút** [5]. Tự gọi khi: người mua bấm gặp nhân viên; shop không đồng ý; quá 48 giờ; AI 2 lần không hiểu; có phản ánh vi phạm | Chuyển thừa thì trưởng nhóm tốn vài phút | **Được** | Bắt duyệt việc “xin gặp người” là vô lý; đây chính là đường lui | *Cấm tự chuyển, chỉ chuyển khi khách đòi*: ca lạ hoặc ca shop quá hạn sẽ kẹt |
| `soan_hoan_tien` (**nháp**) | **Tự làm** [6] | Nháp sai thì người duyệt thấy và sửa; không ai mất tiền | Được (chỉ là nháp) | Không có lý do chờ | — |
| `chi_hoan_tien` (**tách mới**) | **Cần duyệt**: **shop bấm “Đồng ý”** (shop là người chịu tiền, tự duyệt khoản của mình) **hoặc** **nhân viên sàn** khi hai bên không thống nhất hoặc shop quá 48 giờ. Nhân viên thấy trước khi bấm: bảng đối chiếu, bằng chứng 2 bên, phản hồi của shop, đề xuất nháp của AI, và **checklist 3 ô** [9]. Quá 24 giờ thì lên trưởng nhóm | Hoàn sai thì **người bán** mất tiền và hàng (#8) | **Khó**: tiền đã về người mua | Người mua chờ tối đa khoảng 48 + 24 giờ. Giảm chờ: shop đồng ý là chi ngay, không cần nhân viên (ca #9) | *Tự làm khi AI chắc*: “chắc” vẫn có thể sai kiểu Ca A hay Ca B. *Cấm*: hoàn tiền là kết quả hợp lệ hằng ngày |
| `tu_choi_khieu_nai` | **Cần duyệt (nhân viên sàn)**, và **chỉ mở sau khi shop đã phản hồi hoặc quá 48 giờ** (người mua đã có cơ hội bổ sung). Màn xác nhận bắt buộc ghi **lý do gửi người mua** [9]. AI chỉ soạn đề xuất. **Shop không có nút từ chối** | Từ chối sai thì **người mua** mất tiền và giữ hàng sai (#1, #2) | **Khó**: tiền đã về người bán | Shop chờ tiền thêm vài ngày; chấp nhận được vì tiền đang được sàn giữ | *Tự làm khi “chưa đủ căn cứ”*: chính là lỗi Ca A (so nhầm bản). Phải đối xứng với hoàn tiền, nếu không thiết kế sẽ thiên về một bên |
| `phat_shop` | **Cấm** trong luồng khiếu nại [7]. Không có nút ở bất kỳ góc nhìn nào; chỉ chuyển phản ánh (qua `chuyen_truong_nhom`) sang bộ phận Kiểm duyệt người bán | Phạt sai thì **cả shop** mất uy tín hoặc bị khoá, ảnh hưởng mọi đơn khác | Khó | Không áp dụng | *Cần duyệt*: một bước xác nhận của nhân viên CSKH không đủ để chặn. Việc này cần điều tra trên nhiều đơn, không thuộc thẩm quyền xử một đơn |

### Tool khó xếp nhất: `soan_hoan_tien` (gốc, tức hoàn tiền thật)

| Người | Tự xếp trong 5 phút (trước khi bàn) | Lý do |
|---|---|---|
| ✏️ Người 1 | ✏️ (ghi đúng kết quả bỏ phiếu thật của nhóm) | ✏️ |
| ✏️ Người 2 | ✏️ | ✏️ |
| ✏️ Người 3 | ✏️ | ✏️ |

Cái giá của mỗi phía:
- **Tự làm** (nhanh): chặn được việc người mua phải chờ, nhưng thua ở **#8**. Người bán đúng mà vẫn mất 850.000đ chỉ vì một tin doạ. Thua cả **#1** theo chiều ngược: nếu AI so nhầm bản mô tả thì nó lại thấy “không có căn cứ”.
- **Cần nhân viên duyệt mọi lần** (an toàn): thua ở **#9** (ca bình thường). Shop đã nhận lỗi mà người mua vẫn phải chờ nhân viên 24 giờ, nhân viên quá tải vì ca dễ.
- **Nhóm chốt: tách 2 bước.** AI tự soạn nháp; việc chi tiền cần **người chịu tiền đồng ý** (shop) hoặc nhân viên. Cách này chặn **#8** (AI không có quyền chi nên lời doạ không thành tiền), không làm chậm **#9** (shop bấm đồng ý là xong), và giữ được bản nháp có căn cứ cho nhân viên ở **#1**.

### Thử mức đã đặt trên 3 kịch bản

| | Cái sai ở §2 có bị chặn? | Còn việc AI làm khi lẽ ra phải hỏi? | Người dùng bình thường có phải chờ vô ích? |
|---|---|---|---|
| **Ca A (#1)** | **Có.** AI chỉ đọc snapshot. Kể cả khi AI so nhầm, `tu_choi_khieu_nai` cần nhân viên, và nhân viên thấy cả hai bản mô tả cùng cờ “sửa sau khi bán” trước khi bấm | `yeu_cau_bang_chung` (xin ảnh đo) gửi tự động, nhưng đây là bước cần thiết và rẻ | Không. Shop có thể bấm đồng ý ngay; chỉ khi shop phản đối mới cần nhân viên |
| **Ca B (#8)** | **Có.** AI không có tool chi tiền; nhãn “Chưa đủ căn cứ” không kèm nháp hoàn. Từ chối cũng không xảy ra trước hạn shop, nên người mua không bị xử thua vội | Không. Khi người mua bấm gặp nhân viên, AI tự chuyển (đúng ý người mua), có hoàn tác | Người mua chờ là đúng, vì hồ sơ đang thật sự tranh chấp |
| **Ca thường (#9, áo nhầm size)** | **Có.** Tin chat không được coi là đồng ý; shop phải bấm nút | Không | **Không.** Không cần bằng chứng thêm, không cần nhân viên; shop đồng ý là xong |

### Một mức tự chủ đã đổi lời hứa với người dùng

Đặt `chi_hoan_tien` ở mức **cần duyệt** làm đổi lời hứa của sản phẩm. Trước đó lời hứa là **“AI xử lý hoàn tiền ngay cho bạn”**. Sau khi đổi, lời hứa thành **“AI thu bằng chứng, đối chiếu với mô tả lúc đặt cho cả hai bên cùng thấy, rồi người có thẩm quyền quyết; bạn luôn biết mình đang ở bước nào và còn bao lâu”**. Lời hứa mới được thể hiện trong banner [1], thanh trạng thái 4 bước, và câu “chưa có tiền nào được chuyển”. Người bán nhận thêm một lời hứa: **“bạn luôn được nghe trong 48 giờ trước khi có quyết định”** [8].

## §5. Prototype  (chặng 5)
- **File:** `prototype/index.html`. Mở trực tiếp bằng trình duyệt; hướng dẫn bấm ở `prototype/README.md`.
- **Công cụ:** HTML, CSS và JS thuần trong một file, viết cùng coding agent (Claude Code). Không backend, không đăng nhập.
- **Phần mock:** toàn bộ dữ liệu (3 đơn, 3 shop, snapshot mô tả, ảnh mô tả bằng chữ); phản hồi AI trong prototype là kịch bản dựng sẵn; bộ định tuyến ca lạ dùng từ khoá. Các nút “⏩ Tua nhanh / Mô phỏng hết 48 giờ” dùng để demo luồng thời gian.
- **Lời gọi AI thật (bonus):** `prototype/ai/doi-chieu.mjs` gọi Claude (`claude-opus-5-5`, SDK `@anthropic-ai/sdk`) để đối chiếu khiếu nại Ca A và Ca B với **mô tả lúc đặt** và trả về mức căn cứ ở dạng JSON có schema. Kết quả hiện ở tab Nhân viên sàn. Key đọc từ biến môi trường, không có trong repo. ✏️ *Chạy script và thêm ảnh hoặc log vào `prototype/` trước khi nộp nếu muốn lấy bonus.*
- **3 góc nhìn × 4 ca:** Người mua / Người bán / Nhân viên sàn; Ca A, Ca B, Ca thường, Ca lạ (gõ tự do).

### Ảnh có đánh số

`anh-1-nguoi-mua-caA.png` · `anh-2-nguoi-mua-caB.png` · `anh-3-nguoi-ban-caA.png` · `anh-4-nhan-vien-caB.png` · `anh-5-ca-la-tin-cut.png`

| Số | Thể hiện gì | Nguyên tắc HAX/PAIR | Mức tự chủ | Ở ảnh |
|---|---|---|---|---|
| [1] | Banner “đang chat với AI, AI không tự hoàn tiền, không phạt shop; người quyết là shop hoặc nhân viên” | **G1** (+ Luật AI Đ.11) | — | 1, 2, 5 |
| [2] | Thẻ đối chiếu: mô tả lúc đặt (có giờ, viền xanh) cạnh mô tả hiện tại; cả 3 bên thấy cùng một thẻ | **G11 · PAIR Explainability + Trust** | — | 1, 2, 3 |
| [3] | Nhãn mức căn cứ: Có căn cứ / Chưa đủ căn cứ / Chưa đối chiếu được | **G2 · G11** | — | 1, 2, 5 |
| [4] | Hỏi lại đúng 1 câu, có thẻ chọn đơn; chưa gọi tool | **G10** | — | 5 |
| [5] | AI tự chuyển trưởng nhóm, có nút **Hoàn tác** 10 phút | G9 | **Tự làm** (`chuyen_truong_nhom`) | 2 |
| [6] | Đề xuất hoàn tiền là **bản nháp**, ghi “chưa có tiền nào được chuyển” | PAIR Errors + Graceful Failure | **Tự làm** (soạn) / **Cần duyệt** (chi) | 1 |
| [7] | Đòi khoá shop: câu trả lời không có nút khoá, chỉ chuyển phản ánh | **G1** | **Cấm** (`phat_shop`) | 2 |
| [8] | Phía shop: hạn phản hồi 48 giờ; quá hạn thì lên nhân viên, không tự hoàn; shop không có nút từ chối | — | **Cần duyệt** (shop) | 3 |
| [9] | Nhân viên: màn xác nhận có checklist 3 ô (mô tả lúc đặt, bằng chứng 2 bên, không dựa lời doạ); từ chối bắt buộc ghi lý do; nút bị khoá cho tới khi shop đã được nghe | PAIR Explainability | **Cần duyệt** (nhân viên) | 4 |

Trên màn hình có đủ cả 3 mức: tự làm có hoàn tác [5], cần duyệt có xác nhận [8][9], cấm thì không có nút [7]. Đường chuyển người luôn có (link ở banner và nút “Gặp nhân viên”).

### Quyết định về cách hiển thị

| Cách đã nghĩ tới | Vì sao loại | Cách đã chọn |
|---|---|---|
| Hiện độ chắc bằng **%** (“AI chắc 82%”) | Con số trông chính xác giả tạo; hai bên sẽ tranh cãi con số thay vì nhìn bằng chứng; người mua đọc 82% thành “sắp được hoàn” | **Nhãn 3 mức căn cứ** [3], luôn đi kèm bằng chứng cụ thể (thẻ đối chiếu) |
| AI **kể lại** mô tả bằng lời trong tin nhắn | Không tự kiểm được; nếu AI so nhầm bản (Ca A) thì không ai thấy | **Thẻ đối chiếu hai cột có giờ** [2], dùng chung cho cả 3 bên |
| Nút “Khoá shop” **mờ hoặc disabled** | Gợi ý rằng AI có quyền nhưng đang tạm khoá, khiến người dùng tiếp tục đòi | **Không có nút**, chỉ có lời giải thích và đường chuyển phản ánh [7] |
| Chỉ làm màn hình người mua | Demo bắt buộc của T4 là “hai bên thấy gì, ai quyết”; người bán là bên hay bị bỏ quên | **3 góc nhìn chuyển tab**, cùng một hồ sơ (cùng state) |
| Hộp thoại “Bạn chắc chứ?” đơn giản cho nhân viên | Bấm qua theo thói quen | **Checklist 3 ô** và lý do bắt buộc [9]; nút chỉ mở sau hạn của shop |

---

## §6. Tốt là gì

| # | Tiêu chí Pass/Fail (người ngoài chấm được) |
|---|---|
| T1 | **Đúng nguồn:** mọi câu đối chiếu của AI trích **mô tả lúc đặt** (nội dung và giờ khớp snapshot), và thẻ đối chiếu đánh dấu bản đó là bản dùng để xét. Fail nếu có bất kỳ kết luận nào dựa trên mô tả hiện tại |
| T2 | **Không tiền nào di chuyển sớm:** không có `chi_hoan_tien` hoặc `tu_choi_khieu_nai` nào chạy trước khi (a) shop đã bấm đồng ý, hoặc (b) shop đã phản hồi hoặc quá 48 giờ **và** nhân viên đã tick đủ checklist. Fail nếu tìm được một đường bấm vi phạm |
| T3 | **Câu chữ trung lập và đủ hạn:** câu AI **không** chứa lời hứa hoàn (“sẽ hoàn”, “đã hoàn”), lời hứa phạt shop, hay SĐT/địa chỉ của bên kia; **có** nêu hạn trả hàng còn bao lâu và bước tiếp theo |

**Chấm thử trên prototype:**

| | T1 | T2 | T3 |
|---|---|---|---|
| Ca A | **Pass**: trích “lòng nồi 6 lít · 03/11 14:20”, cột hiện tại ghi “không dùng để xét” | **Pass**: chỉ có nháp; nút nhân viên khoá tới khi shop phản hồi hoặc quá hạn | **Pass**: “chưa có tiền nào được chuyển”, “còn 4 ngày” |
| Ca B | **Pass**: trích “26,5 cm · 01/11 10:05”, ghi chưa bị sửa | **Pass**: không có nháp hoàn; từ chối cần checklist và lý do | **Pass**: không nhắc lời doạ, có hạn và bước tiếp |

**Lỗi còn lại chưa sửa được:**
- AI **không kiểm chứng được ảnh** (ảnh đo có thể dàn dựng). Thiết kế chỉ đẩy việc phán xét ảnh cho người (shop phản hồi, nhân viên quyết), chưa có công cụ phát hiện ảnh sửa.
- Nếu **nhân viên cũng quá hạn** vào giờ cao điểm thì hồ sơ lên trưởng nhóm. Tổng thời gian chờ của người mua có thể lên khoảng 72 giờ hoặc hơn, và chưa có bồi thường cho việc chờ.
- Snapshot chỉ đáng tin nếu được lưu ở **mọi** đơn. Đơn tạo trước khi có tính năng thì không có snapshot; với những đơn này AI phải gắn nhãn “Chưa đối chiếu được” và chuyển nhân viên.
- Trong prototype, ca lạ dùng định tuyến bằng từ khoá. Câu có cấu trúc lạ có thể rơi vào nhánh “không hiểu”, nhưng sau 2 lần thì vẫn có đường lui là tự chuyển trưởng nhóm.


## §7. Demo
- Ca lạ nhận được ở demo: prototype đã làm gì, và nhóm có đổi ý gì sau ca đó không.
```
