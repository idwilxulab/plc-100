如图1所示，“Copy RAM to ROM...” 可将PLC工作存储器中的数据备份到装载存储器。

![](/assets/屏幕快照 2017-09-30 上午11.09.33.png)

图1

在所有CPU上，只能在“STOP”操作模式下运行“Copy RAM to ROM...”功能。如果CPU不是处于“STOP”操作模式，系统将询问您是否通过STEP 7将CPU切换到“STOP”操作模式。

如果CPU模块有内置EPROM，可以使用“Copy RAM to ROM...”功能将内部RAM装载存储器中的内容复制到内置EPROM装载存储器中，以便电源断电且无电池时或者总复位时不致丢失数据。对于有内部EPROM作为装载存储器的SIMATIC S7-300 CPU或C7设备，代码和数据块则从RAM装载存储器复制到EPROM装载存储器。

对于有微存储卡\(MMC\)的SIMATIC S7-300 CPU和SIMATIC C7设备，当执行“Copy RAM to ROM...”功能时，与运行系统相关的数据块从主存储器复制到MMC。这里MMC上数据块的实际值被覆盖，以便经过一次总复位之后新的初始值\(新的实际值\)生效。这些新的初始值显示在SIMATIC STEP 7的“Actual value”列。

现在新型常用的PLC都必须配合MMC卡，才能使用，图2是"Copy RAM to ROM"的执行过程。

![](/assets/屏幕快照 2017-09-30 上午11.12.57.png)

                           图2 

