---
layout:     post
title:      DEFCON-长沙
date:       2020-10-17 14:14:23 +0800
categories: Security
tags:       DEFCON
author:     SteveDevin
mathjax:    true
---
* content
{:toc}

## LOT 安全

### 信息泄露 

1. 配置文件泄露
    - phpinfo
    - config
    - dbconfig
    - RouterCfm.cfg
    - Dbconnect
    - ...
    
2. 备份文件泄露
    - /backup
    - /bak
    - /beifen
    - /xxx.bak
    - /xxx.tar
    - /xxx.zip
    - ...
    
3. Others
    - git, svn
    - version
    - test 目录, 页面
    - 管理入口
    - 用户信息
    
### 威胁发现
1. 目录扫描
    - 御剑
    - burpsuite
    
2. 固件解析
    - binwalk
    - android killer
    
    
## 工控安全打造攻击连 - 剑思庭

1. 工业控制系统场景
    - 啤酒工厂布局
    - 监控总控室
    - 生产线设备
    
2. 工业控制产品介绍
    - Siemens 控制系统家族 S7-1500, S7-1200, S7-300/400
    - Siemens 组态软件家族 TIA 博图 /Step7, WINCC组态监控软件, PLCSIM模拟仿真软件
    
3. 工业控制攻击面分析
    - 协议重放攻击. 缺乏身份认证, 缺乏加密保护