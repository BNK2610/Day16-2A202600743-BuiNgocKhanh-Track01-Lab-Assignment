---
artifact: 02 — JTBD Project Analysis
bai-tap: Lab 2 — Dùng JTBD để soi lại dự án nhóm
format: Theo nhóm dự án → share trong bàn → chốt hypothesis cuối
time: 25 phút trên lớp
nop-cuoi: Có — đây là file nộp cuối của Lab 2
companion-reference: Strategyn_JTBD_Playbook.pdf (giảng viên gửi kèm)
---

# Lab 2 — JTBD Project Analysis / Dùng JTBD để soi lại dự án nhóm

**Tên dự án / sản phẩm:** Trợ Lý Đặt Xe An Toàn (V-VoiceRide)

> Nguồn đầu vào cho bản phân tích: Product Brief, PRD và Strategyn JTBD Playbook.
> Những mô tả về hành vi người dùng chưa được kiểm chứng bằng phỏng vấn được ghi rõ là giả thuyết cần validate.

## Bước 0 — Khoanh đúng 1 lát cắt của dự án

- [x] **1 nhóm người dùng chính**
- [x] **1 hoàn cảnh / tình huống rõ**
- [x] **1 job cốt lõi**
- [x] **1 workflow đủ cụ thể để vẽ ra được**

- **Dự án của nhóm tôi là:** Trợ lý giúp người dùng đặt một chuyến xe giả lập bằng hội thoại tiếng Việt, có cơ chế hỏi lại, sửa thông tin và xác nhận an toàn.
- **Lát cắt tôi chọn để phân tích hôm nay là:** Người lớn tuổi hoặc ít thành thạo công nghệ tự sắp xếp chuyến xe đi bệnh viện trong trường hợp khó nhập địa chỉ và kiểm tra thông tin trên ứng dụng.
- **Vì sao tôi chọn lát cắt này:**
  > Đây là primary journey rõ nhất trong PRD, có rủi ro thực tế nếu điểm đón/điểm đến bị hiểu sai và có workflow đủ cụ thể để phân tích. Lát cắt này cũng buộc nhóm đánh giá giá trị của AI qua khả năng giúp user hoàn thành job an toàn, thay vì chỉ trình diễn voice interface.

## Bước 1 — `Project Snapshot`

1. **Nhóm tôi đang nghĩ mình đang giải quyết vấn đề gì?**
   > Một số người lớn tuổi hoặc ít rành công nghệ gặp khó khăn khi nhập địa chỉ, đọc thông tin nhỏ, xử lý nhiều lựa chọn và sửa dữ liệu sai trong ứng dụng gọi xe. Điều này làm họ khó tự đặt chuyến và có thể dẫn đến sai điểm đón, sai điểm đến hoặc lên nhầm xe.

2. **Người dùng chính hiện nhóm đang nhắm tới là ai?**
   > Người lớn tuổi hoặc người ít thành thạo ứng dụng đặt xe, vẫn có nhu cầu tự sắp xếp chuyến đi bằng điện thoại. Người khiếm thị và người bận tay/mắt là secondary personas, không phải lát cắt chính của bài này.

3. **Hiện tại người dùng đó đang giải quyết vấn đề này bằng cách nào?**
   > Giả thuyết hiện tại là họ tự thao tác trên Grab/Be hoặc ứng dụng tương tự, gọi tổng đài taxi, nhờ người thân đặt hộ, hoặc trì hoãn/không tự thực hiện chuyến đi. PRD chưa có interview để xác nhận alternative nào phổ biến nhất.

## Bước 2 — `Market Context`

1. **Ai đang gặp vấn đề này?**
   > Người lớn tuổi hoặc người ít thành thạo smartphone, đặc biệt khi thị lực, khả năng nhập liệu hoặc khả năng xử lý giao diện nhiều bước bị hạn chế.

