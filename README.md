Hướng dẫn cài đặt
```
IP Planning
Hostname		OS			IP
AnsibleServer		Centos7			.....
Client1			Centos7			192.168.80.124
Client2			Centos7			192.168.80.125
Client3			Centos7			192.168.80.12
```

B1. Cài đặt Ansible trên node Ansible Server
```
yum install -y epel-release 
yum update -y
yum install -y ansible
```
B2. Cấu hình SSH Key
Đứng tại user root của node AnsibleServer và thực hiện bước tạo key: 
```
ssh-keygen
```
Thực hiện các thao tác Enter và để mặc định các tùy chọn
```
Generating public/private rsa key pair.
Enter file in which to save the key (/root/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /root/.ssh/id_rsa.
Your public key has been saved in /root/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:ialESG10iMjC8ppgMWh46DaB34s7iuFwbUCB6a0FDP4 root@ansibleserver
The key's randomart image is:
+---[RSA 2048]----+
|X=o+...          |
|%@oo+.           |
|*=Oo.            |
|.B++.  o .       |
|+o=E..o S        |
|o..+..           |
|o ..+            |
|+oo.             |
|oo .             |
+----[SHA256]-----+
```
Thực hiện copy file key sang các node còn lại: ssh-copy-id root@[ip lần lượt của các client]

B3. Tạo và khai báo file inventory.ini
Bình thường sẽ tạo file dạng như này: 
```
[solrcloud]
client1 ansible_host=192.168.80.124 ansible_port=22 ansible_user=root
client2 ansible_host=192.168.80.125 ansible_port=22 ansible_user=root
client3 ansible_host=192.168.80.126 ansible_port=22 ansible_user=root
```
Nhưng do trong phần cài đặt này gồm cả file j2 nên sẽ viết theo cách ở dưới để thuận tiện cho việc file j2 chạy
```
[solrcloud]
192.168.80.124
192.168.80.125
192.168.80.126
```


B4. Sử dụng một số lệnh kiểm tra cơ bản 
Để xem bạn đã khai báo đúng chưa 
```
ansible all -m ping
```

-> trả lại đủ số client bạn đã khai báo với màu xanh lá cây thì ok
-> không trả lại đủ số client với chữ màu đỏ thì ktra lại

B5. Tạo 2 file j2 có tên myid.j2 và zoo.cfg.j2 ở bên trên trong đường dẫn /root/ vì mình viết playbook ở đường dẫn này

B6. Chạy playbook với lệnh
```
ansible-playbook -i inventory.ini playbook.yml
```



