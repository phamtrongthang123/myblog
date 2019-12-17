---
title: Hướng dẫn setup lại nếu lỡ cài lại OS (chẳng hạn Ubuntu)
author: Trong-Thang Pham
date: '2019-12-15'
slug: hướng-dẫn-setup-lại-nếu-lỡ-cài-lại-os-chẳng-hạn-ubuntu
categories:
  - Experiences
tags:
  - Ubuntu
---
Bên trong máy:

- Cài synaptic 
- Cài chrome 
- Cài gnome tweak
- Cài extension Hide Top Bar, Alt-Tab Switcher Popup Delay Removal, User Themes
- Cài dash to dock, nhưng chỉ vào chỉnh sao cho ẩn luôn cái dock luôn, rồi disable (vì nhìn xấu ._. , mình chỉ cần nó ẩn cái thanh kia thôi :D )
- Cài theme mac mojave từ https://www.gnome-look.org/p/1275087/ và bộ icon https://www.pling.com/p/1305429/ cho dịu mắt, nhớ cài luôn shell theme là mc mojave nha. ưu tiên dark mode
- Cài Tilix + VSCode 
  - Chạy script từ https://github.com/cra0zy/code-nautilus , nó sẽ thêm lựa chọn Open Code here và Open Tilix here, khá tiện 
  - `sudo update-alternatives --config x-terminal-emulator` , xong chọn tilix 
  - tilix dễ báo bug, nó có đưa link fix, t nhớ là copy cái gì ra đó, xong rồi thêm vào bash, cứ làm y chang đi.
- Cài fzf, cài theo kiểu pull git rồi install.sh nha
- conda, sure rồi, thêm mớ này vào bashrc: 
```
__conda_setup="$('/media/trongthang/Important/anaconda3/bin/conda' 'shell.bash' 'hook' 2> /dev/null)"
if [ $? -eq 0 ]; then
    eval "$__conda_setup"
else
    if [ -f "/media/trongthang/Important/anaconda3/etc/profile.d/conda.sh" ]; then
        . "/media/trongthang/Important/anaconda3/etc/profile.d/conda.sh"
    else
        export PATH="/media/trongthang/Important/anaconda3/bin:$PATH"
    fi  
fi
unset __conda_setup
```
- nodejs: phải có mớ này: `export PATH="/media/trongthang/Important/HOC_DAI_HOC/nodejs/node-v12.13.0-linux-x64/bin:$PATH"`
- Cài rofi,keybinding cho nó, nhớ có enable fuzzy search nha 
- Cho git thì tạo ssh theo hướng dẫn, thêm vào agent rồi vào git tạo 1 ssh key mới. vậy đủ rồi, ssh chẳng qua là để nó nhớ máy mình thôi ._. 
- youtube-dl, không thể thiếu.
Setup Blog:
- Cài Rstudio (không cần cài R)
- Mở file project lên 
- Vào blogdown tìm cài cách lệnh sau:
  - install.packages("blogdown")
  - install.packages("blogdown")
  - blogdown::install_theme("yihui/hugo-xmin", force=TRUE)
Vậy là xong, nhớ thử push lên github coi netlify có refresh không.