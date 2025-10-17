## 1. Phương pháp quy hoạc động
Phương pháp thiết kế thuật toán theo kiểu dưới lên (Bottom-up).
Xuất phát từ bài toán nhỏ quy hoạch dần dần để giải các bài toán to dần, kết quả bước sau dựa trên kết quả của bước trước
Xây dựng các biểu thức truy hồi

VD lát gạch: cho n viên gạch mỗi viên 1x2 lát sân 2 X n -> đếm số cách lát

Đặt Cn là số cách lát 2 * n
C1=1 |
C2=2 || =
C3=3 ||| =| |=
C4=5 
-> dãy fibonaci

**vd2** Leo thang
Cho n bậc thâng bước 1,2,3 bậc đếm số cách
ý tưởng: Đặt Cn là số cách leo thang
Ta có C1=1       1
	 C2=2        11 2
	 C3=4        111 12 21 3
	 C4=7        1111 22 211 121 112
	 C5=13

VD Cắt ruybang
số catalan Cn=C1* Cn-1+C2* Cn-2+....+Cn-1* C1

Một số bài toán khác
a, dãy con liên tục có tổng lớn nhất
BT cho n, a1,..., an tìm tổng dãy con liên tục có tổng lớn nhất

đổi tiền: tham lam3332213213213213=












