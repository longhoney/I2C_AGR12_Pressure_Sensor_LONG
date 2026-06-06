# Code anh Ngọc
### I2C_AGR12_Pressure_Sensor_Uno
_Chương trình chạy với tần số 50kHz, lặp lại mỗi 1 giây 1 lần_

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
- Dữ liệu thô sau khi đã ghép 2 byte dữ liệu thành giá trị 16 bit (kPa * 10) | Giá trị áp suất thực tế

### I2C_AGR12_Pressure_Sensor_ESP32
_Chương trình chạy với tần số 50kHz, lặp lại mỗi 1 giây 1 lần. Thống nhất dùng mạch chuyển mức tín hiệu riêng cho mọi mạch ESP32_

BƯỚC 1: Gửi lệnh đo lường (0xAC 0x12)
(Xử lý lỗi truyền I2C nếu cần)

BƯỚC 2: Chờ 80ms để cảm biến hoàn tất phép đo

BƯỚC 3: Yêu cầu đọc 4 byte dữ liệu (noData, DATA0, DATA1, CRC) - (noData không phải byte dữ liệu)

BƯỚC 4: Tính toán và kiểm tra CRC. CRC là kết quả của DATA0 XOR DATA1 [24, Bảng 5]

BƯỚC 5: Chuyển đổi dữ liệu thành giá trị áp suất
- Ghép 2 byte dữ liệu thành giá trị 16 bit (kPa * 10)
- Ép kiểu thành số nguyên có dấu 16 bit (Signed Short Int) để xử lý áp suất âm (nếu có, ví dụ AGR12xxPxx hoặc AGR12xxNxx)
- Chia cho 10.0 để có giá trị áp suất thực tế (kPa)

BƯỚC 6: Hiển thị kết quả

# Code em Long
### I2C_AGR12_Pressure_Sensor_Uno_LONG
_Chương trình chạy với tần số 50kHz, lặp lại mỗi 1 giây 1 lần._

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

Kết quả
```
Khoi tao cam bien AGR12 I2C voi toc do 50 kHz...
Khoi tao cam bien AGR12 I2C...
count: 3
0x0 0xE2 0xE2
CRC Uno tinh la: 0xE2
Ap suat: 22.6 kPa
count: 3
0x0 0xE3 0xE3
CRC Uno tinh la: 0xE3
Ap suat: 22.7 kPa
count: 3
0x0 0xE5 0xE5
CRC Uno tinh la: 0xE5
Ap suat: 22.9 kPa
count: 3
0x0 0xE6 0xE6
CRC Uno tinh la: 0xE6
Ap suat: 23.0 kPa
```

### I2C_AGR12_Pressure_Sensor_ESP32_LONG
_Chương trình chạy với tần số 10kHz, lặp lại mỗi 1 giây 1 lần. Thống nhất dùng mạch chuyển mức tín hiệu riêng cho mọi mạch ESP32_
_Chỉnh sửa phần in dữ liệu lên Serial Monitor tương tự với I2C_AGR12_Pressure_Sensor_Uno_LONG_
Kết quả
```
Loi CRC! Du lieu khong hop le. CRC nhan: FF, CRC tinh: 80
0x7F 0xFF 0xFF
CRC Uno tinh la: 0x80
Ap suat: 3276.7 kPa
Guru Meditation Error: Core  1 panic'ed (StoreProhibited). Exception was unhandled.

Core  1 register dump:
PC      : 0x40085c4b  PS      : 0x00060033  A0      : 0x80082df8  A1      : 0x3ffbfb0c  
A2      : 0x3ffb8e5c  A3      : 0x00000001  A4      : 0x3ffb928c  A5      : 0x3ffb8eb0  
A6      : 0x3ffb8f5c  A7      : 0x3ffbfb28  A8      : 0x00000000  A9      : 0x00000001  
A10     : 0x0000007f  A11     : 0x3ff53000  A12     : 0x00000000  A13     : 0x00000000  
A14     : 0x00000000  A15     : 0x0000abab  SAR     : 0x00000000  EXCCAUSE: 0x0000001d  
EXCVADDR: 0x00000000  LBEG    : 0x40085230  LEND    : 0x4008523b  LCOUNT  : 0xffffffff

Backtrace: 0x40085c48:0x3ffbfb0c |<-CORRUPTED

E (3380) i2c.master: I2C software timeout
E (3380) i2c.master: s_i2c_synchronous_transaction(945): I2C transaction failed
E (3380) i2c.master: i2c_master_receive(1268): I2C transaction failed
```

Sửa Wire.setClock(10000), Vietduino ESP32 chạy ổn định hơn, và đã đọc được toàn bộ dữ liệu: 
```
count=3
0x0 0xB0 0xB0
CRC Uno tinh la: 0xB0
Ap suat: 17.6 kPa
count=3
0x0 0xAD 0xAD
CRC Uno tinh la: 0xAD
Ap suat: 17.3 kPa
count=3
0x0 0xA9 0xA9
CRC Uno tinh la: 0xA9
Ap suat: 16.9 kPa
count=3
0x0 0xAB 0xAB
CRC Uno tinh la: 0xAB
Ap suat: 17.1 kPa
count=3
0x0 0xCA 0xCA
CRC Uno tinh la: 0xCA
Ap suat: 20.2 kPa
count=3
0x0 0xD0 0xD0
CRC Uno tinh la: 0xD0
Ap suat: 20.8 kPa
count=3
0x0 0xD1 0xD1
CRC Uno tinh la: 0xD1
Ap suat: 20.9 kPa
```