2. **Vấn đề xuất hiện trong hoàn cảnh nào?**
   > Khi họ cần tự sắp xếp chuyến đi, ví dụ đi bệnh viện, nhưng phải nhập hoặc chọn địa chỉ, kiểm tra điểm đón/điểm đến, sửa lỗi và nhận diện đúng xe trong một giao diện thiên về thị giác.

3. **Hiện tại họ đang dùng giải pháp thay thế nào?**
   > App gọi xe truyền thống, tổng đài taxi, nhờ người thân/người chăm sóc đặt hộ, hoặc tự đi bằng phương tiện khác. Đây vẫn là danh sách giả thuyết cần kiểm chứng với người dùng thật.

4. **Vì sao đây là thời điểm đáng giải?**
   > STT, TTS và LLM tiếng Việt hiện có thể hỗ trợ hội thoại tự nhiên tốt hơn trước, nhưng việc tự động hóa một hành động có rủi ro vẫn cần guardrail rõ. Đây là cơ hội kiểm chứng liệu kết hợp AI hiểu hội thoại với state machine kiểm soát an toàn có giúp người dùng tự chủ hơn hay không.

### Tóm tắt market context

> Thị trường không nên được định nghĩa là “thị trường voice booking app”, mà là nhóm người gặp hạn chế thao tác số đang cố sắp xếp phương tiện để di chuyển an toàn và tự chủ. Họ hiện phải ghép nhiều giải pháp hoặc phụ thuộc người khác. Cơ hội của dự án nằm ở việc giảm effort và sai sót trong các bước có nhiều thông tin, đồng thời không lấy mất quyền kiểm soát của user.

## Bước 3 — Xác định `Job Executor`

- **Job executor của dự án này là:** Người lớn tuổi hoặc ít thành thạo công nghệ đang trực tiếp tự sắp xếp chuyến đi của mình.
- **Vì sao tôi tin đây là người trực tiếp "thuê" giải pháp để làm job:**
  > Chính họ xác định nhu cầu di chuyển, cung cấp điểm đón/điểm đến, chọn phương tiện, kiểm tra thông tin, yêu cầu sửa và quyết định xác nhận chuyến. Người thân có thể là buyer, influencer hoặc người hỗ trợ, nhưng không phải job executor trong lát cắt này.

## Bước 4 — Viết `Core JTBD`

### Bản nháp 1

**Core JTBD bản nháp:**
> Đặt xe bằng giọng nói để đi đúng nơi an toàn.

### Gạch bỏ từ solution nếu có

- Các từ solution tôi đang lỡ nhét vào câu: `đặt xe`, `bằng giọng nói`.

### Bản chốt

**Core JTBD cuối cùng:**
> Sắp xếp phương tiện để di chuyển từ điểm đón đến đúng điểm đến một cách an toàn và tự chủ khi khả năng nhập hoặc kiểm tra thông tin bị hạn chế.

### Tự kiểm

- [x] Nếu bỏ V-VoiceRide, voice hay AI, job này vẫn tồn tại.
- [x] Câu không chứa tên sản phẩm, AI, chatbot, app hoặc giao diện.
- [x] Câu mô tả điều user muốn hoàn thành, không mô tả tính năng.

## Bước 5 — Viết 3 `Job Stories`

| # | Trigger / When | Motivation / I want to | Outcome / so I can | Điều story này cho thấy |
|---|---|---|---|---|
| JS1 | Khi cần tự đi bệnh viện nhưng khó nhập một địa chỉ dài trên điện thoại | Tôi muốn truyền đạt rõ nơi đón và nơi cần đến, rồi kiểm tra lại hệ thống đã hiểu đúng | Tôi có thể tự sắp xếp chuyến đi mà không phải nhờ người thân | Giá trị cảm xúc và chức năng cùng nằm ở sự tự chủ, không chỉ ở tốc độ |
| JS2 | Khi phát hiện điểm đón hoặc điểm đến được hiểu sai trước lúc xác nhận | Tôi muốn sửa đúng phần sai mà không phải cung cấp lại toàn bộ thông tin | Tôi giảm công sức, tránh bối rối và không tạo nhầm chuyến | Correction là một phần cốt lõi của job, không phải edge feature |
| JS3 | Khi phương tiện sắp tới và tôi cần nhận diện đúng xe | Tôi muốn nhận lại thông tin tài xế, màu xe, biển số và trạng thái một cách rõ ràng | Tôi có thể lên đúng xe và cảm thấy an toàn hơn | Job chưa kết thúc ở “booking created”; user còn phải xác định đúng phương tiện |

