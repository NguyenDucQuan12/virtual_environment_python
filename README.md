# virtual_environment_python
Tất cả thông tin về làm việc môi trường ảo ở python mà mình tích lũy được  

### Đặt thư mục ảo nên có chữ `venv` để dễ nhận biết, ví dụ: `venv`, `Camera_venv`  


## Tạo môi trường ảo với `Visual studio code`  

Tạo một thư mục để chứa dự án code: ví dụ `Work_with_camera`    

Mở `Visual studio code` --> `Add folder to workspace` --> add `Work_with_camera`--> Chọn `Yes`  

<img src="https://github.com/user-attachments/assets/cea6056d-ee33-484a-b9c5-450689c9cf92">  

Sau đó ta có các thư mục sẽ chứa code nằm bên phải:  

<img src="https://github.com/user-attachments/assets/7200d931-b581-4c67-8c9f-ae51598fcc71">  

`Mở Terminal của thư mục Work_with_camera và thực hiện các câu lệnh từ bước sau bằng termial`  

<img src="https://github.com/user-attachments/assets/16cb182c-fc8d-4c9a-ad37-47698c5ffa58">  

Bước 1: Tạo môi trường ảo `venv` bên trong thư mục `Work_with_camera`:  
Trong đó `venv_project` là tên thư mục chứa môi trường ảo, `"venv camera"` sẽ là tên hiển thị khi kích hoạt môi trường ảo
```
python -m venv venv_project --prompt="venv camera"
```  

<img src="https://github.com/user-attachments/assets/73348eff-7aea-4b2c-a34c-8c811d0e0674">  

### Cách phía trên sẽ áp dụng phiên bản python mặc định của máy vào thư mục ảo  

Để cài một phiên bản python khác ta sử dụng cách sau:  
+ Đầu tiên cần tải cài 1 phiên bản python khác từ trang chủ python (khi cài đặt nhớ tích vào ô add PATH ...)
+ Chạy lệnh phía dưới để liệt kê danh sách các phiên bản `python` đã cài trên máy  
```
py --list
```

<img src="https://github.com/user-attachments/assets/4d42b085-11d6-4b0e-91b5-4abf9d72c464">  

Chạy lệnh sau để cài phiên bản python cụ thể, ví dụ với `python 3.12`:  
```
py -3.12 -m venv .project_1 --prompt="project1_312"
```
```
Để check phiên bản đang cài thì chỉ cần kích hoạt môi trường ảo và chạy lệnh  
python --version  
 
```
Ta có thể thấy, trên máy có 2 phiên bản python đó là `python 3.12` và `python 3.10`, sau đó ta kiểm tra phiên bản python hiện tại thì nhận được kết quả là `python 3.10`  
Sau khi cài đặt môi trường ảo và kích hoạt môi trường ảo và check lại thì nhận được kết quả là `python 3.12`, vậy là đã thành công  
<img src="https://github.com/user-attachments/assets/0be1bbc9-a43f-45cf-aacd-31cf494d187e"> 

Bước 2: Kích hoạt môi trường ảo bằng `terminal` bằng cách vào thư mục `venv_project/Scripts` và copy đường dẫn `activate`:  

<img src="https://github.com/user-attachments/assets/2d1b0ac0-b1b0-4838-b73a-202c0e7c202a">  

```
venv_project\Scripts\activate  
```

<img src="https://github.com/user-attachments/assets/24b331ec-e8b9-4f15-9952-7c87d970ebe0">  

Nếu mà không kích hoạt được ở `terminal` khi gặp lỗi như hình ảnh bên dưới:  
```
.project_1\Scripts\activate : File D:\Dự án\Python312\.project_1\Scripts\Activate.ps1 cannot be loaded because running scripts is disabled on this system. For more information, see about_Execution_Policies at 
https:/go.microsoft.com/fwlink/?LinkID=135170.
At line:1 char:1
+ .project_1\Scripts\activate
+ ~~~~~~~~~~~~~~~~~~~~~~~~~~~
    + CategoryInfo          : SecurityError: (:) [], PSSecurityException
    + FullyQualifiedErrorId : UnauthorizedAccess
```

<img src="https://github.com/user-attachments/assets/7bfcf901-177d-44d3-8ef0-86c673ba0d69">  

thì cần chạy lệnh này trước khi chạy lại lệnh trên:  
```
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser  
```

Bước 3: Cài đặt các thư viện cần thiết:  

```
python -m pip install -r requirements.txt  
```

Nếu có chỉnh sửa, thay đổi thư viện thì thêm vào file bằng câu lệnh sau:  

```
python -m pip freeze > requirements.txt
```

Nếu xuất hiện lỗi: `pip: Fatal error in ...` thì chạy 2 lệnh sau để khắc phục lỗi:  

```
python -m pip install --upgrade --force -reinstall pip  
python -m pip freeze  
```

## Lỗi khi import thư viện
### Khi import một số thư viện vào môi trường ảo thường sẽ gặp lỗi `Import "newlibrary" could not be resolved`, tuy nhiên code vẫn hoạt động bình thường, lỗi xuất hiện nhìn khó chịu, vì vậy cần sửa như sau:  

