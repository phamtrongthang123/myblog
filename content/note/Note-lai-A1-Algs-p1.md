---
title: "Note Week 1 Algs part 1 (Princeton)"
date: "2018-02-09"
categories: 
- Algorithms

tags: 
- Union-Find
- Application
- Princeton
- Coursera
- Note 
- VI
---

Phải mất khá lâu mình mới bắt đầu làm assignment của tuần này, do khá tự ti về khả năng bản thân rằng sẽ không làm nổi vì hầu như ai cũng nói khó, lần mò thì có người bảo phải cần hiểu trước programming rồi OOP các thứ, làm mình chật vật vì không biết bắt đầu từ đâu. Đến 2 hôm trước sau khi nộp xong deadline về turning point thì mới phải tự vả một cái là hình như mình lại vô vòng an toàn. Có lẽ cũng do đây là Assignment đòi hỏi nhiều công việc đầu tiên mà mình làm nên mình mới như vậy.

# Union - Find
Tuần đầu tiên nên được học phần này, hình như trên đại học không có nội dung này thì phải.

### Step to developing a usable algorithm
* Model the problem.
* Find an algorithm to solve it.
* Fast enough? Fits in memory?
* If not, figure out why.
* Find a way to address the problem.
* Iterate until satisfied.

## 1. Nội dung: 
Ban đầu giáo sư Sedgewick dẫn dắt từ bài toán Dynamic connectivity để nói về khái niệm Union và Find. Các nội dung tiếp theo giáo sư nói  qua các thuật toán tối ưu hơn và sau đó đưa ra các ví dụ ứng dụng khác. Các dẵn dắt rất hay vì cảm giác như mình tìm ra giải pháp cùng Prof. Sedgewick vậy.

Phần này khá đơn giản nên cũng không biết phải note gì nhiều. Ứng dụng thì khá quan trọng: 

* Percolation
* Games (Go, Hex)
* Dynamic Connectivity
* Least common ancestor
* Equivalence of finite state automata
* Hoshen-Kopelman algorithm in physics
* Hinley-Milner polymorphic type inference
* Kruskal's minimum spanning tree algorithm
* Compilng equivalence statements in Fortran
* Morphological attribute openings and closings
* Matlab's `bwlabel()` function in image processing

Trong đó nội dung assignment là về Percolation. Percolation hiểu nôm na là sự thẩm thấu từ top tới bottom. Có một số ví dụ model như:

model | system | vacant site | occupied site | percolates 
:---: | :---: | :---: | :---: | :---: 
electricity | material | conductor | insulated | conducts
fluid flow | material | empty | blocked | porous
social interaction | population | person | empty | communicates 

## 2. Assignment: 
Khi làm assignment thì mới ngộ ra thêm nhiều điều về mức độ quan trọng của việc sử dụng biến và hàm. Đạt được 8x/100 không khó, nhưng 100/100 nhọc thật sự. Có thể note lại như sau:

* Luôn luôn để ý trường hợp ngoại lệ để throw exception. Và phải throw khôn chút để biết có bug thì do ai.
* Gọi hàm thì không được gọi tùy ý vì làm tăng thời gian thực thi, nên gọi xong gán biến cục bộ để giảm thời gian.
* Không được dùng biến tùy tiện. Cái giá phải trả thay vì dùng mảng boolean mà dùng mảng int là quá lớn.

Mốt làm bài tiếp chắc lòi ra tiếp.

# Analysis of Algorithms 

### Scientific method.
* Observe some feature of the natural world.
* Hypothesize a model that is consistent with the observations.
* Predict events using the hypothesis.
* Verify the predictions by making further observations.
* Validate by repeating until the hypothesis and observations agree.

### Principles. 
* Experiments must be reproducible.
* Hypotheses must be falsifiable.

### Tính gần đúng thời gian chạy chương trình
Có thể dùng đồ thị log-log và regression lại. Hoặc làm theo cách dưới đây:

Chạy thử chương trình, tăng x2 input.
Thời gian chạy sẽ bằng khoảng `$$aN^b, b = lg(\frac{time_n}{time_{n-1}})$$` 

Example:

N | time(second) | ratio | lg ratio
:---: | :---: | :---: | :---:
500 | 0.0 | 4.8 | 2.3
1000 | 0.1 | 6.9 | 2.8
2000 | 0.8 | 7.7 | 2.9
4000 | 6.4 | 8.0 | 3.0
8000 | 51.1 | 8.0 | 3.0

Như trên thì `$$b\approx3$$`
giải tiếp `$$51.1=a\times8000^3\Rightarrow a=0.998 \times 10^{-10}$$`
Vậy running time khoảng `$$0.998\times10^{-10}\times N^3$$` giây.

Có nhiều cái QA thú vị nữa nhưng để dành đọc slide, mà có cái hay hay là áp dụng calculus để tính discrete sum:

Ex1. 1+2+...+N `$$\sum_{i=1}^Ni \sim \int_{x=1}^Nxdx \sim \frac{1}{2} N^2$$`
Ex2. 1 + 1/2 +1/3 +... +1/N `$$\sum_{i=1}^N \frac{1}{i} \sim \int_{x=1}^N \frac{1}{x}dx = ln N$$`
...

Tiếp theo đó là nói về order-of-growth, hiểu nôm na về cái này thì bậc càng cao thì khi input lớn => hệ thống chậm. 

Nói cái nữa là log N rất lợi hại, nó gần bằng constant. (ví dụ binary search)

Sau đó là các nội dung khá rõ ràng ở slide. Không đặc biệt, ngoại trừ điều này.  
* **Dùng Big O để ước chừng model là sai, phải dùng dấu Tilde `~`.**

# Các quote trong tuần này:
> *"For me, great algorithms are the poetry of computation. Just like verse, they can be terse, allusive, dense, and even mysterious. But once unlocked, they cast a brilliant new light on some aspect of computing."* **- Francis Sullivan**


> *"An algorithm must be seen to be believed."* **-Donald Knuth**


> *"I will, in fact, claim that the difference between a bat programmer and a good one is whether he considers his code or his data structures more important. Bad programmers worry about the code. Good programmers worry about data structure and their relationships."* **-Linus Torvalds**
 

> *"Algorithms + Data Structures = Programs."* **-Niklaus Wirth**


> *"As soon as an Analytic Engine exist, it will necessarily guide the future course of the science. Whenever any result is sought by its aid, the question will arise - By what course of calculation can these results be arrived at by the machine in the shortest time?"* **-Charles Babbage (1864)**


> *"It is convenient to have a measure of the amount of work involved in a computing process, even though it be a very crude one. We may count up the number of times that various elementary operations are applied in the whole process and then given them various weights. We might, for instance, count the number of additions, subtractions, multiplications, divisions, recording of numbers, and extractions of figures from tables. In the case of computing with matrices most of the work consists of multiplications and writing down numbers, and we shall therefore only attempt to count the number of multiplications and recordings.”* **- Alan Turing**
