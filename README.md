Đồng bộ hóa thời gian trong OpenWrt bằng cách lấy dữ liệu thời gian từ miền đã chọn.

Hỗ trợ đồng bộ thời gian khi có kết nối modem/internet.

Trình kiểm tra kết nối (nếu sử dụng chế độ cron, tập lệnh sẽ kiểm tra kết nối, sau đó khởi động lại ứng dụng VPN nếu không có kết nối internet)

Cài đặt múi giờ tự động tuân theo LuCI - System - System - Timezone.

Hỗ trợ cài đặt múi giờ cho VPN: OpenClash ,Passwall, ShadowsocksR, ShadowsocksR++, V2ray, V2rayA, Xray, Libernet, Xderm Mini, Wegare STL

Sử dụng mặc định - Sử dụng cơ bản

Cài đặt các gói yêu cầu trước bằng cách mở terminal:
opkg update && opkg install curl wget

Dán lệnh bên dưới để cài đặt tập lệnh time_open_wrt: 
wget --no-check-certificate "https://raw.githubusercontent.com/huytran123/update_time_wrt/main/time_open_wrt" -O /usr/bin/time_open_wrt && chmod +x /usr/bin/time_open_wrt

Nhập lệnh bên dưới vào LuCI -> System -> Startup -> Local Startup: 
1. Ví dụ dùng mạng Viettel: /usr/bin/time_open_wrt m.tv360.vn

Nhập lệnh bên dưới vào LuCI -> System -> Scheduled Tasks để auto restart VPN và cập nhật giờ đc lặp lại trong 1 giờ:
1. Ví dụ dùng mạng Viettel: 0 * * * * /usr/bin/viet m.tv360.vn cron

Nhập lệnh bên dưới vào LuCI -> System -> Scheduled Tasks để auto restart router lúc 3h sáng:
1. Ví dụ dùng mạng Viettel: 0 3 * * *  /bin/sh -c "reboot"
