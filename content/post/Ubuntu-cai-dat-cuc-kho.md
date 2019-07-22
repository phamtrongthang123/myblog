---
title: "Cài Ubuntu lần đầu"
author: "Pham Trong Thang"
date: 2018-01-24
categories:
  - Experiences
tags:
  - Ubuntu
  - Fun stuff
---

# Cài Ubuntu lần đầu tiên

Gian nan. Mà mọi lý do chủ yếu đến từ việc graphic card Nvidia :|

Nếu có máy có card rời, nếu ở màn hình menu chọn Try Ubuntu... Install Ubuntu ... mà không chỉnh nomodeset thì sẽ bị kẹt ở logo screen có mấy cái chấm chấm phía dưới. Mình tốn mấy ngày để mò vì tưởng phải chỉnh trong BIOS, chỉnh sau khi có màn hình menu, ... Cuối cùng phát hiện, là tới menu bấm f6 và chọn nomodeset là xong <(").

Sau khi vào được, những tưởng suôn sẻ thì phát hiện máy chỉ chia được 4 primary partition, Windows 10 ngốn đủ 4 cái => wtf? => format ở cứng (có chuyển dữ liệu rồi :))) )

Cài xong, vui thiệt vui vì mấy hôm trời rồi chả mần được gì. Mở windows lên, ngon, không có lỗi. Nghĩ rằng mọi chuyện đã ổn, mở Ubuntu lên => giật màn hình, đoán là do card màn hình => cài driver => không fix được => wtf? 

Sau mấy tiếng bạn Lâm ngồi search google để giúp mình và làm đủ thứ, mất thời gian quá nên thôi tạm ngưng :(. (mình lúc này vô dụng rồi vì không hiểu gì đang xảy ra )

Lên phòng mình tìm kiếm tiếp, chợt thấy có bài nói là "Because of NOMODESET" , ok :)))) , theo bài hướng dẫn vô chỉnh lại nouveau.modeset=0 thì chạy ok, lưu vào grub để nó tự chạy luôn. => ổn thỏa.

