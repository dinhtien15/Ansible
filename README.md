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
- Playbooks : Là nơi khai báo các kịch bản để chạy cho các server. Trong playbooks sẽ chứa một tập hợp các activities hay các tasks sẽ được chạy trên một hay một nhóm server
- Tasks : Là những công việc nhỏ trong Playbooks. Nếu đổi chỗ thứ tự các tasks thì sẽ gây ảnh hưởng nếu những tasks đó có liên quan với nhau. Vậy nên chú ý viết thứ tự các nhiệm vụ trong tasks
- Inventory : Khai báo địa chỉ server cần được setup, đây là nơi chứa tên các server hay địa chỉ mà mình muốn thực thi.
- Modules : Những chức năng cho việc thực thi task dễ dàng và đa dạng. Một vài module thường dùng : Commands,files,firewalld,system,... người dùng có thể viết các module của riêng họ. Module có thể được thực thi trực tiếp trên máy chủ từ xa hoặc thông qua playbooks
- 