### Tự kiểm nhanh

- [x] Mỗi story mô tả một tình huống cụ thể.
- [x] Ba story đại diện cho ba thời điểm khác nhau: khởi tạo, sửa lỗi và nhận diện xe.
- [x] Các story là giả thuyết dựa trên PRD và cần phỏng vấn để kiểm chứng tần suất, mức đau.

## Bước 6 — Liệt kê `Current Alternatives`

| Alternative hiện tại | User đang thuê nó để làm gì? | Nó làm tốt gì? | Nó fail ở đâu? | Switching cost hiện tại cao hay thấp? |
|---|---|---|---|---|
| Tự dùng Grab/Be hoặc app gọi xe tương tự | Tìm chuyến, nhập địa chỉ, xem giá/ETA và theo dõi tài xế | Hệ sinh thái thật, nhiều tài xế, quen thuộc, có bản đồ và thanh toán | Có thể tạo tải nhận thức cao; phụ thuộc nhập liệu, đọc màn hình và tự sửa lỗi | Cao ở giá trị marketplace và thói quen; thấp nếu chỉ xét giao diện hỗ trợ |
| Nhờ người thân/người chăm sóc đặt hộ | Chuyển phần thao tác và kiểm tra cho người đáng tin | Linh hoạt, có người xử lý tình huống và giải thích | Làm giảm tự chủ, phụ thuộc người khác có mặt/online và có thể truyền đạt sai | Cao về niềm tin; thấp nếu user thật sự muốn tự làm |
| Gọi tổng đài taxi hoặc gọi trực tiếp hãng xe | Nói nhu cầu cho nhân viên và nhận xe | Giao tiếp bằng giọng nói quen thuộc, không cần học app | Chờ đợi, khó kiểm tra trực quan, chất lượng phụ thuộc tổng đài và vẫn có thể nghe/truyền đạt sai địa chỉ | Trung bình |

**Nếu project của tôi biến mất hôm nay, user nhiều khả năng sẽ quay về:**
> Nhờ người thân đặt hộ nếu họ thiếu tự tin; nếu vẫn muốn tự làm, họ sẽ dùng app gọi xe hiện có hoặc gọi tổng đài. Thứ tự này là giả thuyết cần được xác nhận qua interview.

## Bước 7 — `JTBD Lite Map`

> Job map dưới đây mô tả điều user cố hoàn thành, không mô tả màn hình hay state machine của V-VoiceRide.

