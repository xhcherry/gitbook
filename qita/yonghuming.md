# windows修改中文用户名

运行(快捷键Win+R)窗口，输入 regedit 命令，确定或回车，可以快速打开注册表编辑器

![](<../.gitbook/assets/image (178).png>)

依次点开HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion**

找到**RegisteredOwner

![](<../.gitbook/assets/image (195).png>)

**双击打开这个名称直接修改数值数据即可**

![](<../.gitbook/assets/image (179).png>)

然后定位到HKEY\_LOCAL\_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\ProfileList这个位置

profilelist里面的文件夹数量不固定，都点开看看，其中有一个如下图红线部分最后的数值栏就是需要修改的位置

![](<../.gitbook/assets/image (192).png>)

双击profilelmagepath打开后修改如下图的数值数据一栏，将最后的名字修改成英文就行

![](<../.gitbook/assets/image (185).png>)

以上完成后右键开始菜单，选择关机或注销，选择注销

注销后重新登录进桌面，这时会报错，直接关闭对话框，不要重启或注销！！

win+e打开资源管理器，左边菜单栏选择此电脑，进入c盘进入用户文件夹

把你曾经的中文名的文件夹改成修改后的英文用户名即可
