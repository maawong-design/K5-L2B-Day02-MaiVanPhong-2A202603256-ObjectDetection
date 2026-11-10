# Mini Guideline - MaiVanPhong - 2A202603256

## Định nghĩa lớp
- 0 car: xe con, sedan, SUV, taxi, xe bán tải.
- 1 truck: xe tải chở hàng, xe đầu kéo.
- 2 bus: xe buýt, minibus chở khách.
- 3 van: van/minivan chở hàng hoặc chở người.

## Quy tắc vẽ box
- Box bám sát phần nhìn thấy của xe, không để dư nền.
- Xe đỗ vẫn gán; xe bị che một phần vẫn gán nếu đủ để nhận lớp.
- Xe bị cắt ở mép khung: gán phần nhìn thấy nếu còn nhận ra được lớp.
- Xe rất nhỏ ở xa không gán (diện tích box dưới 0.1% ảnh; dưới 0.3% ảnh
  nếu nằm ở 25% phía trên của ảnh).

## Ca mơ hồ
1. car hay van: xe thân cao dạng hộp, nhìn xa hoặc nhìn chéo thì giống nhau.
   - Quyết định: gán van khi thấy rõ thân xe cao, phần đuôi dạng hộp vuông
     hoặc có dạng xe chở người/chở hàng cỡ lớn; nếu không thấy rõ các đặc
     điểm này thì gán car (lớp phổ biến hơn).
   - Lý do: nhìn từ camera trên cao và từ xa, hai loại rất dễ nhầm; quy tắc
     mặc định về car giúp gán nhất quán giữa các ảnh.
2. Xe bị cắt ở mép khung nên chỉ thấy một phần, khó nhận ra lớp.
   - Quyết định: gán nếu phần nhìn thấy đủ để nhận ra lớp, vẽ box ôm phần
     nhìn thấy; nếu chỉ thấy một mảng nhỏ không phân biệt được thì bỏ.
   - Lý do: tránh đoán lớp khi thiếu thông tin, đồng thời không bỏ sót xe
     thấy rõ ở rìa ảnh.
3. Xe nhỏ ở xa: ban đầu tôi gán tất cả, nhưng khi so với gold thì thừa rất
   nhiều box (1778 box so với 653 của gold).
   - Quyết định: đặt ngưỡng diện tích như trên.
   - Lý do: giảm box thừa. Lưu ý: ngưỡng được chọn bằng cách dò theo điểm so
     với gold, không hoàn toàn từ quan sát ảnh.

## Ghi chú về ID lớp
Nhãn ban đầu có ID lớp lệch so với gold. Tôi phát hiện khi so với gold và sửa
bằng ánh xạ 1->2, 2->3, 3->1. Nguyên nhân chưa xác nhận.