| Step | Trong workflow này user đang cố làm gì? | Hôm nay họ đang dùng gì? | Friction / pain hiện tại | Mức đau |
|---|---|---|---|---|
| Define | Xác định mục tiêu chuyến đi, thời điểm, điểm đón, điểm đến và nhu cầu phương tiện | Trí nhớ, giấy ghi chú, hỏi người thân, app bản đồ | Có thể không biết địa chỉ chính xác hoặc khó diễn đạt đủ yêu cầu | Med |
| Locate | Tìm đúng địa chỉ và phương án vận chuyển phù hợp | App gọi xe, bản đồ, tìm kiếm web, hỏi người thân/tổng đài | Địa danh mơ hồ, nhiều chi nhánh/lối vào, chữ nhỏ và nhiều lựa chọn | High |
| Prepare | Chuẩn bị thông tin và điều kiện cần để yêu cầu chuyến | Nhập địa chỉ, bật vị trí, chuẩn bị điện thoại/tài khoản/phương thức trả | Nhập liệu dài, quyền truy cập, thông tin phân tán và dễ quên bước | Med |
| Confirm | Kiểm tra phương tiện, điểm đón, điểm đến, ETA/chi phí trước khi cam kết | Đọc summary trên màn hình hoặc nghe nhân viên nhắc lại | Dễ bỏ sót thông tin sai; một nút xác nhận có thể bị bấm khi chưa hiểu rõ | High |
| Execute | Gửi yêu cầu và bảo đảm chuyến đã được ghi nhận | Bấm đặt xe trên app hoặc xác nhận với tổng đài/người thân | Không chắc yêu cầu đã thành công; dễ nhầm trạng thái đang xử lý với đã đặt | Med |
| Monitor | Theo dõi phương tiện được gán, vị trí/ETA và trạng thái đến đón | Bản đồ, thông báo, cuộc gọi tài xế | Khó đọc bản đồ/thông báo, khó biết khi nào xe tới hoặc có thay đổi | Med |
| Modify | Sửa điểm đón, điểm đến, loại xe hoặc xử lý khi thông tin sai/thay đổi | Quay lại form, hủy và đặt lại, gọi tài xế/tổng đài/người thân | Dễ mất thông tin đúng, phải làm lại nhiều bước, sợ tạo nhầm chuyến | High |
| Conclude | Xác định đúng xe và bắt đầu chuyến đi an toàn | Đọc biển số/màu xe, nhìn tài xế, gọi điện đối chiếu | Chữ/biển số khó nhìn, nhiều xe giống nhau, nguy cơ lên nhầm xe | High |

### Chốt 2 bước đau nhất

**Bước đau nhất #1:** `Locate` — xác định và chọn đúng điểm đón/điểm đến
**Bước đau nhất #2:** `Modify` — sửa đúng phần sai mà không làm lại từ đầu

**Vì sao đây là nơi đáng chú ý nhất:**
> Hai bước này kết hợp mức effort cao với hậu quả lớn nếu sai. Locate sai làm toàn bộ chuyến đi sai ngay từ đầu; Modify kém khiến user mất kiểm soát đúng lúc họ đã biết hệ thống hiểu sai. Confirm và Conclude cũng là bước an toàn quan trọng, nhưng cần guardrail và read-back hơn là để AI tự quyết định.

## Bước 8 — Chỉ ra `AI Leverage Point`

| Step | AI nên giúp bằng cách nào? | Vì sao AI hợp ở đây? | Rủi ro chính nếu dùng AI |
|---|---|---|---|
| Locate | Hiểu cách nói địa chỉ tự nhiên, trích xuất điểm đón/điểm đến, phát hiện thiếu hoặc mơ hồ và diễn đạt câu hỏi làm rõ ngắn gọn | Input ngôn ngữ có nhiều biến thể; LLM phù hợp để hiểu intent/context, còn geocoding cung cấp candidate có cấu trúc | AI tự đoán địa chỉ hoặc chọn candidate sai; STT nghe sai tên riêng/địa danh |
| Modify | Hiểu user muốn sửa slot nào và giá trị mới là gì, đồng thời giữ nguyên phần thông tin không liên quan | Yêu cầu sửa bằng lời nói thường không theo form cố định; hiểu ngữ nghĩa giúp giảm việc phải làm lại toàn bộ | Cập nhật nhầm slot, làm mất state cũ hoặc diễn giải quá mức ý của user |

**AI leverage point quan trọng nhất của dự án tôi là:**
> Hiểu và sửa thông tin chuyến đi từ ngôn ngữ tự nhiên ở hai bước Locate và Modify, sau đó chuyển kết quả có cấu trúc cho state machine kiểm tra.

**Vì sao không phải ở bước khác:**
> Ở Confirm và Execute, vấn đề chính là consent và kiểm soát rủi ro; AI không nên tự quyết định. State machine phải chặn booking khi thiếu slot, địa chỉ còn mơ hồ hoặc chưa có xác nhận rõ. Ở Monitor/Conclude, TTS và dữ liệu có cấu trúc hữu ích hơn việc để LLM suy đoán.

