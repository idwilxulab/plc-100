You can save actual values of data blocks by copying the online blocks to your offline project and loading the blocks once again into the SIMATIC S7-300. This reloading means that this data is once again available in the load memory and thus also after an overall reset.

在将修改后的PLC程序下载到CPU之前，需要考虑这样一个问题：**是否要保持当前PLC中DB块的实际值不变？**这些实际值包含一些工艺参数，控制设定值、设备运行状态等重要信息。若直接下载程序而不做保护措施，PLC中的实际值会被下载的DB块中设定的“实际值”覆盖，一些重要的运行参数可能因些而丢失。

要保护当前的实际值不被覆盖，需要先进行备份，然后再将离线项目下载到CPU。流程如图1所示。

![](blob:https://www.gitbook.com/70fb72b6-25d4-43e0-a801-45fa06699c78)

```
                                     图1 在更新程序时备份在线DB数据
```

操作流程如下：

1. 在SIMATIC Manger中，“File” &gt; "Open ... "打开“Open Project”对话框，选择项目。
2. “View” &gt; "Online" 打开在线视图，复制要备份的数据块，即包含了要保存的实际值的DB块文件。
3. 在离线中视图，粘贴并覆盖相应DB块，就样就完成了DB块的备份。
4. 执行“下载”操作，将修改的程序下载到PLC。

![](/assets/屏幕快照 2017-09-30 上午11.05.02.png)

```
                          图2 备份在线DB块
```



