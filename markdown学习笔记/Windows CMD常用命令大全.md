# 常用的

1.cd /? #查询命令cd的用法
2.color /? #查询命令color的用法
在命令后面加上/?即可查询该命令的用法，对一个经常使用命令行的人而言这是最重要的
3.start #该命令会再打开一个命令提示符窗口
4. assoc #显示文件扩展关联(即什么样的后缀名用什么样的软件打开)
5. cd \ #跳转到硬盘的根目录
6. cd C:\WINDOWS  //跳转到当前硬盘的其他文件
7. 将当前目录切换为D盘的桌面 文件夹
   cd /d d:\桌面 
   cd /d d:\大三上学期
   或：
   d:
   输入d下面的目录
>- //查看当前目录下的文件，类似于linux下的ls
 dir
8. cd /d c:\Users\ASUS\ #回到原用户目录
   或： c：
8.cd..  #跳至当前目录上一级
9. cd /?  #查询命令cd的用法
10. cls #清除当前屏幕内容
11. dir #显示当前目录下的子目录与文件的列表
>-  del 文件完整路径or目录路径 #是文件路径则删除文件；如果是目录，则删除目录中所有文件，但目录本身保留

>- rd(rmdir) #移除一个空目录，非空目录无法移除
>- md 目录名（文件夹） #创建目录

>- date #显示当前日期并修改，若显示“当前客户端没有所需特权”，则以管理员身份启动命令提示符即可
>- time #显示系统时间，并且可以更改时间，与date命令类似
>-  title #更改命令提示符窗口的标题(原力与你同在may the force be with you)

>-  move /-Y d:\GAME\1.8.5\test.txt d:\GAME\ #移动文件text.txt，将其从 d:\GAME\1.8.5\移至d:\GAME\，/-Y表示移动后将覆盖已有同名文件，没有/-Y则命令行会询问你是否覆盖

>- copy 路径\文件名 路径\文件名 ：把一个文件拷贝到另一个地方。 

>- mkdir d:\GAME\test_b #在d:\GAME\中创建子目录test_b (新建文件夹)
>- ren(rename) #重命名文件 例:ren d:\GAME\test_b\test.txt dashabi.txt

>- exit #退出命令提示符程序

>- ipconfig #查看本机ip
>- ping 主机名 ；eg： ping LAYLINS

>- find /？获取使用帮助

>- systeminfo 查看系统信息
