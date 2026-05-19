# UET_Parking_Management
Bài tập lớn môn Công nghệ phần mềm.
Thiết kế Hệ thống Bãi xe Thông minh cho Cụm trường UET - UEB

Dự án nghiên cứu, phân tích và thiết kế hệ thống quản lý bãi đỗ xe tự động ứng dụng công nghệ nhận diện biển số và thuật toán tối ưu biểu phí linh hoạt dành cho cụm khuôn viên trường Đại học Công nghệ (UET) và Đại học Kinh tế (UEB).

---

## 📝 1. Lời Giới Thiệu Dự Án

Trong bối cảnh hạ tầng giao thông tĩnh tại các khuôn viên đại học ngày càng chịu áp lực lớn, việc tối ưu hóa quy trình vận hành bãi xe là một bài toán cấp thiết. **Hệ thống Quản lý Bãi đỗ xe UET** được nghiên cứu và phát triển nhằm hiện đại hóa toàn diện công tác kiểm soát phương tiện giao thông tại cụm bãi xe nội bộ. Mục tiêu cốt lõi của dự án là giải quyết triệt để tình trạng ùn tắc vào các khung giờ cao điểm chuyển ca, giảm thiểu sai sót thủ công và nâng cao mức độ an tâm cho sinh viên cũng như cán bộ nhà trường.

Điểm đặc thù mang tính thực tiễn cao của hệ thống nằm ở phân hệ quản lý **vé lượt** kết hợp giải pháp thanh toán không tiền mặt. Thay vì áp dụng một mức phí cố định hay các hình thức tính toán thủ công dễ gây nhầm lẫn và chậm trễ, hệ thống tích hợp một **thuật toán tính giá linh hoạt tự động theo thời gian thực**. 

Cụ thể, thuật toán sẽ tự động nhận diện và phân rã biểu phí dựa trên mốc thời gian xe ra khỏi bãi:
* **Khung giờ ban ngày (Trước 18h00):** Áp dụng mức phí **3.000 VNĐ/lượt** nhằm hỗ trợ tối đa cho sinh viên học tập trong giờ hành chính.
* **Khung giờ ban đêm (Sau 18h00):** Tự động chuyển trạng thái rẽ nhánh sang mức phí **5.000 VNĐ/lượt** để phù hợp với đặc thù quản lý ca đêm.

Sự kết hợp giữa công nghệ nhận diện biển số tự động (ANPR) và thuật toán phân loại biểu phí thông minh này giúp bãi xe vận hành mượt mà, minh bạch hóa dòng tiền và cắt giảm tối đa thời gian chờ đợi tại bốt kiểm soát.

---

## 👥 2. Thành Viên Nhóm Thực Hiện

| STT | Họ và Tên | Mã Sinh Viên | Vai trò / Phân nhiệm chính |
| :-: | --- | :-: | --- |
| 1 | **Giàng A Hải** | 24020484 | Trưởng nhóm / Phân tích hệ thống |
| 2 | **Ngô Thị Cẩm Chi** | 24020413 | Phát triển tài liệu đặc tả & Thiết kế dữ liệu |
| 3 | **Lê Ánh Dương** | 24020460 | Thiết kế thuật toán tính phí & Xử lý ngoại lệ |

---

## 📊 3. Kết Quả Khảo Sát Thực Trạng

Qua dữ liệu thu thập thực tế từ cụm sinh viên trường Đại học Công nghệ (UET) và Đại học Kinh tế (UEB) dùng chung bãi xe, hệ thống định hình dựa trên các chỉ số thực trạng sau:

