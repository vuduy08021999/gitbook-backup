# Các biến toàn cục

## Giới thiệu

Biến toàn cục là biến có thể truy cập tại bất kỳ đâu trong react native, chính vì vậy sẽ có một số điểm rủi ro chính sau:

* Dễ bị tấn công từ code ngoài (vì khai được từ thẻ js file xml)
* Dễ bị xung đột tên với các tên biến
* Khó bảo trì, debug, vì khi nó được gọi mà gây ra lỗi, chương trình không biết được lỗi gì, gọi ở đâu

## Mục đích tài liệu

Cung cấp cho dev danh sách các biến toàn cục và cách sử dụng của các biến này nhằm mục đích:

* Tránh đặt tên biến trùng tên với biến toàn cục
* Biết được biến toàn cục được dùng như thế nào, để khi có lỗi phát sinh có thể debug ra

## Vị trí biến toàn cục

Toàn bộ biến toàn cục được đặt tại file App.js (file đầu tiên của chương trình)

## Danh sách biến toàn cục

AAlert, ALoading, ABottomButton, APopupNotification, backAction
