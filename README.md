# Sakiyary$ Infinite 2048 

​		——211850016 写于2021/12/15晚

## 一.  编译环境与选项

1. 请先配置好**`SDL2`+`SDL2_image`+`SDL2_ttf`**的环境，**Linux**下可直接通过命令行配置，**Windows**下可参考自制的[配置SDL2环境的教程](https://www.bilibili.com/video/BV1oq4y1q72r)。

2. **Linux**下命令行编译请使用：

   ````bash
   gcc Sakiyary_2048.c -o Sakiyary_2048 -lSDL2main -lSDL2 -lSDL2_image -lSDL2_ttf 
   ````

   **Windows**下命令行编译请使用：

   ````bash
   gcc Sakiyary_2048.c -o Sakiyary_2048 -lmingw32 -lSDL2main -lSDL2 -lSDL2_image -lSDL2_ttf 
   ````
   
   使用**Clion**编译时，请注意文件夹中的`CMakeLists.txt`。
   
   若在**Linux**下需将`target_link_libraries(Sakiyary_2048 mingw32)`一行**注释**掉。**Windows**下可直接使用。
   
   另外，使用**Clion**编译时，请先点开右上角“锤子键”与“运行键”之间的配置，点击**编辑配置**，在跳出的窗口中将**“工作目录”**那一栏改为本文件的**绝对路径**。
   
   详情可见自制的[SDL2教程的p2中06:35](https://www.bilibili.com/video/BV1QZ4y197Yk?p=2)所演示。



##二. 游戏指南

1. 当您运行游戏，在您面前呈现的是**开始界面**。

   此时，您可通过**鼠标点击"START"**或**按下"Enter"回车键**或**按下空格键**来进入游戏。

   也可以通过**按下"Esc"键**或**鼠标点击窗口右上角的"×"**来退出游戏。

   

 2. 第一次进入**游戏界面**，在您面前呈现的是**供测试与演示用**的几乎填满的游戏面板。

   您可以通过**按下"w" "a" "s" "d"键**或**按下方向键**或在窗口内**上下左右拖动鼠标一定距离以上**(>100pt)来进行**2048**的**数字移动操作**。

   

 3. 您在**游戏界面**正常游玩时也可以随时进行以下**操作**：

   

   (1). 通过**按下"Esc"键**或**按下"Backspace"键**或**鼠标点击"退出"图标**来退回到**开始界面**，此时游戏面板与游戏时长将不会发生改变。
   
   
   
   (2). 通过**按下"z"键**或**鼠标点击"撤回"图标**来返回上一步。注意，您只能**撤回一步**，且**不产生数字移动的操作**并不会记录为"上一步"。开始游戏/重开游戏后的**第一步操作前**是不能撤回的。
   
   
   
   (3). 通过**按下"r"键**或**鼠标点击"重置"图标**来重开游戏，此时您的游戏分数与游戏时长会**清零**，但最高分不会。
   
   
   
   (4). 通过**按下"Space"空格键**或**鼠标点击"暂停"图标**来暂停游戏，此时会有**游戏暂停对话框**呈现在您的面前。
   
   
   
   (5). 通过**按下"Enter"回车键**来随机方向进行一次**数字移动操作**。此操作必定会**产生数字移动**。
   
   
   
 4. 游戏共有三种**对话框**，**对话框**出现时，您在游玩时可进行的操作将无效化，且暂停游戏时长记录(即对话框停留的时长**不会计入**游戏时长中)。三种**对话框**及操作分别为：

   

   (1). 游戏结束对话框：当您游玩时进行完一次**数字移动操作**，且新的数字**随机生成**后，系统判定您游戏已经无法继续时，此对话框会出现在您的眼前。您此时有三个选项：**退回开始界面**(按下"Esc"键或按下"Backspace"键或鼠标点击"退出"图标，此操作**会**重置游戏面板)，**撤回一步**(按下"z"键或鼠标点击"撤回"图标)，**重新开始**(按下"r"键或鼠标点击"重置"图标)。

   

   (2). 游戏胜利对话框：当您游玩时进行完一次**数字移动操作**，在本局游戏中**第一次**成功合成出**2048**这个数字时，此对话框会出现在您的眼前。您此时有三个选项：**退回开始界面**(按下"Esc"键或按下"Backspace"键或鼠标点击"退出"图标，此操作**不会**重置游戏面板)，**继续游戏**(按下"Space"空格键或鼠标点击"继续"图标)，**重新开始**(按下"r"键或鼠标点击"重置"图标)。若您选择了**继续游戏**(包括退回开始界面再重进)，当您第二次及更多次合成出**2048**时，此对话框**不会**再次出现。在开始界面停留的时长同样**不会计入**游戏时长中。

   

   (3). 游戏暂停对话框：出现条件如**二.3.(4)**所写。您此时有三个选项：**退回开始界面**(按下"Esc"键或按下"Backspace"键或鼠标点击"退出"图标，此操作**不会**重置游戏面板)，**继续游戏**(按下"Space"空格键或鼠标点击"继续"图标)，**重新开始**(按下"r"键或鼠标点击"重置"图标)。在开始界面停留的时长同样**不会计入**游戏时长中。

   

 5. 每一次**产生数字移动**的**数字移动操作**之后所随机生成的新的数字，90%为"2"，10%为"4"。

   

 6. 当您合并出大于**65536**的数时，该数字方块将会显示为纯黑，但其本质与所计分数不会改变。

   

 7. 实测用部分Linux系统(Ubuntu)来运行时**鼠标类**的交互会非常卡顿，不明原因。



8. 当您在游玩中进行某些窗口外操作(如按下**Ctrl+Alt+Delete**调出任务管理器)，会让游戏卡死，此时只能关闭窗口再重开。



## 三. 作者叨叨

​	图形库真好(fan)玩(suo)！

​	有些地方不可避免地写成了屎山(大片的switch-case)，但我还是尽力缩减重复代码了。例如加载图片时用指针数组来循环加载数字图片、将四种方向的移动(用大量的三目运算符)统一进一个函数(写报告的时候发现我是不是可以用数组旋转来避免可读性很差的三目运算符呢，说不定会优化一下)、统一对话框在一个函数中等等。

​	所有随机数所用种子为`srand((unsigned)time(NULL))`，并用类似于`rand()>RAND_MAX/2`而不是`rand()%2`的判断语句来进行随机的操作。

​	内存巨大泄漏的bug应该已经修复，但我测试时还是会占用100MB左右的内存，不知道该如何缩减。随着游玩时间的增加，内存占用会缓慢上升，玩10分钟后会占用到400MB以上，且不会减少，不知该如何优化。(21/12/20更新: 可能已修复，见下)

​	这次是全程使用了git，虽说没有/remake过，但确实在写代码的时候变得很安心。

​	所有图形，除了温迪人物相关与背景，均为自制，有git存档与工程文件.psd留档。

​	感谢游玩！





2021/12/17更新: 本来的Move函数是用三目运算符堆出来的(如下)，可读性实在是不忍直视，故更新了代码，改用了数组旋转。

```c
void Move(int Dir1, int Dir2) {
    for (int i = 0; i < 4; ++i) {
        if (!Map[Dir1 ? 0 : i][Dir1 ? i : 0] && !Map[Dir1 ? 1 : i][Dir1 ? i : 1] && !Map[Dir1 ? 2 : i][Dir1 ? i : 2] && !Map[Dir1 ? 3 : i][Dir1 ? i : 3])
            continue;
        for (int j = Dir2 ? 0 : 3; (Dir2 && j < 3) || (!Dir2 && j > 0); j += Dir2 ? 1 : -1)
            for (int k = 0; (Dir2 && k < 3 - j) || (!Dir2 && k < j); ++k)
                if (!Map[Dir1 ? j : i][Dir1 ? i : j]) {
                    for (int l = j; (Dir2 && l < 3) || (!Dir2 && l > 0); l += Dir2 ? 1 : -1)
                        Map[Dir1 ? l : i][Dir1 ? i : l] = Map[Dir1 ? (Dir2 ? l + 1 : l - 1) : i][Dir1 ? i : (Dir2 ? l + 1 : l - 1)];
                    Map[Dir1 ? (Dir2 ? 3 : 0) : i][Dir1 ? i : (Dir2 ? 3 : 0)] = 0;
                }
        for (int j = Dir2 ? 0 : 3; (Dir2 && j < 3) || (!Dir2 && j > 0); j += Dir2 ? 1 : -1) {
            if (Map[Dir1 ? j : i][Dir1 ? i : j] == Map[Dir1 ? (Dir2 ? j + 1 : j - 1) : i][Dir1 ? i : (Dir2 ? j + 1 : j - 1)] && Map[Dir1 ? j : i][Dir1 ? i : j] != 0) {
                Map[Dir1 ? j : i][Dir1 ? i : j]++;
                Score += 1 << Map[Dir1 ? j : i][Dir1 ? i : j];
                BestScore = BestScore < Score ? Score : BestScore;
                if (Map[Dir1 ? j : i][Dir1 ? i : j] == 11 && !IfWin)IfWin = 1;
                for (int k = Dir2 ? j + 1 : j - 1; (Dir2 && k < 3) || (!Dir2 && k > 0); k += Dir2 ? 1 : -1)
                    Map[Dir1 ? k : i][Dir1 ? i : k] = Map[Dir1 ? (Dir2 ? k + 1 : k - 1) : i][Dir1 ? i : (Dir2 ? k + 1 : k - 1)];
                Map[Dir1 ? (Dir2 ? 3 : 0) : i][Dir1 ? i : (Dir2 ? 3 : 0)] = 0;
                IfMove = 1;
            }
        }
    }
}
```



2021/12/20更新1: 在翻SDL2库的时候发现一个美妙的函数：

````c
SDL_COMPILE_TIME_ASSERT(SDL_Event, sizeof(SDL_Event) == sizeof(((SDL_Event *) NULL)->padding));
````

按照我的理解，此函数可以更新事件队列与内部输入状态，感觉和`fflush()`有相似之处(?)。

运用此函数后程序整体内存占用可以动态控制在60MB左右。

但是当快速按下方向键或wasd时操作还是会记录每一个操作并按序反应出来(虽说在本游戏问题并不大)。



2021/12/20更新2: 试图写成多文件联合，但由于一开始接口没做好，现在改动太复杂了，故只把定义都集中到了`Sakiyary_2048.h`中。
