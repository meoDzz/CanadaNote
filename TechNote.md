# SSH command

## 1. SSH agent
Khởi chạy **ssh agent** mỗi lần chạy **git bash**
```
eval "$(ssh-agent -s)"
```
## 2.Tạo **ssh key**
>Lưu ý: Nếu đã tạo **ssh key** rồi thì không cần tạo lại.

Cú pháp (Syntax):
```
ssh-keygen -t TypeOfKeyToCreate -C "comment"
```
Comment: An option to specify a comment. It’s purely informational and can be anything.

Ví dụ
```
ssh-keygen -t ed25519 -C "ledinhminhnhat1995@gmail.com"
```

Đọc thêm các argument liên quan về tạo **ssh-key**

 >https://medium.com/risan/upgrade-your-ssh-key-to-ed25519-c6e8d60d3c54
## 3. Thêm **ssh key** vào agent
```
ssh-add ~/.ssh/id_ed25519
```

## 4. Copy **ssh key** vào máy cần truy cập **ssh**
>Lưu ý: Nếu đã copy **ssh key** vào máy cần truy cập trước đó rồi, thì không cần copy lần hai.
```
ssh-copy-id -i ~/.ssh/id_ed25519 robot1
```

##
# SCP command
## Copy file từ máy này sang máy khác
```
scp -r pi@192.168.0.232:/home/pi/Desktop/StableVersion-client.zip D:/1-DocumentF
```
```
scp -r D:/1-DocumentF/LAB/3-Skin-small-zumbo/InCanada/StableVersion-PushTheBox.zip pi@192.168.0.232:/home/pi/Desktop/
```

# Permission Denied Serial (Raspberry Pi4 2Gb)

## 1. Thêm user vào *dialout group*:
```
sudo usermod -a -G dialout pi
```
Kiểm tra *user* đã được thêm vào hay chưa
```
groups
``` 
## 2. Thay đổi **enable_uart**
 ```
 sudo nano /boot/config.txt
 ```
 >Change *enable_uart = 0 to enable_uart = 1*

## 3. Thay đổi file 
### a. Mở file *cmdline.txt*
```
sudo nano /boot/cmdline.txt
```
### b. Xóa phần **console=serial0,115200**

ví dụ: 
>~~console=serial0,115200~~ console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline fsck.repair=yes root wait
## 4. Khởi động lại raspberry


##
# Setting ssh configuration
1. Truy cập vào file C:\Users\minhn\.ssh\config
> Nếu chưa có thì tạo file với tên **config**

2. Thêm vào file config danh sách robot

3. Ví dụ
```
Host robot1
	HostName 192.168.0.231
	Port 22
	User pi
```
# Git command - avoid conflict
## Work with sub-stream
> Luôn luôn **git rebase** từ nhánh chính

## Work with main-stream when sub-stream is done
> Git Merge từ nhánh phụ vào nhánh chính

# Change username of raspberrry pi4
Link hướng dẫn: **https://singleboardbytes.com/1234/managing-raspberry-pi-os-username-password.htm** 

Method 2:
1. Open your terminal and switch to root user using the command below:
``` 
sudo su
```
2. Copy to the terminal
```
sed -i s/pi/<new_user>/g /etc/passwd
sed -i s/pi/<new_user>/g /etc/shadow
sed -i s/pi/<new_user>/g /etc/group
sed -i s/pi/<new_user>/g /etc/sudoers
sed -i s/pi/<new_user>/g /etc/gshadow
mv /home/pi /home/<new_user>
reboot
```
Example:
We shall change our default “pi” username to “singleboardbytes.”
```
sed -i s/pi/singleboardbytes/g /etc/passwd
sed -i s/pi/singleboardbytes/g /etc/shadow
sed -i s/pi/singleboardbytes/g /etc/group
sed -i s/pi/singleboardbytes/g /etc/sudoers
sed -i s/pi/singleboardbytes/g /etc/gshadow
mv /home/pi /home/singleboardbytes
reboot
```
# Remove password when login in Raspberry
Go to this link:
> https://superuser.com/questions/1680017/set-password-when-power-my-pi
