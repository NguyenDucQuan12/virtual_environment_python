# virtual_environment_python
Tất cả thông tin về làm việc môi trường ảo ở python mà mình tích lũy được
### Lưu ý nên đặt thư mục ảo có dấu chấm phía trước, ví dụ: `.venv`, `.Camera_ven`  
## Tạo môi trường ảo với `Visual studio code`  
Tạo một thư mục để chứa các dự án code với tên `Venv_Python`  
Mở `Visual studio code` --> `Add folder to workspace` --> add `Venv_Python`  
<img src="https://github.com/user-attachments/assets/8523dad7-4a89-48ee-83ba-ad854a8ffd57">  

Bước 1: Tạo môi trường ảo `.camera_app` bên trong thư mục `Venv_Python`:  
`python -m venv .camera_app --prompt="venv_project1"`  
<img src="https://github.com/user-attachments/assets/115a1045-46a2-4cfc-8359-82b2f6ca23f0"> 

Cách phía trên sẽ áp dụng phiên bản python mặc định của máy vào thư mục ảo  
Để cài một phiên bản python khác ta sử dụng cách sau:  
+ Đầu tiên cần tải cài 1 phiên bản python khác từ trang chủ python (khi cài đặt nhớ tích vào ô add PATH ...)
+ Tiếp theo chạy lệnh sau để xem đã có phiên bản python đã cài chưa `py --list`
+ Chạy lệnh sau để cài phiên bản python cụ thể, ví dụ với python 3.10: `py -3.10 -m venv .project_1 --prompt="project1_310"`
<img src="https://github.com/user-attachments/assets/d73453e6-c553-42f5-b29f-ed3a2bd3a566">  

Bước 2: Kích hoạt môi trường ảo bằng `terminal` bằng cách vào thư mục `.camera_app\Scripts` và copy đường dẫn `activate`:  
<img src="https://github.com/user-attachments/assets/bf851f10-d202-41e3-b1c1-6c7f9d2d9287">

`.camera_app\Scripts\activate`  
<img src="https://github.com/NguyenDucQuan12/virtual_environment_python/assets/68120446/c9524d98-9110-4ac7-8289-654b173724d4">  

Nếu mà không kích hoạt được ở `terminal` thì cần chạy lệnh này trước khi chạy lại lệnh trên: `Set-ExecutionPolicy RemoteSigned -Scope CurrentUser`  
Bước 3: Cài đặt các thư viện cần thiết:  
`python -m pip install -r requirements.txt`  
Nếu có chỉnh sửa, thay đổi thư viện thì thêm vào file bằng câu lệnh sau: `python -m pip freeze > requirements.txt`  
Nếu xuất hiện lỗi: `pip: Fatal error in ...` thì chạy 2 lệnh sau để khắc phục lỗi:  
`python -m pip install --upgrade --force -reinstall pip`  
`python -m pip freeze`
## Khi tạo môi trường ảo, và import một số thư viện ảo hoặc import file py như một thư viện thường sẽ gặp lỗi `Import "newlibrary" could not be resolved`, tuy nhiên code vẫn hoạt động bình thường, lỗi xuất hiện nhìn khó chịu, vì vậy cần sửa như sau:  
<img src="https://github.com/NguyenDucQuan12/virtual_environment_python/assets/68120446/99a31ec5-2246-49f8-87a5-c4761e57f158">  

Bước 1: Mở `setting` từ màn hình `visual studio code` bằng cách nhấn `Ctrl + ,` và tìm kiếm từ khóa `pylance` và tìm đến mục `Python>Analysis: Extra Paths` rồi thêm đường dẫn thư viện của dự án đang làm việc như hình ảnh:  
<img src="https://github.com/NguyenDucQuan12/virtual_environment_python/assets/68120446/c3586623-00d8-4b88-8ec6-1ef752f6261a">  

Bước 2: Nhấn `OK` để lưu và lỗi sẽ mất nếu thư viện đó bạn đã cài bằng `pip`  
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
