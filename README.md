# I2C AGR12 Pressure Sensor 0~100kPa ASAIR

- Hardware:

  - https://hshop.vn/cam-bien-ap-suat-khong-khi-i2c-agr12-pressure-sensor-0-100kpa-asair
  - https://hshop.vn/mach-vietduino-wifi-ble-esp32-arduino-compatible
  - https://hshop.vn/mach-vietduino-uno-usb-c-arduino-uno-compatible
 
- Khảo sát cảm biến áp suất AGR12 29/05/2026

  Vấn đề: Chương trình mẫu trên website Hshop, ESP32 không đọc được giá trị trong vùng 15.5kPA - 25.5kPA. Nhưng chương trình nội bộ lưu trong HS-03 thì vãn test bình thường
1. Quay lại video tình trạng lỗi với ESP32
2. THử lại với Arduino Uno --> OK
3. Thử lại với chương trình nội bộ (ESP32 và Uno) --> không chạy và nhìn phức tạp hơn hẳn
4. Thử dùng chương trình slave_receiver
 
