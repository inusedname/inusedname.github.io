---
layout: post
title: Cài đặt môi trường C++ cho Visual Studio Code (Windows/Linux)
date: 2022-03-01
permalink: /gcc-vscode/
categories: setup, basic
---

***Bài viết được cập nhật 10/08/2022***
> ## Mục lục:
> 1. [Cài đặt trình biên dịch GCC](#setup-environment)
>    1. [Windows](#env-windows)
>    2. [Linux Distros](#env-linux)
>2. [Cài đặt và và chương trình C đầu tiên](#setup-vscode)
>3. [Tuỳ chỉnh lại một chút cho vscode](#config-vscode)
>4. [Nâng cao: Debug cơ bản](#debug)

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

- Bước tiếp theo các bạn cần báo cho máy tính của mình biết bộ dịch này được tải về rồi và nó ở chỗ nào, bằng cách thêm nó vào **Environment Variables**:

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
- Bắt đầu viết code thôi. Chúng ta nhấn vào tab **Folder** nằm ở thanh dock trái, sau đó click **Open Folder**

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
![](/images/cpp-vscode/hello_world.jpg)

- Kết quả:

![build](/images/cpp-vscode/run_successfully.jpg)

# Step 3: Tuỳ chỉnh một chút cho vscode <a id = "config-vscode"> </a>

Từ bây giờ chúng ta dùng Visual Studio Code để code C++ vô tư rồi, tuy nhiên để cải thiện trải nghiệm mình muốn chỉnh sửa một chút để quen với workflow của mình hơn. Đây là file config của mình để các bạn tham khảo, các bạn có thể tự viết tuỳ chỉnh cho mình:

- Mở file config:
    - Nhấn `F1`, sau đó tìm `Open Setting (JSON)`
    
![config_search](/images/cpp-vscode/config.jpg)
    
- Sau đó dán vào config phía dưới:

```js
{%- raw -%}
// VanSu's Config
{
  // Code Runner Configs
  "code-runner.runInTerminal": true,
  "code-runner.saveFileBeforeRun": true,
  "code-runner.saveAllFilesBeforeRun": true,
  "code-runner.preserveFocus": false,
  "cph.general.autoShowJudge": false,

  // Editor Configs
  "editor.formatOnSave": true,
  "editor.formatOnType": true,
  "editor.formatOnPaste": true,
  "explorer.confirmDelete": false,
  "files.autoSave": "afterDelay",
  "workbench.sideBar.location": "right",
  "explorer.confirmDragAndDrop": false,
  "terminal.integrated.tabs.enabled": false,
  "terminal.integrated.copyOnSelection": true,
  "terminal.integrated.tabs.focusMode": "singleClick",
  "terminal.integrated.enableMultiLinePasteWarning": false,
  "workbench.startupEditor": "none",

  // Other
  "git.autofetch": true,
  "git.confirmSync": false,
  "diffEditor.ignoreTrimWhitespace": true,
  "security.workspace.trust.untrustedFiles": "open",

  /**
   * Themes của mình
   * Bạn tự cài theo sở thích riêng
   * Hoặc bỏ comment đoạn config của mình và dùng ✌️
   * Nhớ cài plugin: Fluent Icons, font chữ Firacode NF nhé
   */

  // "workbench.productIconTheme": "fluent-icons", 
  // "terminal.integrated.fontFamily": "Firacode NF Retina",
  // "workbench.colorTheme": "Visual Studio Light",
  // "window.zoomLevel": 1,

  // C/C++ Configs
  "[c]": {
    "editor.defaultFormatter": "ms-vscode.cpptools"
  },
  "[cpp]": {
    "editor.defaultFormatter": "ms-vscode.cpptools"
  },
  "C_Cpp.default.cStandard": "gnu99",
  "C_Cpp.default.cppStandard": "gnu++17",
  "C_Cpp.default.compilerPath": "D:\\bin\\msys2\\mingw64\\bin\\g++.exe",

  // Other Languages
  "[json]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  },
}
{% endraw %}
```

# Step 4: Debug C++ với VSCODE: <a id = "debug"> </a>
Bắt tay vào làm luôn thui :3

* Thêm breakpoint
**Breapoint là gì ?**
  > Breakpoint là điểm mà khi code chạy tới đấy thì chương trình dừng lại. Vậy thôi ✌️

![addbreakpoint](/images/cpp-vscode/addbreakpoint.jpg)
* Vào mode debug

![debuglaunch](/images/cpp-vscode/clickondebug.jpg)
* Ở đây nó sẽ hiện ra một cái box bên trên, bạn click vào cái g++ nhé

![debugrequire](/images/cpp-vscode/debugrequire.jpg)
* Ảo ma canada!

![debugrequire](/images/cpp-vscode/debugfirstsee.jpg)
* Đây là chương trình Hello World thôi, thế nếu chương trình yêu cầu nhập vào từ bàn phím thì làm thế nào ? Dễ thôi 💯

![debugrequire](/images/cpp-vscode/debuglaunch.jpg)
* Okay, thế giờ muốn stop lại thì làm thế nào nhỉ ✌️, giới thiệu với mọi người thanh điều hướng trong debug nhé

![debugrequire](/images/cpp-vscode/debugcontroller.jpg)
* Debug thực sự rất tiện dành cho người mới học, tuy nhiên post này không đi sâu vào debug, nên mọi người tự tìm hiểu nhé 😄
[Đây nhá!!!](https://viblo.asia/p/huong-dan-debug-danh-cho-nguoi-moi-eclipse-visual-studio-OeVKBWpYZkW)


**Các đường dẫn bổ sung:**
- Phím tắt VSCode: [https://www.facebook.com/clubproptit/posts/4542934582495170](https://www.facebook.com/clubproptit/posts/4542934582495170)
- Snippet VSCode: [https://www.facebook.com/clubproptit/posts/4804423199679639](https://www.facebook.com/clubproptit/posts/4804423199679639)