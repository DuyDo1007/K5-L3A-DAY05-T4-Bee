# Bài nộp LAB5 — T4 Thương mại điện tử · Nhóm ✏️[TenNhom]

**Lớp:** L3A ✏️ · **Bàn / zone:** ✏️ · **Track:** T4 — Thương mại điện tử (trợ lý khiếu nại “hàng nhận không đúng mô tả”, tham khảo “Trò chuyện với Shopee”)

| Họ và Tên | Mã Học Viên | Việc đã làm |
|---|---|---|
| ✏️ Người 1 | ✏️ | §1 Lát cắt & phạm vi · §2 bảng 11 kịch bản rủi ro và lập luận chọn 2 kịch bản đắt nhất · §6 tiêu chí Pass/Fail và chấm thử · §7 ghi ca lạ · tạo repo, soát chéo §1/§4/§5 với prototype · demo: 30 giây mở đầu và dẫn ca lạ |
| ✏️ Người 2 | ✏️ | Chính sách dựng và dữ liệu giả · §3 Khi AI sai (câu AI nói, loại lỗi, HAX/PAIR) · toàn bộ câu chữ trong prototype · §5 lập luận cách hiển thị và 5 ảnh đánh số · demo: chỉ từng nguyên tắc HAX/PAIR trên màn hình |
| ✏️ Người 3 | ✏️ | Điều phối bước tự xếp mức · §4 Mức tự chủ (cost-of-error, tách `chi_hoan_tien`, thử trên 3 kịch bản) · dựng `prototype/index.html` 3 góc nhìn · script gọi AI thật `prototype/ai/` · demo: bấm prototype qua ca khó, trả lời về mức tự chủ |

> **Chính sách dựng dùng xuyên suốt bài** (khác chính sách thật của Shopee là 15 ngày): hạn yêu cầu trả hàng **7 ngày** kể từ ngày nhận · shop có **48 giờ** để phản hồi một khiếu nại · nhân viên sàn xử lý trong **24 giờ** sau khi hồ sơ vào hàng chờ, quá hạn thì tự lên trưởng nhóm. “Hôm nay” trong mọi ví dụ là **12/11/2026 14:30**.

---

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