## Bước 9 — Viết `Product Hypothesis`

**Bản hypothesis của tôi:**

> Nếu chúng ta giúp người lớn tuổi hoặc ít thành thạo công nghệ xác định và sửa thông tin chuyến đi tốt hơn ở các bước Locate và Modify, bằng cách dùng AI hiểu hội thoại tiếng Việt nhưng bắt buộc mọi dữ liệu rủi ro đi qua geocoding, read-back và state machine, thì họ sẽ có xu hướng chuyển từ nhờ người thân hoặc vật lộn với form app sang một luồng hội thoại safety-first, vì họ có thể tự hoàn thành chuyến với ít thao tác hơn mà vẫn kiểm soát được thông tin trước khi xác nhận.

### Tín hiệu sớm nếu hypothesis này đúng

1. Trong usability test, ít nhất 80% người tham gia thuộc lát cắt có thể hoàn thành scenario hợp lệ, và correction success đạt ít nhất 70% mà không cần người hỗ trợ thao tác thay.
2. Người tham gia đánh giá mức tin tưởng/tự chủ từ 4/5 trở lên và chủ động chọn luồng này thay vì nhờ người thân trong ít nhất một tình huống thử nghiệm phù hợp.

## Bước 10 — `Assumptions to Validate`

| Assumption | Vì sao assumption này rủi ro? | Tôi đang có bằng chứng gì? | Cần validate bằng cách nào tiếp theo? |
|---|---|---|---|
| A1. Người lớn tuổi/ít rành công nghệ là job executor phù hợp và thật sự muốn tự đặt chuyến | Có thể người thân mới là người luôn thực hiện job; user không muốn hoặc không được phép tự làm | Persona và journey trong PRD, chưa có user research | Phỏng vấn 5-8 người dùng mục tiêu và 3-5 người chăm sóc; hỏi về chuyến gần nhất, không hỏi họ có thích ý tưởng không |
| A2. Locate và Modify là hai pain đủ lớn, xảy ra đủ thường xuyên | Team có thể đang ưu tiên edge case trong khi pain chính là giá, thiếu tài xế hoặc thanh toán | Các critical scenarios và risk analysis nội bộ trong PRD | Contextual interview/usability test trên app hiện tại; ghi số lần cần trợ giúp, lỗi và thời gian ở từng step |
| A3. Voice/hội thoại giảm effort tốt hơn form hoặc accessibility mode hiện có | Môi trường ồn, giọng vùng miền hoặc STT sai có thể làm voice chậm và đáng sợ hơn | Technical concept và scenario test; chưa có so sánh người dùng | Prototype test A/B voice-first với form đơn giản; đo completion, correction, time, confidence và preference |
| A4. User đủ tin hệ thống sau read-back và explicit confirmation | Việc AI nghe sai một lần có thể làm user mất niềm tin; câu xác nhận bắt buộc có thể gây khó nhớ | Safety invariants trong PRD, chưa có bằng chứng hành vi | Test nhiều cách read-back/xác nhận; quan sát user có hiểu trạng thái và tự phát hiện lỗi hay không |
| A5. User sẽ chuyển khỏi alternative hiện tại dù MVP chưa gọi xe thật | Một demo booking không tạo đủ giá trị để kiểm chứng switching; marketplace và độ tin cậy của app hiện tại là moat lớn | Chưa có bằng chứng; MVP chủ yếu chứng minh interaction | Test concierge hoặc clickable prototype nối với quy trình đặt xe có người hỗ trợ; hỏi lựa chọn trên tình huống thật và willingness to adopt |

### Assumption nguy hiểm nhất nếu tôi đang sai

> A1: người dùng mục tiêu thật sự muốn và có khả năng tự sắp xếp chuyến đi. Nếu họ luôn muốn người thân/tổng đài chịu trách nhiệm, hoặc nhu cầu tự chủ không đủ mạnh, thì dù voice và safety flow hoạt động tốt, product hypothesis vẫn không tạo ra adoption.

## Bước 11 — Share trong bàn

