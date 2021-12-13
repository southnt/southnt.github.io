
+++
author = "NamNT"
title = "WSL2 affects MTU"
date = "2021-12-01"
description = "A brief description of Hugo Shortcodes"
categories = [
    "Tech",
]
tags = [
    "IT",
    "Tech",
]
+++

## WSL2
Cài đặt wsl2:
https://www.omgubuntu.co.uk/how-to-install-wsl2-on-windows-10

trong các bước hướng dẫn ở link có thể thiếu bước phải enable hyperV ở bios, nếu cài xong rồi mà không chạy thì nên xem lại phần hyperV ở bios đã được enable chưa

## MTU
MTU là gì? https://quantrimang.com/mtu-la-gi-149617


## WSL2 affects MTU
Nếu install wsl2 theo các step dưới đây thì step 1 hoặc step 3 đã làm thay đổi giá trị [metrix](https://docs.microsoft.com/en-us/troubleshoot/windows-server/networking/automatic-metric-for-ipv4-routes) dẫn đến các packet của bạn trước khi install wsl2 và sau khi install wsl2 sẽ đi khác lộ trình với nhau. 
1. **Enable Hyper-V at boot**
2. Enable WSL 2
3. **Enable ‘Virtual Machine Platform’**
4. Set WSL 2 as default
5. Install a Linux distro

> A metric is a value that's assigned to an IP route for a particular network interface. It identifies the cost that's associated with using that route.

Trước khi install wsl, packet đi theo lộ trình A không có vấn đề gì, nhưng sau khi install wsl2 thì giá trị metrix bị thay đổi đẫn đến packet đi theo lộ trình B. Ở lộ trình B này, ở một hub nào đó giá trị MTU < giá trị MTU mà máy bạn setting thì packet sẽ không truyền đi được dẫn tới lỗi!
