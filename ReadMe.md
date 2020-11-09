<!-- TOC -->

- [Linux系统编程手册](#linux系统编程手册)
  - [01-历史和标准](#01-历史和标准)
  - [03-系统编程概念](#03-系统编程概念)
  - [04-通用的IO模型](#04-通用的io模型)
  - [05-深入探究文件IO](#05-深入探究文件io)
  - [06-进程](#06-进程)
  - [07-内存分配](#07-内存分配)
  - [08-用户和组](#08-用户和组)
  - [09-进程凭证](#09-进程凭证)
  - [10-时间](#10-时间)
  - [11-系统限制和选项](#11-系统限制和选项)
  - [12-系统和进程信息](#12-系统和进程信息)
  - [13-文件IO缓冲](#13-文件io缓冲)
  - [14-文件系统](#14-文件系统)
  - [15-文件属性](#15-文件属性)
  - [16-扩展属性](#16-扩展属性)
  - [17-访问控制列表](#17-访问控制列表)
  - [18-目录与链接](#18-目录与链接)
  - [19-监控文件事件](#19-监控文件事件)
  - [20-信号基本概念](#20-信号基本概念)
  - [21-信号处理函数](#21-信号处理函数)
  - [22-信号高级特性](#22-信号高级特性)
  - [23-定时器与休眠](#23-定时器与休眠)
  - [24-进程的创建](#24-进程的创建)
  - [25-进程的终止](#25-进程的终止)
  - [26-监控子进程](#26-监控子进程)
  - [27-程序的执行](#27-程序的执行)
  - [28-详述进程创建和程序执行](#28-详述进程创建和程序执行)
  - [29-线程基础](#29-线程基础)
  - [30-线程同步](#30-线程同步)
  - [31-线程安全和线程存储](#31-线程安全和线程存储)
  - [32-线程取消](#32-线程取消)
  - [33-线程更多细节](#33-线程更多细节)
  - [34-进程组-会话-作业控制](#34-进程组-会话-作业控制)
  - [35-进程优先级和调度](#35-进程优先级和调度)
  - [36-进程资源](#36-进程资源)
  - [37-Daemon](#37-daemon)
  - [38-编写安全的特权程序](#38-编写安全的特权程序)
  - [39-能力](#39-能力)
  - [40-登录记账](#40-登录记账)
  - [41-共享库基础](#41-共享库基础)
  - [42-共享库高级特性](#42-共享库高级特性)
  - [43-进程间通信简介](#43-进程间通信简介)
  - [44-管道和FIFO](#44-管道和fifo)
  - [45-SystemV-IPC-介绍](#45-systemv-ipc-介绍)
  - [46-SystemV-消息队列](#46-systemv-消息队列)
  - [47-SystemV-信号量](#47-systemv-信号量)
  - [48-SystemV-共享内存](#48-systemv-共享内存)
  - [49-内存映射](#49-内存映射)
  - [50-虚拟内存操作](#50-虚拟内存操作)
  - [51-POSIX-IPC介绍](#51-posix-ipc介绍)
  - [52-POSIX-消息队列](#52-posix-消息队列)
  - [53-POSIX-信号量](#53-posix-信号量)
  - [54-POSIX-共享内存](#54-posix-共享内存)
  - [55-文件加锁](#55-文件加锁)
  - [56-socket介绍](#56-socket介绍)
  - [57-socket-UNIX-Domain](#57-socket-unix-domain)
  - [59-socket-Internet-Domain](#59-socket-internet-domain)
  - [60-socket-服务器设计](#60-socket-服务器设计)
  - [61-socket-高级主题](#61-socket-高级主题)
  - [62-终端](#62-终端)
  - [63-其他备选的IO模型](#63-其他备选的io模型)
  - [64-伪终端](#64-伪终端)
  - [附录A-跟踪系统调用](#附录a-跟踪系统调用)
  - [附录B-解析命令行选项](#附录b-解析命令行选项)
  - [附录C-对NULL指针做转型](#附录c-对null指针做转型)
  - [附录D-内核配置](#附录d-内核配置)
- [linux性能优化](#linux性能优化)
  - [CPU性能](#cpu性能)
  - [IO性能](#io性能)
  - [内存性能](#内存性能)
  - [网络性能](#网络性能)
- [linux操作系统](#linux操作系统)
  - [概述](#概述)
  - [系统初始化](#系统初始化)
    - [X86体系](#x86体系)
      - [16位寄存器](#16位寄存器)
      - [32位寄存器](#32位寄存器)
    - [BIOS](#bios)
    - [Bootloader](#bootloader)
    - [内核初始化](#内核初始化)
    - [0号进程](#0号进程)
    - [1号进程](#1号进程)
    - [2号进程](#2号进程)
    - [glibc](#glibc)
  - [文件系统](#文件系统)
    - [磁盘系统](#磁盘系统)
      - [inode 与块的存储](#inode-与块的存储)
      - [inode 位图和块位图](#inode-位图和块位图)
      - [文件系统的格式](#文件系统的格式)
      - [目录的存储格式](#目录的存储格式)
      - [软链接和硬链接的存储格式](#软链接和硬链接的存储格式)
    - [虚拟文件系统](#虚拟文件系统)
    - [挂载文件系统](#挂载文件系统)
    - [打开文件](#打开文件)
    - [文件缓存](#文件缓存)
      - [系统调用层和虚拟文件系统层](#系统调用层和虚拟文件系统层)
      - [ext4 文件系统层](#ext4-文件系统层)
      - [带缓存的写入操作](#带缓存的写入操作)
      - [带缓存的读操作](#带缓存的读操作)
  - [输入输出系统](#输入输出系统)
    - [用设备控制器屏蔽设备差异](#用设备控制器屏蔽设备差异)
    - [用驱动程序屏蔽设备控制器差异](#用驱动程序屏蔽设备控制器差异)
    - [用文件系统接口屏蔽驱动程序的差异](#用文件系统接口屏蔽驱动程序的差异)
    - [字符设备](#字符设备)
      - [内核模块](#内核模块)
      - [打开字符设备](#打开字符设备)
      - [写入字符设备](#写入字符设备)
      - [使用 IOCTL 控制设备](#使用-ioctl-控制设备)
      - [驱动中断程序](#驱动中断程序)
    - [块设备](#块设备)
      - [直接 I/O](#直接-io)
      - [缓存 I/O](#缓存-io)
      - [向块设备层提交请求](#向块设备层提交请求)
      - [块设备的初始化](#块设备的初始化)
      - [请求提交与调度](#请求提交与调度)
      - [请求的处理](#请求的处理)
  - [进程管理](#进程管理)
    - [ELF文件的分类](#elf文件的分类)
    - [多线程并行](#多线程并行)
    - [内核任务](#内核任务)
    - [用户态函数栈](#用户态函数栈)
    - [调度策略与调度类](#调度策略与调度类)
      - [实时调度策略](#实时调度策略)
      - [普通调度策略](#普通调度策略)
      - [调度策略的调度类](#调度策略的调度类)
      - [普通进程的 fair 完全公平调度算法 CFS](#普通进程的-fair-完全公平调度算法-cfs)
      - [调度队列和调度实体](#调度队列和调度实体)
      - [调度类如何工作](#调度类如何工作)
        - [主动调度](#主动调度)
        - [抢占式调度](#抢占式调度)
        - [抢占时机](#抢占时机)
    - [进程创建](#进程创建)
    - [线程的创建](#线程的创建)
  - [进程间通信](#进程间通信)
    - [管道模型](#管道模型)
      - [管道](#管道)
      - [匿名管道](#匿名管道)
      - [命名管道](#命名管道)
    - [消息队列模型](#消息队列模型)
    - [共享内存模型](#共享内存模型)
      - [共享内存的内核机制](#共享内存的内核机制)
    - [信号量](#信号量)
      - [信号量的内核机制](#信号量的内核机制)
    - [信号](#信号)
      - [信号的发送](#信号的发送)
      - [信号的处理](#信号的处理)
  - [内存管理](#内存管理)
    - [用户态和内核态的虚拟内存空间](#用户态和内核态的虚拟内存空间)
    - [物理内存的组织方式](#物理内存的组织方式)
    - [小内存的分配](#小内存的分配)
    - [用户态内存映射](#用户态内存映射)
    - [内核页表](#内核页表)
  - [网络系统](#网络系统)
    - [Socket通信之网络协议基本原理](#socket通信之网络协议基本原理)
    - [发送数据包](#发送数据包)
      - [TCP socket过程](#tcp-socket过程)
      - [UDP socket过程](#udp-socket过程)
      - [解析 socket 函数](#解析-socket-函数)
      - [解析 bind 函数](#解析-bind-函数)
      - [解析 listen 函数](#解析-listen-函数)
      - [解析 accept 函数](#解析-accept-函数)
      - [解析 connect 函数](#解析-connect-函数)
    - [发送网络包](#发送网络包)
      - [解析 socket 的 Write](#解析-socket-的-write)
      - [解析 tcp_sendmsg](#解析-tcp_sendmsg)
      - [解析 tcp_write_xmit](#解析-tcp_write_xmit)
      - [解析 ip_queue_xmit](#解析-ip_queue_xmit)
      - [解析 ip_finish_output](#解析-ip_finish_output)
    - [接收网络包](#接收网络包)
      - [设备驱动层](#设备驱动层)
      - [网络协议栈的二层逻辑](#网络协议栈的二层逻辑)
      - [网络协议栈的 IP 层](#网络协议栈的-ip-层)
      - [网络协议栈的 TCP 层](#网络协议栈的-tcp-层)
      - [Socket 层](#socket-层)
  - [虚拟化](#虚拟化)
    - [三种虚拟化方式](#三种虚拟化方式)
    - [创建虚拟机](#创建虚拟机)
    - [虚拟化之CPU](#虚拟化之cpu)
    - [虚拟化之内存](#虚拟化之内存)
    - [虚拟化之存储](#虚拟化之存储)
    - [虚拟化之网络](#虚拟化之网络)
  - [容器化](#容器化)
    - [Docker的基本原理](#docker的基本原理)
    - [Namespace技术](#namespace技术)
    - [cgroup技术](#cgroup技术)
    - [数据中心操作系统](#数据中心操作系统)

<!-- /TOC -->

## Linux系统编程手册
### 01-历史和标准
### 03-系统编程概念
### 04-通用的IO模型
### 05-深入探究文件IO
### 06-进程 
### 07-内存分配
### 08-用户和组 
### 09-进程凭证
### 10-时间  
### 11-系统限制和选项
### 12-系统和进程信息
### 13-文件IO缓冲
### 14-文件系统 
### 15-文件属性
### 16-扩展属性
### 17-访问控制列表
### 18-目录与链接
### 19-监控文件事件
### 20-信号基本概念
### 21-信号处理函数
### 22-信号高级特性
### 23-定时器与休眠
### 24-进程的创建
### 25-进程的终止
### 26-监控子进程
### 27-程序的执行
### 28-详述进程创建和程序执行
### 29-线程基础
### 30-线程同步 
### 31-线程安全和线程存储 
### 32-线程取消  
### 33-线程更多细节
### 34-进程组-会话-作业控制
### 35-进程优先级和调度
### 36-进程资源 
### 37-Daemon
### 38-编写安全的特权程序 
### 39-能力   
### 40-登录记账
### 41-共享库基础 
### 42-共享库高级特性
### 43-进程间通信简介
### 44-管道和FIFO
### 45-SystemV-IPC-介绍
### 46-SystemV-消息队列
### 47-SystemV-信号量
### 48-SystemV-共享内存
### 49-内存映射 
### 50-虚拟内存操作
### 51-POSIX-IPC介绍 
### 52-POSIX-消息队列 
### 53-POSIX-信号量
### 54-POSIX-共享内存
### 55-文件加锁
### 56-socket介绍 
### 57-socket-UNIX-Domain
### 59-socket-Internet-Domain
### 60-socket-服务器设计 
### 61-socket-高级主题
### 62-终端
### 63-其他备选的IO模型
### 64-伪终端
### 附录A-跟踪系统调用
### 附录B-解析命令行选项
### 附录C-对NULL指针做转型
### 附录D-内核配置


## linux性能优化
### CPU性能
### IO性能
### 内存性能
### 网络性能


## linux操作系统
### 概述
### 系统初始化
#### X86体系
##### 16位寄存器
##### 32位寄存器
#### BIOS
#### Bootloader
#### 内核初始化
#### 0号进程
#### 1号进程
#### 2号进程
#### glibc 

### 文件系统
#### 磁盘系统
##### inode 与块的存储
##### inode 位图和块位图
##### 文件系统的格式
##### 目录的存储格式
##### 软链接和硬链接的存储格式
#### 虚拟文件系统
#### 挂载文件系统
#### 打开文件
#### 文件缓存
##### 系统调用层和虚拟文件系统层
##### ext4 文件系统层
##### 带缓存的写入操作
##### 带缓存的读操作

### 输入输出系统
#### 用设备控制器屏蔽设备差异
#### 用驱动程序屏蔽设备控制器差异
#### 用文件系统接口屏蔽驱动程序的差异
#### 字符设备
##### 内核模块
##### 打开字符设备
##### 写入字符设备
##### 使用 IOCTL 控制设备
##### 驱动中断程序
#### 块设备
##### 直接 I/O
##### 缓存 I/O
##### 向块设备层提交请求
##### 块设备的初始化
##### 请求提交与调度
##### 请求的处理

### 进程管理
#### ELF文件的分类
#### 多线程并行
#### 内核任务
#### 用户态函数栈
#### 调度策略与调度类
##### 实时调度策略
##### 普通调度策略
##### 调度策略的调度类
##### 普通进程的 fair 完全公平调度算法 CFS
##### 调度队列和调度实体
##### 调度类如何工作
###### 主动调度
###### 抢占式调度
###### 抢占时机
#### 进程创建
#### 线程的创建

### 进程间通信
#### 管道模型
##### 管道
##### 匿名管道
##### 命名管道
#### 消息队列模型
#### 共享内存模型
##### 共享内存的内核机制
#### 信号量
##### 信号量的内核机制
#### 信号
##### 信号的发送
##### 信号的处理

### 内存管理
#### 用户态和内核态的虚拟内存空间
#### 物理内存的组织方式
#### 小内存的分配
#### 用户态内存映射
#### 内核页表

### 网络系统
#### Socket通信之网络协议基本原理
#### 发送数据包
##### TCP socket过程
##### UDP socket过程
##### 解析 socket 函数
##### 解析 bind 函数
##### 解析 listen 函数
##### 解析 accept 函数
##### 解析 connect 函数
#### 发送网络包
##### 解析 socket 的 Write
##### 解析 tcp_sendmsg
##### 解析 tcp_write_xmit 
##### 解析 ip_queue_xmit 
##### 解析 ip_finish_output
#### 接收网络包
##### 设备驱动层
##### 网络协议栈的二层逻辑
##### 网络协议栈的 IP 层
##### 网络协议栈的 TCP 层
##### Socket 层

### 虚拟化
#### 三种虚拟化方式
#### 创建虚拟机
#### 虚拟化之CPU
#### 虚拟化之内存
#### 虚拟化之存储
#### 虚拟化之网络

### 容器化
#### Docker的基本原理
#### Namespace技术
#### cgroup技术
#### 数据中心操作系统
