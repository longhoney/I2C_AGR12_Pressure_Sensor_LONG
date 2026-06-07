# Các bước thực hiện trong chương trình chung
BƯỚC 1: Gửi lệnh đo lường (0xAC 0x12)
(Xử lý lỗi truyền I2C nếu cần)

BƯỚC 2: Chờ 80ms để cảm biến hoàn tất phép đo

BƯỚC 3: Yêu cầu đọc 3 byte dữ liệu (DATA0, DATA1, CRC)

BƯỚC 4: Tính toán và kiểm tra CRC. CRC là kết quả của DATA0 XOR DATA1 [24, Bảng 5]

BƯỚC 5: Chuyển đổi dữ liệu thành giá trị áp suất
- Ghép 2 byte dữ liệu thành giá trị 16 bit (kPa * 10)
- Ép kiểu thành số nguyên có dấu 16 bit (Signed Short Int) để xử lý áp suất âm (nếu có, ví dụ AGR12xxPxx hoặc AGR12xxNxx)
- Chia cho 10.0 để có giá trị áp suất thực tế (kPa)

BƯỚC 6: Hiển thị kết quả
- Số byte Uno đọc được (biến count)
- Dữ liệu dạng HEX Uno đọc được từ cảm biến | CRC Uno tính lại
- Giá trị áp suất thực tế

### I2C_AGR12_Pressure_Sensor_Uno
_Chương trình chạy với tần số 50kHz, lặp lại mỗi 1 giây 1 lần_

_Sử đụng được với vi điều khiển: Arduino Uno, ESP8266 (dùng thêm mạch chuyển mức tín hiệu)_

### I2C_AGR12_Pressure_Sensor_ESP32
_Chương trình chạy với **tần số 10kHz**, lặp lại mỗi 1 giây 1 lần. Thống nhất dùng mạch chuyển mức tín hiệu riêng cho mọi mạch ESP32_

_Sử dụng được với ESP8266, lưu ý phần cấu hình chân I2C_

