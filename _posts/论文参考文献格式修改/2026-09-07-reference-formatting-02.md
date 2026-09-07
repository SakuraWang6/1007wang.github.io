---
title: '论文文献引用更改'
date: 2026-09-07 00:00:00 +0800
categories:
  - '论文参考文献格式修改'
---
Word中为实现连续多个参考文献的的引用，如\[1-3\]，教程如下：

1.将文末的参考文献自动编号

![](https://pic1.zhimg.com/v2-2a3b07a49b2c02e732f8bbbf1e08f230_b.jpg)

2.光标移至要引用的位置，选择【引用】-【交叉引用】，分别插入要引用文献编号的首位和末位，这里以\[1\]和\[3\]为例

![](https://pic2.zhimg.com/v2-f8526239a89a3fc99dc557e9bfa82291_b.jpg)

3.选中引用的编号，右键【切换域代码】

\[1\] 变为【{REF \_Ref444874348 \\r \\h}】

\[3\] 变为【{REF \_Ref444874357 \\r \\h}】

![](https://pic4.zhimg.com/v2-4b06ee15bdcdfd3be27d9265bd2dce13_b.jpg)

![](https://pic4.zhimg.com/v2-539937ac3dd27a3c8a4fba49680be68f_b.jpg)

4.编辑代码，分别加入字符【\\#"\[0"】和【\\#"0\]"】

\[1\] 的域代码变为【{REF \_Ref444874357 \\r \\h\\#"0\]"}】

\[3\] 的域代码变为【{REF \_Ref444874357 \\r \\h\\#"0\]"}】

![](https://pic1.zhimg.com/v2-49b7e71c379e31bf8fd3b3b943b06f3c_b.jpg)

5.右键域代码，选择【更新域】，变为\[13\]，中间加破折号变为\[1-3\]

![](https://pic1.zhimg.com/v2-72ed9b03fd00487db56bef9c67c13c10_b.jpg)

![](https://pic1.zhimg.com/v2-3aaabbe2dfcee1750465b521b4dce430_b.jpg)

![](https://pic3.zhimg.com/v2-317da61d91108909491192c4dec94aa6_b.jpg)

6.选中\[1-3\]，设置上标

![](https://pic2.zhimg.com/v2-5d1ee76195183cf536d54c8887eb2ac5_b.jpg)

