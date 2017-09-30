使用系统功能

* SFC 84 “WRIT\_DBL” 可以将工作存储器中的“实际值”写入装载存储器（Load memory）（MMC卡）
* SFC 83 "READ\_DBL" 可读取装载存储器中的数据，并写回工作存储器。

工作过程如图所示。

![](/assets/屏幕快照 2017-09-30 上午11.20.27.png)

注意：

SFC 83可能需要多个扫描周期才可完成，触发调用SFC83后，需要把触发条件复位，SFC 83多用于读取UN-Linked类型的数据块。

SFC 84可能需要多个扫描周期才可完成，触发调用SFC84后，需要把触发条件复位，SFC 84对MMC卡有写操作，MMC 仅允许进行 100,000 次写访问，超过此次数，MMC卡将损坏。SFC 84多用于写UN-Linked类型的数据块，对于断电保持的数据块也可以进行写操作，但只有在CPU复位的情况下才可查看到SFC84最后一次写操作的数值。

---

参考自《Storage Concept and Data Backup Mechanisms for SIMATIC S7-300》

