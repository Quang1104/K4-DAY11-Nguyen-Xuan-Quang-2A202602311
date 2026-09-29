# Quan sát vạch ô đỗ

- Hai vạch `parking_line` đã vẽ (mô tả vị trí trong ảnh): các vạch chia ô đỗ chéo, rõ ở dải foreground phía dưới trái
  và phía dưới phải; chúng kéo từ mép dưới ảnh lên khu vực mặt bằng đỗ xe ở giữa ảnh.
- Một vạch/dấu sơn hoặc biên **không** vẽ, và vì sao: đường ngang phía xa/biên mép bãi và các vệt sáng trên mặt đường
  không được vẽ vì không phải vạch chia ô đỗ nhìn thấy được.
- Polygon `free_space` dừng ở đâu; có phần bị che nào không: polygon chỉ bao phần nền bãi đỗ trống nhìn thấy rõ giữa
  các vạch ô, dừng trước xe màu đỏ và không lấn sang vạch đỗ, lề/biên xa hoặc vùng không nhìn rõ. Xe đỏ là phần bị
  che nên không được tính vào free space.
- Ca chưa chắc cần hỏi người soát (nếu không có, ghi “không có”): không có; các vệt nghi ngờ ở phía xa được loại vì
  không đủ rõ để khẳng định là vạch chia ô đỗ.
