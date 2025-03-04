# 工具

## 概览

我们有一套丰富的工具可用于协助 `crash dump` 的分析。如果使用得当，这可以节省大量时间。

Xcode 提供了很多现成的帮助。然而，如何使用和理解 Xcode 工具提供的信息是令人望而生畏的。在后面的章节中，我们将介绍这些工具的使用示例。

此外，在 macOS 中还提供了标准的命令行工具。这些工具在特定场景下有这难以想象的作用，尤其在我们已经知道我们需要找到什么的时候。我们将介绍具体的场景，并说明该如何使用这些工具。

接下来是帮助我们逆向工程的软件工具。有时候在使用第三方库时，有些问题很难被我们发现。那么除了查看文档或提出支持请求外，还可以使用这些工具自行进行调查。

## 逆向工程

逆向工程是研究已构建的二进制文件（例如应用程序，库或辅助进程守护程序），以确定它是如何工作的。对于一个特定的对象，我们可能想知道：

- 它所提供对象的生命周期是什么？
- 它对对象做什么检查？
- 它依赖哪些文件或资源？
- 它为什么返回故障代码？

通常，我们不用了解所有信息，只需要某些特定的东西来帮助建立假设。
一旦我们得到一个假设，我们将测试它与我们正在处理的 `crash dump` 是否有关。

逆向工程应该走多远，应该投入多少时间和金钱？我们提供以下建议：

- 如果我们刚刚开始我们的应用程序开发人员之旅，或者我们的资金有限，那么只需坚持使用标准的 Xcode 工具，macOS 命令行和 `class-dump` 工具。
- 如果我们是专业的应用程序开发人员，强烈建议购买商业逆向工程工具。最引人注目的是 `Hopper` ; 它提供了许多由 IDA Pro（一种高端工具）提供的功能。价格合理，即使只使用了几次，也可以提高生产力。我们在本书中将展示如何使用 Hopper。
- 如果我们是一个专业的渗透测试人员、逆向工程师或安全研究员，那么我们可能希望投资于顶级软件工具 IDA Pro。该工具成本高达数千美元，但通常是在公司范围内购买的。

## Class Dump 工具

Objective-C 运行时的一大优点是它在其构建的二进制文件中携带了大量丰富的程序结构信息。这些在语言的动态上得以发挥作用。实际上，灵活的动态调度是许多崩溃的源头。我们建议安装 `class-dump` 因为我们将在后面的章节中引用它的用法。

> 点击 [Class-dump]([http://stevenygard.com/projects/class-dump/](http://stevenygard.com/projects/class-dump/)) 下载安装。

 `class-dump` 工具允许我们查看给定程序中的Objective C 类、方法和属性。

## 第三方工具手机崩溃报告

虽然 iTunes Connect 中的 Apple Crash Reporter 工具非常的出色，但是仍有改进空间。

 一个强大的开源软件，由 Plausible Labs 的 Landon Fuller 所编写 `plcrashreporter`。@plcrashreporter

我们想让让我们的应用程序能够尽可能的处理发生的所有可能的信号和异常，一旦应用程序将无法实现，从而导致底层操作系统触发崩溃。

通过这个工具，可以记录崩溃信息，然后传输到我们自己的服务器上。

这有两个好处。首先，崩溃处理程序可以处理 Apple `ReportCrash` 工具尚未处理的边缘情况。其次，可以采用更全面的服务器端解决方案。

对于那些想要探索和理解操作系统以及底层应用程序代码的人来说，`plcrashreporter` 提供了一个学习精心设计的系统软件的绝好机会。

当公司拥有许多应用程序，许多应用程序变体，并且拥有基于 Android 等其他平台的应用程序时，就需要更强大的多平台解决方案。处理崩溃报告很快就会成为一种管理问题。哪个崩溃最严重？ 有多少客户受到影响？ 质量和稳定性的指标是什么？

有许多可用的商业解决方案，都主要基于上述开源项目。

移动软件开发领域在过去几年已经发展成为一个大产业。。许多专业公司为 App 开发者提供专业的服务。 该领域在合并和收购方面非常活跃。由于这个行业的变化之快，我们没办法在本书中列举这些专业公司的名称。

阅读 `rollout.io` 的博客是一个好的开始，它介绍了市场上的竞争者们。@3rdpartycrashtools