### Mỗi người / mỗi nhóm chỉ nói 4 thứ

1. **Job executor của bạn là ai**
2. **Core JTBD của bạn là gì**
3. **Step đau nhất đang nằm ở đâu**
4. **AI leverage point + assumption rủi ro nhất là gì**

### Nếu chưa biết hỏi ngược gì, dùng 4 câu này

1. **"Câu JTBD này có đang lỡ nhét solution vào không?"**
2. **"Alternative hiện tại của user là gì, và tại sao họ chưa bỏ nó?"**
3. **"Pain mạnh nhất nằm ở bước nào trong workflow, có chắc AI giải tốt được không?"**
4. **"Assumption nào nếu sai thì cả hypothesis sẽ sập?"**

### Ghi nhanh sau khi nghe bàn phản biện

| Ý phản biện tôi nghe được | Nó chạm vào phần nào? | Tôi sẽ giữ / sửa gì? |
|---|---|---|
| Nhóm “người lớn tuổi hoặc ít thành thạo công nghệ” vẫn khá rộng; mức suy giảm thị lực, kinh nghiệm dùng app và mức sẵn sàng tự đặt xe có thể rất khác nhau. Cần khóa rõ bối cảnh sử dụng thay vì coi toàn bộ nhóm có cùng hành vi. | `Job executor`, lát cắt người dùng và assumption A1 | Giữ nhóm primary persona theo PRD nhưng thu hẹp lát cắt cuối thành người lớn tuổi/ít rành app đang cần tự sắp xếp chuyến đi bệnh viện và gặp khó ở việc nhập, kiểm tra hoặc sửa địa chỉ. Tiếp tục coi mong muốn tự chủ là assumption cần validate, không xem là fact. |
| `Locate` và `Modify` hợp lý theo logic sản phẩm, nhưng hiện mới được suy ra từ PRD. Có thể pain thật của user lại là giá, thiếu xe, thanh toán, sợ đi một mình hoặc muốn người thân chịu trách nhiệm. | Hai pain step và mức độ ưu tiên | Tạm giữ `Locate` và `Modify` làm hai pain cần thiết kế test, đồng thời ghi rõ cần contextual interview/usability test để xác nhận tần suất và mức đau trước khi đầu tư sâu. |
| Product hypothesis hiện gộp quá nhiều điều: AI hiểu đúng, guardrail hoạt động, user hoàn thành được, cảm thấy tin tưởng và chuyển khỏi alternative. Nếu test thất bại sẽ khó biết giả định nào sai. | `Product hypothesis`, success signal và kế hoạch validate | Sửa hypothesis cuối theo hướng hẹp hơn: kiểm tra liệu luồng hội thoại có giúp user hoàn thành tác vụ với ít trợ giúp hơn và giữ cảm giác kiểm soát hay không. Việc chuyển khỏi app/người thân được giữ thành assumption riêng để test sau. |

## Bước 12 — Chốt version cuối sau thảo luận

### Sau khi nghe phản biện, tôi thay đổi gì?

- [ ] Giữ nguyên `job executor`
- [x] Sửa `job executor`
- [x] Giữ nguyên `core JTBD`
- [ ] Sửa `core JTBD`
- [x] Giữ nguyên `AI leverage point`
- [ ] Sửa `AI leverage point`
- [ ] Giữ nguyên `product hypothesis`
- [x] Sửa `product hypothesis`

### Vì sao tôi giữ / sửa?