<img src="https://github.com/NguyenDucQuan12/virtual_environment_python/assets/68120446/99a31ec5-2246-49f8-87a5-c4761e57f158">  

Bước 1: Mở `setting` từ màn hình `visual studio code` bằng cách nhấn `Ctrl + ,` và tìm kiếm từ khóa `pylance` và tìm đến mục `Python>Analysis: Extra Paths` rồi thêm đường dẫn thư viện của dự án đang làm việc như hình ảnh:  

<img src="https://github.com/NguyenDucQuan12/virtual_environment_python/assets/68120446/c3586623-00d8-4b88-8ec6-1ef752f6261a">  

Bước 2: Nhấn `OK` để lưu và lỗi sẽ mất nếu thư viện đó bạn đã cài bằng `pip`  

## Khi import một hàm từ file python khác như mô đun bằng đường dẫn tuyệt đối nhưng không được, còn đường dẫn tương đối thì được (không nên sử dụng đường dẫn tương đối)  
Đường dẫn tương đối là sử dụng, không nên sử dụng cách này  
```
from ....service.schemas import function  
```
Sử dụng đường dẫn tuyệt đối  

<img src="https://github.com/user-attachments/assets/57d6bdd3-18df-4656-b746-720960ead48f"> 

Để có thể nhập được đường dẫn tuyệt đối (import hàm của thư mục cha vào thư mục con)  

> Đầu tiên ta cần phải tạo một tệp tin "__init__.py" trống
> Mỗi thư mục mà chứa tệp tin cần import nó thì ta sẽ tạo tệp tin init kia (ngoại trừ thư mục gốc, hoặc thư mục chứa file main thì ko cần thêm, vì nó là gốc)

Bước 1: Chuột phải vào `This PC` chọn `Properties`  

<img src="https://github.com/user-attachments/assets/88ff0e13-76a6-4dfa-96b8-9a0a82932ff1"> 

Chọn `Advanced system settings` và vào `Enviroment Variable`  

<img src="https://github.com/user-attachments/assets/ac27406f-b126-4048-949b-cb7d3710a3a4"> 

Bước 2: Chọn `New` trong mục `System Variable` và điền thông tin như sau  
`Variable Name` sẽ là `PYTHONPATH`  
`Variable value` sẽ là đường dẫn đến dự án của bản thân  

<img src="https://github.com/user-attachments/assets/a0558238-eeb6-4ae2-beda-dd315816d1b1"> 

Sau đó mở lại visual studio code và import các hàm của thư mục khác  

<img src="https://github.com/user-attachments/assets/b0264b42-a584-4384-9d44-927e960d28ef">

# Cách debug trong môi trường ảo của python với visual studio code
Đầu tiên cần đặt `Breakpoint` tại các dòng code sinh ra rỗi, hoặc bạn nghi dòng đó có thể dẫn đến lỗi  

<img src="https://github.com/NguyenDucQuan12/virtual_environment_python/assets/68120446/bb2e8881-decd-4f57-abc9-865821f51cff">


Ví dụ ở hình ảnh phía trên là đặt `Breakpoint` ở dòng 225 bằng cách `click chuột` vào bên trái dòng 225 là được.

## Cách 1
* Mở bảng điều khiển
Nhấn `Ctrl+Shift+P` và tìm kiếm `Python: Select interpreter` như ảnh dưới:

<img src="https://github.com/NguyenDucQuan12/get_rtsp_ipcamera/assets/68120446/613483fe-14b9-4440-b795-adc6a0d5718f">


* Chọn thư mục chứa môi trường ảo và chọn phiên bản python phù hợp theo cú pháp `python x.xx.x ('name_folder':venv)`:

<img src="https://github.com/NguyenDucQuan12/get_rtsp_ipcamera/assets/68120446/72e84611-498d-44df-9875-c90a97dc83b2">  

Nếu không hiển thị môi trường ảo của bạn vừa tạo thì ấn `Enter interpreter path..` xong ấn `find` vào thư mục thoe đường dẫn `project/Scripts/python.exe` và chọn  

<img src="https://github.com/user-attachments/assets/b18b316d-0ae3-4751-ab74-95d8ead8511c">


* Xong nhấn `F5` để debug

## Cách 2  
* Thêm file `launch.json`
Nhấn vào tab `debug` bên trái và chọn mũi tên xuống dưới để thêm file `launch.json`:

<img src="https://github.com/NguyenDucQuan12/get_rtsp_ipcamera/assets/68120446/b1729e14-5f8a-470b-913d-ad4f6e276335">

 
* Chọn `add config (thư mục ảo cần debug)` và thêm dòng : `"justMyCode": false`.

<img src="https://github.com/NguyenDucQuan12/get_rtsp_ipcamera/assets/68120446/209c40aa-44d2-4806-aafb-505c0d188056">  


* Lưu lại file và nhấn 1 trong 2 lựa chọn bên dưới để debug

<img src="https://github.com/NguyenDucQuan12/virtual_environment_python/assets/68120446/dd3fae7f-113c-46f4-8203-80ffd7418a54">  


`F5 và 2 bấm nút 2 lựa chọn` sẽ cho hai kết quả khác nhau  
