## Giới thiệu 
* Đề tài mình làm là “Hệ thống tưới cây & giám sát môi trường thông minh dùng STM32 + cảm biến IoT”.
* Mục tiêu là tự động điều khiển bơm, đèn, quạt dựa vào các thông số: độ ẩm đất, ánh sáng, nhiệt độ, độ ẩm không khí.
* Hệ thống có thể chỉnh ngưỡng hoạt động trực tiếp bằng nút nhấn, lưu lại trong EEPROM, hiển thị realtime trên 2 màn hình LCD.


## Công nghệ sử dụng
Vi điều khiển: STM32 (hoặc Arduino framework trên chip ARM).
* Cảm biến:  
1. Soil Moisture sensor → đo độ ẩm đất.
2. Light sensor → đo ánh sáng môi trường.
3. DHT11 → đo nhiệt độ, độ ẩm không khí.
4. Hiển thị: 2 màn hình LCD I2C:
5. LCD1 hiển thị giá trị cảm biến.
6. LCD2 hiển thị ngưỡng cài đặt.
7. Điều khiển thiết bị: Relay cho bơm nước, đèn, quạt.
8. Lưu trữ: EEPROM (lưu ngưỡng cài đặt để không mất khi reset).
* Chức năng thủ công: Các nút nhấn riêng để bật/tắt bơm, đèn, quạt thủ công.
* Anti-bounce (Debounce): Xử lý chống dội phím khi đọc nút nhấn.

## Điểm nổi bật (kỹ thuật quan trọng)  
* Tự viết hàm debounce() để xử lý nhiễu khi bấm nút.
* Sử dụng EEPROM để lưu lại ngưỡng điều khiển (ví dụ: độ ẩm đất < 40% thì bật bơm).
* Có cả chế độ tự động & chế độ thủ công (manual override).
* Cấu hình ngưỡng trực tiếp bằng nút nhấn, hiển thị rõ trên LCD.

Lập trình relay điều khiển thiết bị một cách thông minh: nếu bật thủ công thì bỏ qua auto, nếu auto thì so sánh với ngưỡng.
## Sơ đồ mạch thiết kế:  
![image](https://github.com/user-attachments/assets/fba3842c-e7d0-4d2a-ae84-66889b4d4f94)  

## Sơ đồ mạch in:  
![image](https://github.com/user-attachments/assets/91b17522-d36f-44c0-847f-05722fea052f)  



## Tính năng chính:  
* Giám sát liên tục các thông số môi trường và hiển thị trên màn hình LCD
* Điều khiển tự động các thiết bị dựa trên ngưỡng cài đặt
* Cho phép người dùng điều chỉnh ngưỡng thông qua nút nhấn và lưu trữ vào EEPROM
* Hỗ trợ điều khiển thủ công các thiết bị thông qua nút nhấn
* Thiết kế mạch in PCB với Altium Designer