> Tôi giữ `core JTBD` vì câu hiện tại mô tả kết quả người dùng muốn hoàn thành — di chuyển đúng nơi, an toàn và tự chủ — mà không phụ thuộc vào voice, AI hay sản phẩm V-VoiceRide. Tôi cũng giữ `AI leverage point` ở Locate và Modify vì hiểu cách diễn đạt địa chỉ tự nhiên và yêu cầu sửa từng phần là nơi AI có lợi thế rõ nhất; các quyết định an toàn cuối vẫn thuộc về geocoding, read-back và state machine.
>
> Tôi sửa `job executor` để khóa rõ hơn bối cảnh đi bệnh viện và loại khó khăn mà người dùng đang gặp, thay vì coi mọi người lớn tuổi hoặc ít rành công nghệ là một nhóm đồng nhất. Tôi sửa `product hypothesis` vì bản trước gộp quá nhiều giả định và tuyên bố switching quá sớm. Bản cuối tập trung vào kết quả có thể kiểm chứng trước: mức độ hoàn thành tác vụ, nhu cầu trợ giúp và cảm giác kiểm soát. Các kết luận này vẫn là giả thuyết dựa trên PRD, chưa phải bằng chứng hành vi từ người dùng thật.

### Version cuối cùng tôi nộp

**Job executor:**
> Người lớn tuổi hoặc ít thành thạo ứng dụng đặt xe đang trực tiếp cần tự sắp xếp chuyến đi bệnh viện và gặp khó khăn khi nhập, kiểm tra hoặc sửa thông tin chuyến đi trên điện thoại.

**Core JTBD:**
> Sắp xếp phương tiện để di chuyển từ điểm đón đến đúng điểm đến một cách an toàn và tự chủ khi khả năng nhập hoặc kiểm tra thông tin bị hạn chế.

**2 bước đau nhất trong workflow:**
> `Locate`: xác định và chọn đúng điểm đón, điểm đến khi địa chỉ dài, không đầy đủ hoặc mơ hồ.
>
> `Modify`: sửa đúng phần thông tin bị hiểu sai mà không phải cung cấp lại toàn bộ yêu cầu hoặc bắt đầu lại từ đầu.

**AI leverage point chính:**
> Dùng AI để hiểu cách người dùng diễn đạt điểm đón, điểm đến và yêu cầu sửa bằng tiếng Việt tự nhiên tại các bước Locate và Modify. Kết quả phải được chuyển thành dữ liệu có cấu trúc để geocoding, read-back và state machine kiểm tra; AI không được tự chọn địa chỉ mơ hồ hoặc tự quyết định tạo booking.

**Product hypothesis:**
> Nếu người lớn tuổi hoặc ít thành thạo ứng dụng đặt xe có thể cung cấp và sửa thông tin chuyến đi bằng hội thoại tiếng Việt, đồng thời được nghe lại và xác nhận rõ trước khi tạo booking, thì họ sẽ hoàn thành kịch bản tự sắp xếp chuyến đi với ít trợ giúp hơn và cảm thấy kiểm soát, an toàn hơn so với khi tự thao tác trên form ứng dụng.

**Assumption cần validate đầu tiên:**
> Người dùng trong lát cắt này thực sự muốn tự sắp xếp chuyến đi và sẵn sàng chịu trách nhiệm xác nhận thông tin, thay vì luôn muốn người thân hoặc tổng đài thực hiện và chịu trách nhiệm thay họ.

## Checklist trước khi nộp

- [x] Tôi đã khoanh đúng 1 lát cắt cụ thể của dự án.
- [x] Tôi đã phân biệt được `job executor` với buyer / influencer.
- [x] `Core JTBD` của tôi không nhét solution vào câu.
- [x] Tôi đã viết đủ 3 `job stories`.
- [x] Tôi đã điền `JTBD lite map` và khoanh ra 2 bước đau nhất.
- [x] Tôi đã chỉ ra `AI leverage point` thay vì nhảy thẳng vào feature list.
- [x] Tôi đã ghi rõ `assumptions to validate`.
- [x] Tôi đã sửa version cuối sau khi share trong bàn.

## Kết luận tự kiểm

> Nếu bỏ AI, dự án vẫn còn tạo giá trị ở read-back rõ ràng, giao diện dễ tiếp cận, sửa từng phần và guardrail xác nhận. AI làm tăng giá trị chủ yếu ở khả năng hiểu cách diễn đạt tự nhiên và correction linh hoạt; nó không phải nguồn quyết định an toàn cuối cùng.
