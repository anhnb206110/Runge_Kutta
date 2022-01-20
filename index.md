# **Hướng dẫn sử dụng**

## Yêu cầu:

 - Có cài đặt Python3 (3.9.0 hoặc mới hơn)
 - Có cài đặt các thư viện cần thiết (`numpy, sympy, matplotlib`)
  
## Cài đặt thư viện

Chạy 1 trong 2 lệnh:

```bash
  pip install numpy sympy matplotlib
  pip install numpy==1.19.3 sympy==1.8 matplotlib==3.3.3
```

## Các bước chạy chương trình

> **Phải để các file cùng thư mục vì chúng có liên kết với nhau.**

### `runge_kutta.py`:

>>  Giải ODE cấp 1 trong không gian 1 chiều (y' = f(x,y))

Các bước:
  - B1: Chạy file.
  - B2: Nhập input gồm hàm f(x,y) (dấu mũ: ^ hoặc **, e^x là exp(x)), điểm đầu a, điểm cuối b, bước đều h (cho phép nhiều h)

    Minh họa:
    
```
PS D:\> python runge_kutta.py

 Enter equation:
 y' = exp(x) + cos(x^2) - 1/x + y - 2

 Init value a <= x <= b, y(a) = y0
 Enter a b y0 h (allow more than one h): 1 1.5 1 0.1

 :--- R-K: {0:'RK1', 1: 'RK2', 3: 'RK3', 5:'RK4 Classic'}
 '-------> Select (Ex 1 3, no input = all): 0 3

 Exact solution (no input = skip) y(x) = 
 Press 'Enter' to plot
```

  - B3: Chọn công thức RK để giải từ danh sách được liệt kê bằng các số như: 0 3
  - B4: Kết quả được lưu ở thư mục `output` với tên `table.txt` và `graph.png`


### `adaptive.py`:

>>  Giải ODE cấp 1 trong không gian 1 chiều (y' = f(x,y)) bằng phương pháp Fehlberg

Các bước:
  - Tương tự như `runge_kutta.py`. Nhập từ bàn phím hàm f, giá trị a,b,y0,h0.
  - eps, hmin, hmax là tùy chọn (có giá trị mặc định nếu không nhập), nếu nhập thì phải đủ, đúng thứ tự.

    Minh họa:

```
PS D:\> python adaptive.py

 Enter equation:
 y' = -200y

 Init value: a <= x <= b, y(a) = y0
 Enter a b y0 h0 (eps hmin hmax): 0 0.3 1 0.1

 Exact solution (no input = skip) y(x) = exp(-200x)
```

### `systemofODEs.py`:

>>  Giải hệ x' = f(t,x), t0 <= t <= tf, bước lưới dt
  
  Nhập từ bàn phím hệ nhiều phương trình dễ gây sai sót và phải nhập lại từ đầu, tốc độ chậm khi xử lý từ văn bản thành hàm
  => Sửa trực tiếp hàm `f(t,x)` trong file `systemofODEs.py`.
Các bước:
  - B1: Sửa hàm `f(t,x)` ở dòng 28,29,... theo hướng dẫn được viết trong hàm, phải tự đổi biến hàm thành x[0],x[1],... ẩn t.
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

  - B2: Lưu file sau đó chạy file, nhập input theo yêu cầu gồm t0,tf,dt, giá trị ban đầu của hệ x_00,x_10,x_20,...

    Minh họa:

```
PS D:\> python systemofODEs.py

Enter start point (t0), end point (tf), step (dt)
t0 tf dt: 0 40 0.05

Enter 2 init value(s): 50 20 
```

  - Kết quả thu được ở thư mục `output` với file là `system.txt,systemSolution.png`

# Ví dụ

## ODE cấp 1

![image](https://user-images.githubusercontent.com/89454092/150267139-77bfb540-c1f3-4318-8808-6ea5ff8c14b8.png)

## ODE cấp 2 và hệ phương trình

![image](https://user-images.githubusercontent.com/89454092/150267169-fb3ef2dd-730b-420e-815f-dd5965465d46.png)