* **Đối tượng & Phương tiện:** 95.5% đối tượng sử dụng là sinh viên nội bộ, phương tiện di chuyển chủ yếu là xe máy và xe đạp/xe điện. Tần suất gửi xe hàng ngày chiếm tỷ lệ cao nhất (63.6%).
* **Vấn đề ùn tắc & Tiền lẻ:** 59.1% người dùng gặp khó khăn trong việc chuẩn bị tiền lẻ khi thanh toán vé lượt bằng tiền mặt, dẫn đến tình trạng ùn tắc nghiêm trọng tại cổng ra vào giờ cao điểm (đầu ca 2, ca 4 và lúc tan tầm).
* **Nhu cầu công nghệ:** 100% người dùng mong muốn có giải pháp tự động hóa. Trong đó, nhu cầu thanh toán tự động không tiền mặt (qua mã QR) chiếm 81.8% và xác thực bằng thẻ sinh viên/thẻ từ chiếm 86.4%.
* **Xử lý sự cố:** Rủi ro thường gặp là sinh viên bị mất thẻ xe. Người dùng đồng thuận với quy trình xử lý kiểm tra giấy tờ chính chủ và chịu mức phạt cố định 100.000 VNĐ để bảo mật an ninh bãi xe.
* **Phương thức tương tác:** Tối ưu hóa tốc độ qua màn hình hiển thị trực tiếp tại bãi xe và đầu đọc thẻ tại cổng, loại bỏ các bước cài đặt ứng dụng di động phức tạp khi ra vào gate.

---

## 🏗️ 4. Các Tác Nhân Hệ Thống (Actors)

| Tác nhân (Actor) | Mô tả Vai trò & Trách nhiệm trong Hệ thống |
| --- | --- |
| **Người gửi xe** | Sinh viên UET và sinh viên UEB dùng chung mặt bằng hạ tầng. Thực hiện quẹt thẻ để vào/ra bãi, quét mã QR thanh toán phí hoặc trình báo sự cố khi có lỗi mất thẻ. |
| **Nhân viên bảo vệ** | Nhân sự trực tiếp tại bốt kiểm soát. Giám sát quá trình tự động hóa, đối chiếu thông tin phương tiện, xử lý thủ công các ca đặc biệt (như sự cố mất thẻ) và xác nhận cho xe xuất nhập bãi. |
| **Quản trị viên (Admin)** | Chịu trách nhiệm quản lý vận hành phía Back-office: kiểm soát trạng thái cấp phát của kho thẻ từ, tra cứu dữ liệu lịch sử hệ thống và truy xuất báo cáo doanh thu tài chính. |
| **Hệ thống Quản lý** | Phần mềm nền tảng tự động xử lý dữ liệu: điều khiển camera, trích xuất dữ liệu biển số xe, tính toán biểu phí dựa trên thời gian và khởi tạo mã QR thanh toán động. |

---

## ⚙️ 5. Yêu Cầu Chức Năng & Phi Chức Năng

### 5.1 Yêu Cầu Chức Năng (Functional Requirements)
* **FR-ENTRY-01 (Xử lý quẹt thẻ vào):** Tiếp nhận sự kiện quẹt thẻ từ/vé từ Người gửi xe tại cổng kiểm soát lối vào bãi.
* **FR-ENTRY-02 (Ghi nhận thông tin xe vào):** Điều khiển camera tự động chụp ảnh biển số, ảnh toàn cảnh và đóng dấu thời gian vào cơ sở dữ liệu.
* **FR-EXIT-01 (Xử lý quẹt thẻ ra):** Đọc dữ liệu thẻ xe và kiểm tra tính hợp lệ khi xe tiến đến bốt kiểm soát lối ra.
* **FR-EXIT-02 (Rẽ nhánh tính phí tự động):** Áp dụng quy tắc tính phí theo khung giờ: Thu **3.000 VNĐ** nếu thời gian ra $\le$ 18h; Thu **5.000 VNĐ** nếu thời gian ra $>$ 18h.
* **FR-EXIT-03 (Thanh toán qua mã QR):** Sinh mã QR thanh toán động hiển thị trực tiếp lên màn hình phụ tại bốt để người dùng quét mã.
* **FR-LOST-01 (Xử lý sự cố mất thẻ):** Cho phép lập biên bản sự cố, áp mức phạt cố định **100.000 VNĐ** sau khi kiểm tra giấy tờ xác minh chính chủ để giải phóng xe ra ngoài.
* **FR-ADMIN-01 (Quản lý thẻ & Thống kê):** Cung cấp giao diện quản trị kho thẻ, xem toàn bộ log lịch sử hệ thống và kết xuất dữ liệu báo cáo thống kê doanh thu.

