#  很久没更新了，最近会更新的，别问了

#  CSGO辅助 海王 汉化版
CS:GO Hack - 海王 Chinese version

## 功能
* **自瞄** - 辅助瞄准
* **自动扳机** - 当准星处有敌人时自动开枪
* **回溯** - 放大延迟补偿来提高你的开火容错率
* **发光** - 对实体渲染发光效果
* **上色** - 对玩家模型上色以提升可见度
* **透视** - 显示游戏内各种实体的信息 例如玩家和掉落的武器
* **视觉** - 更多的视觉选项
* **皮肤修改器** - 更换武器、刀和手套的皮肤以及贴纸
* **音频** - 修改某些音效的音量大小
* **样式** - 选择窗口样式以及颜色
* **杂项** - 更多功能
* **举报机器人** - 自动向官方服务器举报玩家
* **配置** - 基于JSON的配置系统

## 如何使用


### 使用

1. 打开`VAC变脑瘫.exe`，会自动重启Steam并关闭vac系统防止被vac封禁
2. 登录Steam账号进入CS:GO
3. 打开`A60-Injector V2.exe`自动将`A60SENSE.dll`注入至CS:GO（请勿修改`A60SENSE.dll`的名字，因为注入器是定向注入，修改名字将导致注入器不生效）


## 常见问题

### 如何打开菜单？
在CS:GO窗口内按下键盘的 <kbd>INSERT</kbd> 键。

### 为什么注入后无法显示中文？
此版本Osiris不支持在非中文环境的Windows以及精简版Windows下使用，如果一定要使用请安装[字体](https://github.com/djkcyl/CSGO-Hack-Osiris-Chinese-version/raw/master/Deng.TTF)

### 我的配置文件存在哪里？
配置文件存在 `Documents` 的 `A60SENSE` 目录里 (`%USERPROFILE%\Documents\A60SENSE`). 配置文件采用可读未加密形式存储 (可以使用各类文本编辑器打开) ，在更新后你需要载入参数并重新保存参数，否则可能会丢失一些功能。

### 使用冥王会不会被封禁？
CSGO目前采用两套封禁机制
1. VAC封禁
2. OW封禁（监管封禁）

# vac不会放过任何一个作弊者

# Osiris

![Windows](https://github.com/danielkrupinski/Osiris/workflows/Windows/badge.svg?branch=master&event=push)
![Linux](https://github.com/danielkrupinski/Osiris/workflows/Linux/badge.svg?branch=master&event=push)

Free and open-source game hack for **Counter-Strike 2**. Compatible with the latest Steam version of the game. Cross-platform - available for Windows and Linux systems.

## What's new

* 16 December 2023 - **Remove Sniper Scope Blur** function was added to **Visuals**
* 6 December 2023 - **Visualize Weapon Reload Sound** function was added to **Sound**
* 2 December 2023 - **Visualize Weapon Scope Sound** function was added to **Sound**
* 23 November 2023 - **Visualize Bomb Defuse** function was added to **Sound**
* 16 November 2023 - **Visualize Bomb Beep** function was added to **Sound**

## Technical features

* C++ runtime library (CRT) is not used in release builds
* No heap memory allocations
* No static imports in release build on Windows
* No threads are created
* Exceptions are not used
* No external dependencies

## Compiling

### Prerequisites

#### Windows

* **Microsoft Visual Studio 2022** with **Desktop development with C++** workload

#### Linux

* **CMake 3.24** or newer
* **g++ 11 or newer** or **clang++ 15 or newer**

### Compiling from source

#### Windows

Open **Osiris.sln** in Visual Studio 2022, set build configuration to **Release | x64**. Press *Build solution* and you should receive **Osiris.dll** file.

#### Linux

Configure with CMake:

    cmake -DCMAKE_BUILD_TYPE=Release -B build

Build:

    cmake --build build -j $(nproc --all)

After following these steps you should receive **libOsiris.so** file in **build/Source/** directory.

### Loading / Injecting into game process

#### Windows

You need a **DLL injector** to inject (load) **Osiris.dll** into game process.

Counter-Strike 2 blocks LoadLibrary injection method, so you have to use a manual mapping (aka reflective DLL injection) injector.

**Xenos** and **Extreme Injector** are known to be **detected** by VAC.

#### Linux

You can simply run the following script in the directory containing **libOsiris.so**:

    sudo gdb -batch-silent -p $(pidof cs2) -ex "call (void*)dlopen(\"$PWD/libOsiris.so\", 2)"

However, this injection method might be detected by VAC as gdb is visible under **TracerPid** in `/proc/$(pidof cs2)/status` for the duration of the injection.

## License

> Copyright (c) 2018-2023 Daniel Krupiński

This project is licensed under the [MIT License](https://opensource.org/licenses/mit-license.php) - see the [LICENSE](https://github.com/danielkrupinski/Osiris/blob/master/LICENSE) file for details.



