
div><!--EndFragment-->
</body>
</html>dis ip int brief
查看虚接口运行
dis int br
查看接口运行
dis vlan
查看VLAN
dis cu
查看当前配置 dis version
查看当前设备版本信息
sysname
设备名称
dis device
查看设备型号，状态
dis cpu-usage
查看设备CPU运行信息
dis ip routing-table
查看当前路由
dis ip routing-table 8.8.8.8
查看某一个路由条目
display saved-configuration 查看配置信息———-配置信息可以作为导入文件
description to_Core,neiwang 接口模式下添加接口描述信息 description
dis lldp neighbor brief
dis lldp neighbor brief
dis lldp neighbor brief ----#neighbor 邻居 brief 简要描述#【查看交换上联和下联设备名称信息】
华为命令更新20210824：
dis lldp neighbor brief ----#neighbor 邻居 brief 简要描述#
请进入命令行 采集相关信息
Display diagnostic-information （此命令时间很长）
dis int brief (看端口)
reset  counters interface g0/0/26（重置端口的统计信息）
dis arp all
----------------------------------------------------------
display ?（?是英文）#查看命令#
（未开启激活LLDP步骤#sys--lldp en--quit--save--y--y#记得保存）
dis tran int g 0/0/14 ver----#看端口信息#可以看到光模块的信息
dis vlan
dis cpu-usage ----#查看内存使用信息#
display device 简写 dis dev-----#查看设备信息#
display current-configuration；简写dis cur；#显示当前配置#
-----------------------------------------------------------
关闭（恢复）某个端口
<S5720>sys
Enter system view, return user view with Ctrl+Z.
[S5720]``int g0/0/7
[S5720-GigabitEthernet0/0/7]shutdown
[S5720-GigabitEthernet0/0/7]undo shutdown  （恢复）
quit 退出
----------------------------------------------------------
dis saved-configuration 查看命令
display current-configuration 简写dis cur；#显示当前配置#
dis ip int brief
查看虚接口运行
dis int br
查看接口运行
dis vlan
查看VLAN
dis cu
查看当前配置 dis version
查看当前设备版本信息
sysname
设备名称
dis device
查看设备型号，状态
dis cpu-usage
查看设备CPU运行信息
dis ip routing-table
查看当前路由
dis ip routing-table 8.8.8.8
查看某一个路由条目
display saved-configuration 查看配置信息———-配置信息可以作为导入文件
description to_Core,neiwang 接口模式下添加接口描述信息 description
dis lldp neighbor brief
dis lldp neighbor brief
dis lldp neighbor brief ----#neighbor 邻居 brief 简要描述#【查看交换上联和下联设备名称信息】
华为命令更新20210824：
dis lldp neighbor brief ----#neighbor 邻居 brief 简要描述#
请进入命令行 采集相关信息
Display diagnostic-information （此命令时间很长）
dis int brief (看端口)
reset  counters interface g0/0/26（重置端口的统计信息）
dis arp all
----------------------------------------------------------
display ?（?是英文）#查看命令#
（未开启激活LLDP步骤#sys--lldp en--quit--save--y--y#记得保存）
dis tran int g 0/0/14 ver----#看端口信息#可以看到光模块的信息
dis vlan
dis cpu-usage ----#查看内存使用信息#
display device 简写 dis dev-----#查看设备信息#
display current-configuration；简写dis cur；#显示当前配置#
-----------------------------------------------------------
关闭（恢复）某个端口
<S5720>sys
Enter system view, return user view with Ctrl+Z.
[S5720]``int g0/0/7
[S5720-GigabitEthernet0/0/7]shutdown
[S5720-GigabitEthernet0/0/7]undo shutdown  （恢复）
quit 退出
----------------------------------------------------------
dis saved-configuration 查看命令
display current-configuration 简写dis cur；#显示当前配置#
-----------------------------------------------------------
2.将一个端口添加到某个VLAN中
1 2 3 4 5 6 7 8 9 10 11 12 13	<AC6605>sys Enter system view, return user view with Ctrl+Z. [AC6605]``interface GigabitEthernet0/0/3 [AC6605-GigabitEthernet0/0/3]port link-type access [AC6605-GigabitEthernet0/0/3]port default vlan 44 [AC6605-GigabitEthernet0/0/3]quit [AC6605]quit <AC6605>save The current configuration will be written to the device. Are you sure to continue``? (y/n)[n]:y It will take several minutes to save configuration file, please wait.......... Configuration file has been saved successfully Note: The configuration file will take effect after being activated
3.将几个端口一次性添加到一个vlan中（port-``group 1）
注意这里的``group``不能有和已知的``group``重复
1 2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18 19 20 21 22	<AC6605>sys Enter system view, return user view with Ctrl+Z. [AC6605]port-``group 1 [AC6605-port-``group``-1]``group``-member g0/0/3 to g0/0/6 [AC6605-port-``group``-1]port link-type access [AC6605-GigabitEthernet0/0/3]port link-type access [AC6605-GigabitEthernet0/0/4]port link-type access [AC6605-GigabitEthernet0/0/5]port link-type access [AC6605-GigabitEthernet0/0/6]port link-type access [AC6605-port-``group``-1]port default vlan 44 [AC6605-GigabitEthernet0/0/3]port default vlan 44 [AC6605-GigabitEthernet0/0/4]port default vlan 44 [AC6605-GigabitEthernet0/0/5]port default vlan 44 [AC6605-GigabitEthernet0/0/6]port default vlan 44 [AC6605-port-``group``-1]quit [AC6605]quit <AC6605>save The current configuration will be written to the device. Are you sure to continue``? (y/n)[n]:Y It will take several minutes to save configuration file, please wait......... Configuration file has been saved successfully Note: The configuration file will take effect after being activated
华为s5720-S5735  console口密码重置
**

