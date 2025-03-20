# 🛠 Hệ Thống STM32F4 Kết Nối EtherCAT Qua FSMC 🚀

## 📌 Tổng Quan
Dự án này bao gồm **hai bo mạch** kết nối với nhau, sử dụng **STM32F4** để giao tiếp với một bo mạch chính hỗ trợ **EtherCAT**. Hệ thống này được thiết kế phục vụ các ứng dụng **tự động hóa công nghiệp, thu thập dữ liệu tốc độ cao và điều khiển thời gian thực**.

---

## 🔧 Cấu Trúc Hệ Thống
### 🟢 1. Bo Mạch Điều Khiển (bai12.pdf & bai122.pdf)
#### ✨ **Thành Phần Chính:**
- 🎛 **Vi điều khiển:** STM32F407ZGT6 – Đóng vai trò điều khiển chính.
- 🔋 **Nguồn điện:** AMS1117-3.3V – Chuyển đổi 5V từ USB thành 3.3V cấp cho vi điều khiển.
- 🖲 **Nút nhấn (SW1 → SW8):** 8 nút nhấn với điện trở pull-down, dùng để nhập lệnh hoặc điều khiển.
- 💡 **LED chỉ báo (LED1 → LED10):** Giúp hiển thị trạng thái hoạt động.
- 🔗 **Giao tiếp FSMC:**
  - Địa chỉ: FSMC_A0 → FSMC_A15
  - Dữ liệu: FSMC_D0 → FSMC_D15
  - Điều khiển: FSMC_NE, FSMC_NWE, FSMC_NOE
- 🔌 **Cổng USB:** Dùng để cấp nguồn hoặc truyền dữ liệu.
- 🔄 **Các tín hiệu FSMC mở rộng:**
  - Địa chỉ: FSMC_A0 → FSMC_A12
  - Dữ liệu: FSMC_D0 → FSMC_D15
  - Điều khiển: FSMC_NE4, FSMC_NWE, FSMC_NOE

#### 🏗 **Thiết Kế Mạch:**
✔️ **STM32F4 giao tiếp với bo EtherCAT thông qua FSMC** để đảm bảo tốc độ truyền dữ liệu cao.
✔️ **Tụ lọc nhiễu 0.1µF và 10µF** giúp đảm bảo nguồn sạch.
✔️ **Các chân GPIO được mở rộng**, có thể lập trình thêm.

---

### 🟠 2. Bo Chính EtherCAT (bai123.pdf)
#### ✨ **Thành Phần Chính:**
- 🌐 **Ethernet PHY:** HR911105A – Kết nối mạng Ethernet.
- ⚡ **Bộ điều khiển EtherCAT:** AX58100LT – Xử lý giao tiếp EtherCAT.
- 🗄 **EEPROM AT24C32:** Lưu trữ cấu hình thiết bị.
- ⏱ **Thạch anh 25MHz:** Đảm bảo thời gian chính xác.
- 🔋 **Nguồn nhiều mức (3.3V, 1.2V):** Hỗ trợ các mức logic khác nhau.

#### 🏗 **Thiết Kế Mạch:**
✔️ **AX58100LT giao tiếp với STM32F4 thông qua FSMC**.
✔️ **HR911105A xử lý kết nối Ethernet**.
✔️ **EEPROM AT24C32 được điều khiển qua I2C**.
✔️ **Các bộ lọc EMI và điện trở pull-up giúp ổn định tín hiệu**.

---

## 🔄 **Cách Kết Nối Giữa Các Mạch**
- 📌 **Bo điều khiển STM32F4** kết nối trực tiếp với **bo chính EtherCAT** qua **FSMC**.
- 📡 **STM32F4 truyền dữ liệu đến AX58100LT**, bộ điều khiển này xử lý giao tiếp EtherCAT.
- ⚡ **Ethernet PHY HR911105A** đảm bảo truyền dữ liệu qua mạng.

---

## 🎯 Chức Năng Chính
✅ **STM32F4** đóng vai trò điều khiển trung tâm.
✅ **FSMC kết nối tốc độ cao giữa STM32F4 và EtherCAT**.
✅ **Bo chính với AX58100LT hoạt động như một thiết bị EtherCAT Slave**.
✅ **Hỗ trợ thu thập dữ liệu, điều khiển tự động hóa**.
✅ **USB có thể dùng để cập nhật firmware hoặc cấp nguồn**.

---

## 🚀 Ứng Dụng
- 🏭 **Tự động hóa công nghiệp:** Điều khiển EtherCAT.
- 🤖 **Hệ thống PLC & Robot:** Giao tiếp với thiết bị ngoại vi.
- ⚡ **Xử lý dữ liệu tốc độ cao:** Giao tiếp song song qua FSMC.
- 🔬 **Phát triển hệ thống nhúng:** Thiết kế mô-đun dễ mở rộng.

---

## 📂 Nội Dung Kho Lưu Trữ
📜 `bai12.pdf & bai122.pdf` – Sơ đồ bo điều khiển STM32F4.
📜 `bai123.pdf` – Sơ đồ bo chính với EtherCAT.
📜 `PCB Layout Files` – File thiết kế Altium.
📸 **Hình ảnh thiết kế:**
- 🔼 **Mặt trên bo điều khiển**
- 🔽 **Mặt dưới bo điều khiển**
- 🎨 **Hình ảnh 3D bo điều khiển**
- 📏 **Layout PCB bo điều khiển**
- 🔼 **Mặt trên bo EtherCAT**
- 🔽 **Mặt dưới bo EtherCAT**
- 🎨 **Hình ảnh 3D bo EtherCAT**
- 📏 **Layout PCB bo EtherCAT**

---

## 🛠 Hướng Dẫn Bắt Đầu
1️⃣ **Clone repository**
   ```sh
   git clone https://github.com/your-repo/STM32F4-FSMC-EtherCAT.git
   ```
2️⃣ **Mở bằng Altium Designer** 📐
   - Load `bai12.SchDoc`, `bai122.SchDoc`, `BUOI13.SchDoc`.
   - Kiểm tra thiết kế PCB và tối ưu đường mạch.
3️⃣ **Lập trình firmware (tùy chọn)**
   - Cấu hình **FSMC trên STM32F4** để giao tiếp với bo chính.
   - Lập trình giao tiếp **EtherCAT với AX58100LT**.

---

## 🔮 Kế Hoạch Mở Rộng
✨ Thêm giao diện **SPI/I2C** cho cảm biến.
✨ Viết firmware mẫu cho **STM32F4**.
✨ Tối ưu quản lý **nguồn tiêu thụ thấp**.

---
