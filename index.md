# Runge-Kutta

[Tải code tại đây.](https://github.com/anhnb206110/Runge_Kutta/archive/refs/heads/main.zip)

# **Hướng dẫn sử dụng**

## Yêu cầu:

 - Có cài đặt Python3 (3.8.10 hoặc mới hơn, khuyến khích cài từ python.org)
 - Có cài đặt các thư viện cần thiết (**`numpy, sympy, matplotlib`**)
  
## Cài đặt thư viện

Chạy 1 trong 2 lệnh:

```bash
  pip install numpy sympy matplotlib
  pip install numpy==1.19.3 sympy==1.8 matplotlib==3.3.3
```

## Các bước chạy chương trình

> **Phải để các file cùng thư mục vì chúng có liên kết với nhau.**

Sau khi cài đặt Python3 và đầy đủ thư viện, chạy **`app.py`**, nhập các đầu vào cần thiết và bấm **`Solve and plot`**.

Các giá trị đầu vào bao gồm:
 1. Biểu thức hàm f(x,y). Ví dụ nhập: exp(x) + cos(x^2) - 1/x + y + x**2
 2. Điểm bắt đầu `a`, điểm kết thúc `b`, giá trị ban đầu `y0`, bước lưới `h`.
 3. Các công thức R-K để giải (bằng các số được liệt kê) hoặc dùng phương pháp Fehlberg bằng cách tick vào checkbox.
 4. Nghiệm chính xác nếu muốn so sánh với kết quả đúng.

Các file cũng có thể chạy riêng lẻ, đầu vào cũng tương tự như trên. Kết quả trả về được lưu ở thư mục `output` cùng đường dẫn tới các file.

### `runge_kutta.py`:

  - Giải ODE cấp 1 trong không gian 1 chiều (y' = f(x,y))

### `adaptive.py`:

  - Giải ODE cấp 1 trong không gian 1 chiều (y' = f(x,y)) bằng phương pháp Fehlberg với sai số mong muốn eps. Với eps, hmin, hmax là tùy chọn (có giá trị mặc định nếu không nhập), nếu nhập thì phải đủ, đúng thứ tự.

### `systemofODEs.py`:

  - Giải hệ x' = f(t,x) (x là vector trong $\mathbb{R}^k$), t0 <= t <= tf, bước lưới dt.
  - Đối với hệ 1,2,3 phương trình, nhập theo thứ tự các hàm x',y',z' biến t (hệ 1 chỉ cần nhập f, hệ 2 phương trình chỉ cần nhập f,g).
  - Với nhiều hơn 3 phương trình trong hệ, sửa hàm `f(t,x)` của file `systemofODEs.py` ở dòng 30,31,... theo hướng dẫn được viết trong hàm, phải tự đổi biến hàm thành x[0],x[1],... ẩn t.
    Hệ 2 phương trình thì viết ở 2 dòng 30 31,hệ 3 phương trình 30 31 32,... (Có dấu phẩy cuối dòng)

    Minh họa:

```py
14  def f(t,x) -> np.array:
15      """..."""
28      return np.array([
29                        # Sửa return ở dòng dưới này
30                        x[1],
31                        t + x[0] + x[1],
32
33      ])
```

  - Lưu file sau đó chạy file, nhập input theo yêu cầu gồm t0,tf,dt, giá trị ban đầu của hệ x_0(t0),x_1(t0),x_2(t0),...
    Minh họa:

```
PS D:\> python systemofODEs.py

 Enter start point (t0), end point (tf), step (dt)
 t0 tf dt: 0 40 0.05

 Enter 2 init value(s): 50 20 
```

  - Trong trường hợp hệ 2 hoặc 3 phương trình, bấm `2nd Plot` để xem thêm đồ thị khác.

# Ví dụ

## ODE cấp 1

![image](https://user-images.githubusercontent.com/89454092/150267139-77bfb540-c1f3-4318-8808-6ea5ff8c14b8.png)

## ODE cấp 2 và hệ phương trình

![image](https://user-images.githubusercontent.com/89454092/150267169-fb3ef2dd-730b-420e-815f-dd5965465d46.png)