**
现场问题描述：
某公司仓库C1库1F挂壁机柜S5720设备
如图，设备无法通过console口登录？原始密码未知
如何破解-----查看现场网络环境和查阅资料后决定破解密码。

★想到办法，立马开干，第一步先了解一下生产环境，确认设备可以断电，可以调试，打好招呼了开始干活。
---------------------------------步骤LIST-------------------------------------
1、通过Console口连接交换机，切断电源，重启设备；
2、当界面出现以下打印内容时候，快速按下“ctrl+B”；

3、并输入BootRom密码：[Admin@huawei.com](mailto:Admin@huawei.com)；

4、根据打印信息，选择第7条，清除console口用户密码；

5、注意：新版本S5735系列，根据此图操作，选择6，少了一个选项（210819更新）；

6、接上面步骤4，选择7之后，马上会打印信息；
7、根据打印信息，选择Y，之后会打印新的信息，入图，选择第1个；

8、此时不要着急，等待约2-3分钟的设备重启，然后端口会逐步启用；

9、等所有端口都起来了，就可以使用了。
Ps：不足之处验证：（当时太快了，缺截图，待完善）
另外：再补充一下，如需再次设置该端口密码，请执行：

1 2 3 4 5 6 7 8 9 10 11 12 13 14	<HUAWEI>sys Enter system view, return user view with Ctrl+Z.
[HUAWEI] [HUAWEI]user-``interface console 0 
[HUAWEI-ui-console0]au 
[HUAWEI-ui-console0]authentication-mode password 
[HUAWEI-ui-console0]``set authentication password cipher Huawei@123 
[HUAWEI-ui-console0]``return 
<HUAWEI>save The current configuration will be written to the device. Are you sure to continue``?[Y/N]Y Info: Please input the file name ( *.cfg, *.zip ) [vrpcfg.zip]: Aug 19 2021 15:50:12+08:00 
HUAWEI DS/4/DATASYNC_CFGCHANGE:OID 1.3.6.1.4.1.2011.5.25.191.3.1 configurations have been changed. The current change number is 5, the change loop count is 0, and the maximum number of records is 4095. Aug 19 2021 15:50:12+08:00
HUAWEI %%01CFM/4/SAVE(s)[0]:The user chose Y when deciding whether to save the configuration to the device.