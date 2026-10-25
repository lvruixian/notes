1．为什么C+＋比Python多了一步"编译"?●Python像同声传译：写一行代码，运行环境就直接看一行、执行一行，不需要提前打包。
·C+＋像提前印刷成书：你写的．cpp只是纯文本。电脑（CPU）只认识0和1。所以必须请g+＋这个"翻译官"，把你的文本翻译成电脑能懂的可执行文件。
2．那些复杂的编译命令到底在干嘛？
g++check_version.cpp-o check_version $(pkg-config --cflags --libs opencv4)
●g++：翻译官（编译器）。
● check_version.cpp：你写的原稿（源代码）。
●-o check_version：告诉翻译官，把翻译好的结果命名为check_version。
·$(pkg-config…)：告诉翻译官， "OpenCV 的资料库在这个角落，去这里拿材料"（自动配置头文件和链接库路径）。