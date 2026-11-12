
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
