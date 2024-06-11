---
date: 2024-05-25
authors: [txmabc]
title: LateX数学公式在实际工作中的应用
description: >
  LaTeX是一个高质量的排版系统；它包括为生产技术和科学文档而设计的功能。LaTeX是科学文献交流和出版的事实标准。LaTeX是免费软件。
categories:
  - LaTeX
tags:
  - LaTeX
comments: true
---

[Simpletex]：一个可以将图片快速转化为Latex公式的软件

[math]：一个计算机手写板，你写出的任何计算式都会自动识别，并立即求得任何格式的结果。一些平时不能打出的数学符号，在这里可以完美识别

[墨迹公式]：微软office自带，支持手写输入，文档排版必备

<!-- more -->

1.运算符号

| 编号 | 符号 | 公式 | 语句 |
| ---- | ---- | ---- | ---- |
| 1 | 极限符号 | $$ \lim_{n \to +\infty} $$ | \lim_{n\to +\infty} |
| 2 | 样本均值 | $ \bar x $ | \bar x 或者\overline x |
| 3 | 分数 | $ \frac{1}{n} $ | \frac{1}{n} |
| 4 | 期望 | $ \mathbb{E} $ | \mathbb{E} |
| 5 | 求和 | $$ \sum_{i=1}^n $$ | \sum_{i=1}^n |
| 6 | 依概率收敛到 | $ x_n\stackrel{p}\longrightarrow\mu $ | x_n\stackrel{p}\longrightarrow\mu |
| 7 | 二次根号 | $ \sqrt{n} $ | \sqrt{n} |
| 8 | 四次根号 | $ \sqrt[4]{n} $ | \sqrt[4]{n} |
| 9 | 转置符合 | $ \mathtt{X} $ | \mathtt{X} |
| 10 | 累乘符号 | $ \prod $ | \prod |



2.希腊字母

| 小写 | 大写 | Latex小写命令 | Latex大写命令 |
|:-------:|:-------:|:-------:|:-------:|
| $\alpha$ | $\Alpha$ | \alpha | \Alpha |
| $\beta$ | $\Beta$ | \beta | \Beta |
| $\gamma$ | $\Gamma$ | \gamma | \Gamma |
| $\delta$ | $\Delta$ | \delta | \Delta | 
| $\epsilon$ | $\Epsilon$ | \epsilon | \Epsilon |
| $\zeta$ | $\Zeta$ | \zeta | \Zeta |
| $\nu$ | $\Nu$ |	\nu | \Nu |
| $\xi$ | $\Xi$ |	\xi | \Xi |
| $\omicron$ | $\Omicron$ | \omicron | \Omicron |
| $\pi$ | $\Pi$ | \pi | \Pi |
| $\rho$ | $\Rho$ | \rho | \Rho |
| $\sigma$ | $\Sigma$ | \sigma | \Sigma |
| $\eta$ | $\Eta$ | \eta | \Eta |
| $\theta$ | $\Theta$ | \theta | \Theta |
| $\iota$ | $\Iota$ | \iota | \Iota |
| $\kappa$ | $\Kappa$ | \kappa | \Kappa |
| $\lambda$ | $\Lambda$ | \lambda | \Lambda |
| $\mu$ | $\Mu$ | \mu | \Mu |
| $\tau$ | $\Tau$ | \tau | \Tau |
| $\upsilon$ | $\Upsilon$ | \upsilon | \Upsilon |
| $\phi$ | $\phi$ | \phi | \phi |
| $\chi$ | $\Chi$ | \chi | \Chi |
| $\psi$ | $\Psi$ | \psi | \Psi |
| $\omega$ | $\Omega$ | \omega | \Omega |

{{ read_excel('docs/assets/tables/latex_more.xlsx', engine='openpyxl') }}

[math]: https://webdemo.myscript.com/views/math/index.html
[Simpletex]: https://simpletex.cn/
[墨迹公式]: https://support.microsoft.com/zh-cn/office/word-%E4%B8%AD%E4%BD%BF%E7%94%A8-unicodemath-%E5%92%8C-latex-%E7%9A%84%E7%BA%BF%E6%80%A7%E6%A0%BC%E5%BC%8F%E5%85%AC%E5%BC%8F-2e00618d-b1fd-49d8-8cb4-8d17f25754f8