### 5.2 Yêu Cầu Phi Chức Năng (Non-Functional Requirements)
* **Hiệu năng (Performance):** Thời gian thực thi trọn vẹn từ lúc quẹt thẻ, chụp ảnh đối khớp thông tin đến khi phát lệnh mở barrier phải đạt thời gian **< 2.0 giây** nhằm tối ưu giải tỏa ùn tắc giờ cao điểm.
* **Độ chính xác (Accuracy):** Thuật toán nhận diện ký tự biển số tự động (ANPR) từ camera luồng vào và ra phải đảm bảo độ chính xác **> 96%** trong điều kiện ánh sáng tiêu chuẩn.
* **Độ tin cậy (Reliability):** Trong trường hợp mất kết nối mạng nội bộ, chức năng kiểm tra tại bốt phải cho phép lưu trữ dữ liệu offline tạm thời để đảm bảo không làm gián đoạn luồng xe ra vào.

---

## 📋 6. Danh Sách User Stories

### Phân hệ Quản lý Xe Vào (Entry Process)
#### US-01 | Khách vào bãi
* **Phát biểu:** Là một *Người gửi xe (Sinh viên UET/UEB)*, tôi muốn *dừng xe tại lối vào và tiến hành quẹt thẻ từ/vé lên đầu đọc*, để *hệ thống ghi nhận lượt vào và mở cổng cho tôi vào bãi xe*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Hệ thống phản hồi tín hiệu "Bíp" xác nhận đã đọc thẻ trong vòng dưới 0.3 giây.
  * Màn hình hiển thị thông tin chào mừng ngắn gọn và trạng thái thẻ hợp lệ.

#### US-02 | Chụp ảnh tự động
* **Phát biểu:** Là *Hệ thống quản lý tự động*, tôi muốn *tự động chụp ảnh biển số, ảnh toàn cảnh phương tiện và ghi dấu thời gian vào hệ thống ngay khi thẻ được quẹt*, để *thiết lập dữ liệu minh chứng phục vụ đối khớp an ninh ở cổng ra*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Dữ liệu bao gồm 2 file ảnh (ảnh biển số + ảnh người lái) và 1 chuỗi ký tự biển số được lưu đồng bộ cùng mã ID của thẻ từ.
  * Barrier tự động nhấc lên góc 90 độ ngay sau khi lưu dữ liệu thành công.

---

### Phân hệ Quản lý Xe Ra & Tính phí (Exit Process)
#### US-03 | Đối khớp thông tin ra
* **Phát biểu:** Là một *Người gửi xe*, tôi muốn *quẹt thẻ từ/vé tại đầu đọc cổng ra*, để *hệ thống kiểm tra thông tin đối khớp xe vào và bắt đầu quy trình tính phí*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Hệ thống thực hiện đối khớp cơ sở dữ liệu ảnh và chuỗi ký tự biển số xe lúc vào với biển số hiện tại ở cổng ra.
  * Nếu thông tin trùng khớp, hệ thống chuyển tiếp sang màn hình hiển thị biểu phí.

#### US-04 | Tính phí theo ca giờ
* **Phát biểu:** Là *Hệ thống quản lý tự động*, tôi muốn *tự động tính toán chi phí gửi xe dựa trên mốc thời gian thực tế*, để *áp dụng mức thu phí chính xác theo ca quy định (3.000 VNĐ cho ca ngày, 5.000 VNĐ cho ca đêm)*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Nếu thời điểm xe ra $\le$ 18h, hệ thống áp mức phí cố định là 3.000 VNĐ.
  * Nếu thời điểm xe ra $>$ 18h, hệ thống tự động chuyển sang mức phí ca đêm là 5.000 VNĐ.

#### US-05 | Hiển thị mã QR thanh toán
* **Phát biểu:** Là một *Người gửi xe*, tôi muốn *nhìn thấy số tiền phải trả và mã QR động hiển thị trên màn hình tại bốt trực*, để *tôi quét mã thanh toán nhanh qua ví điện tử/ngân hàng mà không cần chuẩn bị tiền lẻ*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Mã QR được sinh ra chứa sẵn số tiền cần thanh toán và thông tin nội dung chuyển khoản định danh duy nhất của lượt gửi đó.
  * Thời gian hiển thị mã QR ngay sau khi quẹt thẻ ra phải < 0.5 giây.

