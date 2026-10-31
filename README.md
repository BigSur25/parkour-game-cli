# 跑酷小游戏

终端上的跑酷闯关 — 上下跳跃切换三轨道躲避怪物、攒经验、放技能、打 Boss，七波通关。

```
  ↑ ↓   跳跃 / 下翻
  ← →   左右微调（松手回正）
 空格   暂停
```

## 模式

启动时二选一：

| 模式 | 说明 |
|---|---|
| **1. 普通模式** | 随机种子，每局都不同 |
| **2. 每日挑战** | 当天日期作 `srand` 种子，同一天全球玩家面对同一套关卡波次 |

通关后保存本机 Top 5 速通计时：
- 普通模式 → `parkour_classic.txt`
- 每日挑战 → `parkour_daily.txt`

跟朋友约好同一天玩每日挑战就能比同一份关卡的通关时间。

## 编译

需要支持 C++17 的编译器。代码用到了 `<windows.h>` + `<conio.h>` 与一些Unicode方框字符，**只在 Windows 上编译运行**。

### MinGW / Dev-C++

```bash
g++ -std=c++17 -O2 C_Windows.cpp -o game.exe
./game.exe
```

### MSVC (Developer Command Prompt)

```bat
cl /EHsc /std:c++17 C_Windows.cpp
```

> 控制台默认字体里 `┻ ┿ ▄ ┃ ◥ ◤ ╱ ╲` 这类字符偶尔会显示成方块，换字体为 "新宋体" / "Consolas" 或开 " Cascadia Code" 都行。

## 文件

| 文件 | 说明 |
|---|---|
| `C_Windows.cpp` | Windows 主程序（推荐） |
| `C.cpp` | macOS 适配版（POSIX termios + ANSI 转义） |
| `C_backup_original.cpp` | 原始版本备份 |

macOS 玩家编译 `C.cpp`：

```bash
g++ -std=c++17 -O2 C.cpp -o game
./game
```

## 自定义参数

启动时选 `1` 开启自定义，可以调：游戏速度、经验量、Boss 血量、道具持续时间、初始技能、Boss 顺序等。

## 系统

- Win10 1809+（需要控制台 VT processing 支持 ANSI 转义）
- 或 macOS 10.15+（编 `C.cpp`）


## Credits & Acknowledgements / 致谢

This project (`parkour-game-cli`) is a macOS terminal port based on the original C++ logic and framework provided by my classmate and his Luogu team. 

I have refactored the code, adapted it for the macOS terminal environment, and added new parkour gameplay features. 

Special thanks to them for offering the original code and the foundation for this project!

本项目基于我同班同学及其洛谷（Luogu）团队提供的原始 C++ 代码与逻辑框架修改而来。

我在此基础上进行了重构，将其移植到了 macOS 终端环境，并添加了新的跑酷玩法。

特别感谢他们提供的原始代码和项目灵感！没有他们踩过的坑，就没有这个终端版游戏。
