# Ansible
Báo cáo tìm hiểu Ansible
Ansible là gì?
- Là 1 platform open source giúp giảm thiểu việc phải thao tác cài đặt giống nhau trên nhiều VPS
- VD có 10 VPS cần cài Python thay vì truy cập vào từng VPS và gõ lệnh cài , ta chỉ cần cấu hình và đứng ở Ansible server gửi lệnh cài Python lên 10 VPS đó

Hoạt động : Mình sẽ đứng trên 1 node control hay thường được đặt là Ansible server và ra lệnh cho các server mà mình quản lý
- Gửi các lệnh cài đặt đến một cụm các server được khai báo trong /etc/ansible/hosts, tuy nhiên vấn đề đặt ra số lượng thao tác cần thực hiện lớn , không thể gõ tay nhiều lệnh
- Khi đó cần viết 1 playbooks - chứa tất cả những gì muốn làm với các server từ xa kia , mỗi thao tác trong playbooks được gọi là 1 task(setup, start,stop,..), sử dụng các module để tạo thành task ( ví dụ muốn cài đặt 1 gói trên centos7 ta sdung module yum)
- giờ ta cần truyền thông tin chi tiết hơn về server cho Playbook chứ không thì làm sao nó biết sẽ làm việc với ai. Lúc này ta cần đến Inventory.
- Iventory giúp khai báo chi tiết các server mà mình sẽ quản lý và làm việc cùng

Tại sao nên sử dụng :
- là 1 open source
- chạy bằng phương thức ssh
- cài đặt không tốn nhiều tài nguyên
- Script thường được dùng định dạng YAML
- Cộng đồng tương tác lớn

Các thành phần trong Ansible 
- Playbooks : Là nơi khai báo các kịch bản để chạy cho các server
- Tasks : Là những công việc nhỏ trong Playbooks
- Inventory : Khai báo địa chỉ server cần được setup
- Modules : Những chức năng cho việc thực thi task dễ dàng và đa dạng
