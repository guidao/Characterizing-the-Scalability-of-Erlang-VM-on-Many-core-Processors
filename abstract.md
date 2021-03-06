###多核处理器上的erlang虚拟机的特性
`作者：JIANRONG ZHANG`
`译者：`
`论文日期：2011年1月20日`

####概要

随着CPU芯片集成了更多的处理器内核，计算机系统从多核心到大量核心发展。如何充分的高效利用这些处理器核心是一个非常大的挑战。作为一个消息传递式并且原生支持并发的程序语言，使用erlang开发，是一个在这些系统上开发应用的非常方便的方式。可扩展的应用程序依靠erlang运行时系统和虚拟机运行。本篇论文是在一个64核心的多核处理器（TILEPro64）上的可扩展erlang虚拟机的研究过程。目的是为了研究erlang虚拟机的并行实现和它的瓶颈并且提供一些优化建议。为了完成这个愿望，会通过一些基准测试程序测试erlang虚拟机。发现的问题将利用一些方法例如profiling和tracing进行仔细的检查。研究结果表明当前的erlang虚拟机版本实现了非常好的可测量性，这一点使用了许多基准测试程序测试。最大的速度提升是从40核心到50核心。冲突引起的同步问题是系统的主要瓶颈所在。可扩展性可以通过减少锁冲突得到提高。另外一个主要问题是虚拟机的并行版本仅仅使用一个核心进行包含大量消息传递的基准测试，这是非常慢的。未来分析指出非竞争锁是诱发同步延迟的主要原因。低开销的锁，无锁结构和算法被推荐用于提高elang虚拟机的执行速度。我们的评估结果表明erlang非常适用在多核心系统上开发应用。

####道谢

我非常感谢我的审查人，Mats Brorsson教授，他支持并指导了整个项目。我也非常感谢爱立信Erlang/OTP团队的to Richard Green 和 Björn-Egil Dahlberg，他们向我介绍了erlang运行时系统的实现并回答了我许多问题，没有他们的帮助，这个项目将花费更多时间才能完成。此外，我需要感谢Erlang/OTP 团队提供的基准测试程序。我必须感谢在Kista多核中心的计算机科学学院的研究人员。例如Karl-Filip Faxén, Konstantin Popov,感谢他们的有价值的建议。

