---
layout: post
title: FreeRTOS学习教程（一）
description: FreeRTOS简介
categories:
  - FreeRTOS
  - M4
  - 实时操作系统
---

提到FreeRTOS，大家的第一反应是，为什么会去学FreeRTOS，FreeRTOS有哪些优缺点，这篇文章会从零开始带领大家进入FreeRTOS的世界，这也是我验证自身所学的一个过程。

## FreeRTOS简介

RTOS全称为real-time-operate-sysyem，以为实时操作系统，很多软件都能够在不是用RTOS的情况下编写好，但是在实时性和复杂情况下，RTOS有得天独厚的优势。大致总结一下RTOS相对于普通的嵌入式程序的优势

1）实时性

实时性是RTOS最大的特征，这里可以借用维基百科上的一段对实时性的描述：

<font color  = 'blue'> 实时运算（Real-time computing）是计算机科学中对受到“实时约束”的计算机硬件和计算机软件系统的研究，实时约束像是从事件发生到系统回应之间的最长时间限制。实时程序必须保证在严格的时间限制内响应。</font>

总的来说，所有的实时操作系统都会包含一个实时任务调度器，而RTOS中的任务调度器相对于其他操作系统来说，最大的不同就是RTOS是强调<font color='red'> 按照任务优先级来分配CPU时间，并且时间片的轮转不是实时调度器的一个必选项</font>。　

