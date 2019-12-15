---
title: 'Hệ điều hành: bộ nhớ'
author: Trong-Thang Pham
date: '2019-12-12'
slug: hệ-điều-hành-bộ-nhớ
categories:
  - Study at university
tags:
  - Hệ điều hành
  - Note
  - Operating System
---
Bắt đầu ôn bài thôi nhỉ. Từ đây sẽ là chuỗi bài ôn bài HDH cuối kì cho mình. Ôi mình cố dịch từ sách rồi ghi lại đấy, hic. 
Mình sẽ đi theo hướng giải bt vì nếu tóm tắt sẽ không đủ thời gian để hoàn thành. :( 

8.1 Name two differences between logical and physical addresses

user sẽ thấy theo logical  - còn thực tế sử dụng physical 
logial từ 0 -> max - physical được map qua R+0 -> R+max 
logical được CPU sinh ra - physical thì memory unit đọc được 

8.2 Consider a system in which a program can be separated into two parts: code and data. The CPU knows whether it wants an instruction (instruction fetch) or data (data fetch or store). Therefore, two base-limit register pairs are provided: one for instructions and one for data. The instruction base–limit register pair is automatically read-only, so programs can be shared among different users. Discuss the advantages and disadvantages of this scheme.

