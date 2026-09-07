---
title: '论文文献引用更改'
date: 2026-09-07 00:00:00 +0800
categories:
  - '论文参考文献格式修改'
---
Word中为实现连续多个参考文献的的引用，如\[1-3\]，教程如下：

1.将文末的参考文献自动编号

![自动编号参考文献]({{ '/assets/img/reference-formatting/zhihu-01.jpg' | relative_url }})

2.光标移至要引用的位置，选择【引用】-【交叉引用】，分别插入要引用文献编号的首位和末位，这里以\[1\]和\[3\]为例

![插入交叉引用]({{ '/assets/img/reference-formatting/zhihu-02.jpg' | relative_url }})

3.选中引用的编号，右键【切换域代码】

\[1\] 变为【{REF \_Ref444874348 \\r \\h}】

\[3\] 变为【{REF \_Ref444874357 \\r \\h}】

![切换域代码]({{ '/assets/img/reference-formatting/zhihu-03.png' | relative_url }})

![参考文献域代码]({{ '/assets/img/reference-formatting/zhihu-04.jpg' | relative_url }})

4.编辑代码，分别加入字符【\\#"\[0"】和【\\#"0\]"】

\[1\] 的域代码变为【{REF \_Ref444874357 \\r \\h\\#"0\]"}】

\[3\] 的域代码变为【{REF \_Ref444874357 \\r \\h\\#"0\]"}】

![编辑域代码]({{ '/assets/img/reference-formatting/zhihu-05.jpg' | relative_url }})

5.右键域代码，选择【更新域】，变为\[13\]，中间加破折号变为\[1-3\]

![更新域代码]({{ '/assets/img/reference-formatting/zhihu-06.png' | relative_url }})

![连续引用编号]({{ '/assets/img/reference-formatting/zhihu-07.jpg' | relative_url }})

![引用编号加破折号]({{ '/assets/img/reference-formatting/zhihu-08.jpg' | relative_url }})

6.选中\[1-3\]，设置上标

![设置参考文献上标]({{ '/assets/img/reference-formatting/zhihu-09.jpg' | relative_url }})
