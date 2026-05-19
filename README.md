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

| STT | Họ và Tên | Mã Sinh Viên | Vai trò  |
| :-: | --- | :-: | --- |
| 1 | **Giàng A Hải** | 24020484 | Trưởng nhóm |
| 2 | **Ngô Thị Cẩm Chi** | 24020413 | Thành viên |
| 3 | **Lê Ánh Dương** | 24020460 | Thành viên |

---

## 💻 3. Logic Thuật Toán Tính Phí Linh Hoạt (3K/5K)

Hệ thống bãi xe UET tối ưu hóa riêng cho chu kỳ sinh hoạt của sinh viên/giảng viên với mô hình **Vé lượt đồng giá theo khung giờ checkout**. 

### Quy tắc rẽ nhánh hệ thống
Hệ thống chỉ căn cứ vào **thời điểm xe quẹt thẻ ra** để áp phí, không phụ thuộc vào tổng thời gian xe đỗ bên trong bãi là bao lâu:
* Nếu Giờ xuất bãi **<= 18:00:00**: Áp dụng mức phí cố định ca ngày là **3.000 VNĐ**.
* Nếu Giờ xuất bãi **> 18:00:00**: Tự động chuyển phân hệ sang mức phí ca đêm là **5.000 VNĐ**.

### Mã giả minh họa thuật toán (Pseudo-code)
```python
def calculate_parking_fee(ticket_id, current_timestamp):
    ticket = database.find_active_ticket(ticket_id)
    if not ticket:
        return ERROR_INVALID_TICKET
        
    exit_hour = current_timestamp.get_hour() 
    
    if exit_hour <= 18:
        fee = 3000  # Ca ngày (<= 18h)
    else:
        fee = 5000  # Ca đêm (> 18h)
        
    qr_code = qr_service.generate_dynamic_qr(amount=fee, reference=ticket_id)
    return fee, qr_code






  
