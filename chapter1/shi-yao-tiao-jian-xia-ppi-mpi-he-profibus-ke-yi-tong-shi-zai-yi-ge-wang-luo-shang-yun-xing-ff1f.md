PPI，MPI 和 PROFIBUS指的是不同通讯协议，它们都使用RS-485串行接口进行通讯，正是由于这个原因，才有可能在同一串行通讯网络中出现多种通讯协议共存的情况。

在波特率一致、各站地址不同的情况下，PPI，MPI 和 PROFIBUS 可以同时在一个网络上运行，并且互不干扰。

这就是说如果一个网络上有 S7-300、S7-200，S7-300 之间可以通过 MPI 或PROFIBUS 通讯，而在同时在同一个网络上的 TP170 micro 触摸屏可以与一个 S7-200 CPU 通讯。

