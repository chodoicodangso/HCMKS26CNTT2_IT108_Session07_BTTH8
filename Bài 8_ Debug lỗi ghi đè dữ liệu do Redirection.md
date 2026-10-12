## 1\. Phân tích lỗi

**Dòng gây lỗi:** Cả 3 dòng lệnh chứa Out-File weekly\_errors.txt.  
**Nguyên nhân:** Lệnh Out-File mặc định sẽ **ghi đè** (xóa dữ liệu cũ).  
**Kết quả:** File chỉ còn lại dòng cuối cùng \--- Ket thuc quet \---.

## 2\. Giải pháp & So sánh

Sửa script bằng cách thêm tham số \-Append:  
"\[\$(Get-Date)\] \--- Bat dau quet \---" | Out-File \-Append weekly\_errors.txt  
Select-String \-Path app.log \-Pattern "error" | Out-File \-Append weekly\_errors.txt  
"\[\$(Get-Date)\] \--- Ket thuc quet \---" | Out-File \-Append weekly\_errors.txt

| Lệnh | Hành vi | Kết quả |
| :---- | :---- | :---- |
| Out-File | Ghi đè | Mất dữ liệu cũ |
| Out-File \-Append | Ghi nối | Giữ dữ liệu cũ |
| Add-Content | Ghi nối | Giữ dữ liệu cũ (nhanh hơn) |

