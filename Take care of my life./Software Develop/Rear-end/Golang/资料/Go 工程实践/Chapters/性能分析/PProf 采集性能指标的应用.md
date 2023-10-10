# PProf 采集性能指标的应用

这是本次分享的第一部分，主要介绍了 PProf 工具能采集的指标、展示方式和调用采样的简单示例。

PProf 的源码存在`runtime/pprof`包中，同时针对 HTTP 场景在`net/http/pprof`中封装了入口，引入该包即可在 HTTP handler 中注册 PProf 入口。

PProf 可以采集 CPU、堆内存、Goroutine、锁竞争、阻塞调用以及系统线程几种指标。

访问采样时，程序会将采样信息保存至本地文件，Go 自带的 PProf 工具可以通过网页或可视化终端展示这些信息；可以通过 Top、Graph、源码、火焰图、Peek、反汇编等视图来分析信息。

## 📒 课件

- [**点击此处，查看本节课件**](https://bytedance.feishu.cn/file/boxcn8A0z0MExQtwotXb17aHile?from=from_copylink "https://bytedance.feishu.cn/file/boxcn8A0z0MExQtwotXb17aHile?from=from_copylink")