#### US-06 | Xác nhận giải phóng xe
* **Phát biểu:** Là một *Nhân viên bảo vệ tại bốt kiểm soát*, tôi muốn *hệ thống hiển thị trạng thái 'Đã thanh toán thành công' trực quan trên màn hình giám sát*, để *tôi ra hiệu lệnh/mở barrier cho xe xuất bến an toàn và nhanh chóng*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Màn hình của bảo vệ chuyển sang trạng thái màu xanh lá cây kèm thông báo lệnh mở barrier ngay khi hệ thống nhận được callback thanh toán thành công.
  * Lịch sử giao dịch được ghi nhận đầy đủ vào log doanh thu của ngày hệ thống.

---

### Phân hệ Quản lý Sự cố Mất thẻ (Lost Ticket Process)
#### US-07 | Trình báo mất thẻ
* **Phát biểu:** Là một *Người gửi xe vô tình làm mất thẻ xe trong trường*, tôi muốn *báo cáo sự cố mất thẻ trực tiếp với nhân viên bảo vệ tại cổng ra*, để *được xử lý giải phóng xe ra khỏi bãi theo đúng quy định an ninh*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Người gửi xe cung cấp được giấy đăng ký xe, CCCD hoặc thẻ sinh viên chính chủ để bảo vệ đối chiếu với thông tin ảnh chụp lưu trên hệ thống lúc vào bãi.

#### US-08 | Xử lý biên bản & Phạt vi phạm
* **Phát biểu:** Là một *Nhân viên bảo vệ*, tôi muốn *hệ thống cung cấp chức năng lập biên bản sự cố mất thẻ xe và áp mức phạt cố định 100.000 VNĐ*, để *thu tiền phạt theo đúng chính sách quy định của nhà trường trước khi cho xe ra*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Giao diện phần mềm hỗ trợ nút bấm "Xử lý mất thẻ", tự động điền mức phạt 100.000 VNĐ vào phiếu thu sự cố.
  * Hệ thống lưu vết định danh tài khoản của bảo vệ thực hiện xử lý ca ngoại lệ này kèm hình ảnh xe ra để phục vụ hậu kiểm đối soát.

---

### Phân hệ Quản trị & Thống kê (Admin Back-office)
#### US-09 | Quản lý kho thẻ từ
* **Phát biểu:** Là một *Quản trị viên hệ thống (Admin)*, tôi muốn *quản lý trạng thái và thông tin của toàn bộ kho thẻ từ (Thêm mới, khóa thẻ bị mất, kích hoạt lại thẻ)*, để *đảm bảo an toàn vận hành, tránh việc kẻ gian lợi dụng thẻ cũ nhặt được để trộm xe*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Admin có thể tìm kiếm thẻ theo mã UID, chuyển đổi trạng thái thẻ thành "Active", "Blocked" hoặc "Lost" trên bảng điều khiển quản trị.

#### US-10 | Tra cứu lịch sử hệ thống
* **Phát biểu:** Là một *Quản trị viên hệ thống (Admin)*, tôi muốn *tra cứu toàn bộ lịch sử vào/ra của bãi xe (bao gồm mốc thời gian, hình ảnh chụp phương tiện, ID thẻ và định danh bảo vệ xử lý)*, để *giải quyết các khiếu nại, tranh chấp hoặc hỗ trợ cơ quan chức năng điều tra khi có sự cố an ninh*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Hệ thống hỗ trợ bộ lọc tìm kiếm đa năng theo: Biển số xe, Khoảng thời gian (Từ ngày - Đến ngày), Loại xe và Trạng thái (Hợp lệ / Mất thẻ).

#### US-11 | Thống kê doanh thu định kỳ
* **Phát biểu:** Là một *Quản trị viên hệ thống (Admin)*, tôi muốn *hệ thống tự động thống kê doanh thu và xuất báo cáo định kỳ (theo ngày/tuần/tháng)*, để *theo dõi chính xác hiệu quả tài chính và quản lý minh bạch dòng tiền của bãi xe trường*.
* **Tiêu chí nghiệm thu (Acceptance Criteria):**
  * Báo cáo kết xuất ra định dạng file Excel (.xlsx) thể hiện chi tiết tổng doanh thu ca ngày, tổng doanh thu ca đêm, tổng tiền phạt mất thẻ và phân rã theo từng cổng kiểm soát.
