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
2. [Cài đặt và và chương trình C đầu tiên](#setup-vscode)
3. [Tuỳ chỉnh lại một chút cho vscode](#config-vscode)

# Step 1: Cài đặt trình biên dịch GCC <a id = "setup-environment"></a>

### A. Windows: <a id = "env-windows"> </a>

- Để có thể biên dịch và chạy được mã C++ trên Windows, bạn cần cài đặt mingw-64:

    > Yêu cầu tải về: [mingw-64.7z](https://sourceforge.net/projects/mingw-w64/files/Toolchains%20targetting%20Win64/Personal%20Builds/mingw-builds/8.1.0/threads-posix/seh/x86_64-8.1.0-release-posix-seh-rt_v6-rev0.7z)

- Chuột phải vào file tải về, chọn **Extract File**, sau đó chọn vị trí mà bạn muốn lưu thư mục mingw64

|![mingw_setup_1](/images/cpp-vscode/mingw_setup_1.png)|
|:--:|
|*Giải nén thư mục tải về*|
|![mingw_setup_2](/images/cpp-vscode/mingw_setup_2.png)|
|:--:|
|*Chọn vị trí muốn cài đặt - ở đây mình chọn* `D:\bin`|
|![mingw_setup_3](/images/cpp-vscode/mingw_setup_3.png)|
|:--:|
|*Kết quả:*|

- Bước tiếp theo các bạn cần phải nói cho máy tính của mình biết bộ dịch này được tải về rồi và nó ở chỗ nào, bằng cách thêm nó vào **Environment Variables**:

![environment_1](/images/cpp-vscode/environment_1.jpg)
<br />
![environment_2](/images/cpp-vscode/environment_2.jpg)
<br />
![environment_3](/images/cpp-vscode/environment_3.jpg)
<br />
![environment_4](/images/cpp-vscode/environment_4.jpg)

- Bước cuối cùng để kiểm tra bạn đã làm đúng các bước trên, nhấn `Window - R`, điền `cmd`, sau đó nhập vào:

```bash
g++ --version
```
- Nó hiện vậy là oke:

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

# Step 2: Cài đặt và chương trình C đầu tiên: <a id = "setup-vscode"> </a>
> Yêu cầu tải về: [Visual Studio Code](https://code.visualstudio.com/)

- Ấn next và next thôi :D

- Sau khi cài xong mọi người sẽ có giao diện như vậy:

![gettingstaterd](/images/cpp-vscode/getting_started.jpg)

- Bước tiếp theo mọi người cần làm là
    - Chọn tab **Extension** nằm ở thanh dock bên trái
    - Tìm **C/C++** và **Code Runner** sau đó **Install**

![extension](/images/cpp-vscode/extension.jpg)
- Oke chúng ta đã có thể viết chương trình đầu tiên được rồi, bạn nhấn vào tab **Folder** nằm ở thanh dock, sau đó click **Open Folder**

    > Bạn có thể tạo mới một folder, hoặc sử dụng folder đã sẵn có. Mình khuyến khích các bạn nên sử dụng Open Folder thay vì Open File riêng lẻ vì sẽ có một số trường hợp vscode sẽ không hoạt động đối với Open File

![folder](/images/cpp-vscode/open_folder.jpg)

- Oke giờ thì tạo một file mới:

![file](/images/cpp-vscode/new-file.jpg)

- Viết Hello World và chạy:

    ```c++
    #include <stdio.h>
    int main()
    {
        printf("Hello World");
        return 0;
    }
    ```
    
<br>
![hello](/images/cpp-vscode/hello_world.jpg)

- Kết quả:

![build](/images/cpp-vscode/run_successfully.jpg)

# Step 3: Tuỳ chỉnh một chút cho vscode <a id = "config-vscode"> </a>

Visual Code của bạn giờ đã sẵn sàng để sử dụng, tuy nhiên để cải thiện trải nghiệm mình muốn chỉnh sửa một chút để quen với workflow của mình hơn. Đây là file config của mình để các bạn tham khảo, các bạn có thể tự viết tuỳ chỉnh cho mình:

- Mở file config:
    - Nhấn `F1`, sau đó tìm `Open Setting (JSON)`
    
![config_search](/images/cpp-vscode/config.jpg)
    
- Sau đó dán vào config phía dưới:

```js
{%- raw -%}
// My VSCODE Config
{
  "code-runner.runInTerminal": true,
  "code-runner.saveFileBeforeRun": true,
  "code-runner.saveAllFilesBeforeRun": true,
  "code-runner.preserveFocus": false,
  "terminal.integrated.tabs.enabled": false,
  "terminal.integrated.copyOnSelection": true,
  "terminal.integrated.tabs.focusMode": "singleClick",
  "files.autoSave": "afterDelay",
  // Sửa dòng bên dưới thành vị trí lưu mingw của bạn
  "C_Cpp.default.compilerPath": "D:\\bin\\mingw64\\bin\\g++.exe",
  // sửa dòng code phía trên
  "C_Cpp.default.cppStandard": "gnu++17",
  "C_Cpp.default.cStandard": "gnu11",
  // Nếu bạn sử dụng Linux, sửa dòng bên dưới thành: linux-gcc-x64
  "C_Cpp.default.intelliSenseMode": "windows-gcc-x64",
  "editor.formatOnSave": true,
  "editor.formatOnType": true,
  "editor.formatOnPaste": true,
}
{% endraw %}
```
> Tips: Các bạn có thể chỉnh sửa ở giao diện thân thiện hơn bằng cách ở bước tìm kiếm, chọn `Open Setting (UI)`. Tuy nhiên thì setting khá nhiều và bạn sẽ cần phải tìm chức năng của một config nào đó trên internet.


Các đường dẫn tham khảo ngoài:
- Phím tắt VSCode: [https://www.facebook.com/clubproptit/posts/4542934582495170](https://www.facebook.com/clubproptit/posts/4542934582495170)