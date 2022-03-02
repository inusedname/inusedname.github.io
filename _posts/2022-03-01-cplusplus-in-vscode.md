---
layout: post
title: Hướng dẫn cài đặt C++ cho Visual Studio Code (Windows và Linux)
date: 2022-03-01
permalink: /gcc-vscode/
categories: basic
---

## Mục lục:
1. [Cài đặt trình biên dịch GCC](#setup-environment)
    1. [Windows](#env-windows)
    2. [Linux Distros](#env-linux)
2. [Cài đặt và thiết lập Visual Studio Code]()

# Step 1: Cài đặt trình biên dịch GCC <a id = "setup-environment"></a>

### A. Windows: <a id = "env-windows"> </a>

- Để có thể biên dịch và chạy được mã C++ trên Windows, bạn cần cài đặt mingw-64:

    > Yêu cầu tải về: [mingw-64.7z](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/seh/x86_64-8.1.0-release-posix-seh-rt_v6-rev0.7z)

- Chuột phải vào file tải về, chọn **Extract File**, sau đó chọn vị trí mà bạn muốn lưu thư mục mingw64

*Giải nén thư mục tải về*
<br />
![mingw_setup_1](/images/cpp-vscode/mingw_setup_1.png)

*Chọn vị trí muốn cài đặt - ở đây mình chọn* 
**D:\bin**
<br />
![mingw_setup_2](/images/cpp-vscode/mingw_setup_2.png)

*Kết quả:*
<br />
![mingw_setup_3](/images/cpp-vscode/mingw_setup_3.png)

- Bước tiếp theo các bạn cần phải nói cho máy tính của mình biết bộ dịch này được tải về rồi và nó ở chỗ nào, bằng cách thêm nó vào **Environment Variables**:

![environment_1](/images/cpp-vscode/environment_1.jpg)
<br />
![environment_2](/images/cpp-vscode/environment_2.jpg)
<br />
![environment_3](/images/cpp-vscode/environment_3.jpg)
<br />
![environment_4](/images/cpp-vscode/environment_4.jpg)

- Bước cuối cùng để kiểm tra bạn đã làm đúng các bước trên, nhấn Window - R, điền cmd, sau đó nhập vào:
```bash
g++ --version
```
Nó hiện vậy là oke:
```
C:\Users\mycomputer>g++ --version
g++ (x86_64-posix-seh-rev0, Built by MinGW-W64 project) 8.1.0
Copyright (C) 2018 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.
```

### B. Linux Distros <a id = "env-linux"> </a>

Các distro Linux luôn đi kèm với bộ dịch GCC (do Linux được viết bằng C), cho nên không cần thiết chúng ta phải cài GCC thêm một lần nữa, tuy nhiên sau đây là một số lệnh nếu bạn muốn kiểm tra bộ dịch gcc của mình:

```bash
# Kiểm tra phiên bản GCC:
gcc --version
g++ --version

# Update/cài đặt gcc"
sudo apt-get install gcc g++
```

# Step 2: Cài đặt và thiết lập Visual Studio Code:
> Yêu cầu tải về: [Visual Studio Code](https://code.visualstudio.com/)

Ấn next và next thôi :D

... còn nữa