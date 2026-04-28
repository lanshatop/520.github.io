[https://docs.zlmediakit.com/zh/](https://docs.zlmediakit.com/zh/)

# 快速开始

[[ZLMediaKit](https://docs.zlmediakit.com/)](https://docs.zlmediakit.com/)2023年10月9日大约 4 分钟

---

此页内容

- [[构建环境](https://docs.zlmediakit.com/zh/tutorial/#%E6%9E%84%E5%BB%BA%E7%8E%AF%E5%A2%83)](https://docs.zlmediakit.com/zh/tutorial/#构建环境)
- *   [[支持 C++11 的编译器](https://docs.zlmediakit.com/zh/tutorial/#%E6%94%AF%E6%8C%81-c-11-%E7%9A%84%E7%BC%96%E8%AF%91%E5%99%A8)](https://docs.zlmediakit.com/zh/tutorial/#支持-c-11-的编译器)
    - [[CMake](https://docs.zlmediakit.com/zh/tutorial/#cmake)](https://docs.zlmediakit.com/zh/tutorial/#cmake)
- [[获取代码](https://docs.zlmediakit.com/zh/tutorial/#%E8%8E%B7%E5%8F%96%E4%BB%A3%E7%A0%81)](https://docs.zlmediakit.com/zh/tutorial/#获取代码)
- *   [[安装依赖库](https://docs.zlmediakit.com/zh/tutorial/#%E5%AE%89%E8%A3%85%E4%BE%9D%E8%B5%96%E5%BA%93)](https://docs.zlmediakit.com/zh/tutorial/#安装依赖库)
- [[构建与编译 ZLMediaKit](https://docs.zlmediakit.com/zh/tutorial/#%E6%9E%84%E5%BB%BA%E4%B8%8E%E7%BC%96%E8%AF%91-zlmediakit)](https://docs.zlmediakit.com/zh/tutorial/#构建与编译-zlmediakit)
- [[运行 ZLMediaKit](https://docs.zlmediakit.com/zh/tutorial/#%E8%BF%90%E8%A1%8C-zlmediakit)](https://docs.zlmediakit.com/zh/tutorial/#运行-zlmediakit)
- *   [[MediaServer 进程](https://docs.zlmediakit.com/zh/tutorial/#mediaserver-%E8%BF%9B%E7%A8%8B)](https://docs.zlmediakit.com/zh/tutorial/#mediaserver-进程)
    - [[C 接口的 SDK](https://docs.zlmediakit.com/zh/tutorial/#c-%E6%8E%A5%E5%8F%A3%E7%9A%84-sdk)](https://docs.zlmediakit.com/zh/tutorial/#c-接口的-sdk)
    - [[以 test_ 开头的测试程序](https://docs.zlmediakit.com/zh/tutorial/#%E4%BB%A5-test-%E5%BC%80%E5%A4%B4%E7%9A%84%E6%B5%8B%E8%AF%95%E7%A8%8B%E5%BA%8F)](https://docs.zlmediakit.com/zh/tutorial/#以-test-开头的测试程序)
- [[推流测试](https://docs.zlmediakit.com/zh/tutorial/#%E6%8E%A8%E6%B5%81%E6%B5%8B%E8%AF%95)](https://docs.zlmediakit.com/zh/tutorial/[#](https://docs.zlmediakit.com/zh/tutorial/#%E6%9E%84%E5%BB%BA%E7%8E%AF%E5%A2%83)推流测试)

本教程将指导您完成编译和运行 ZLMediaKit。

## [#](https://docs.zlmediakit.com/zh/tutorial/#构建环境)构建环境

新手提示

如果你是位新手，强烈建议使用 Ubuntu16 以上版本编译 ZLMediaKit，macOS 是次选推荐平台。不推荐使用 CentOS6.x 或 windows 构建与使用。

vcpkg

ZLMediaKit 已上架 vcpkg，便捷安装请参考 [[vcpkg 安装 ZLMediaKit](https://docs.zlmediakit.com/zh/guide/install/install_zlmediakit_using_vcpkg.html)](https://docs.zlmediakit.com/zh/guide/install/install_zlmediakit_using_vcpkg.html)。

[#](https://docs.zlmediakit.com/zh/tutorial/#%E6%94%AF%E6%8C%81-c-11-%E7%9A%84%E7%BC%96%E8%AF%91%E5%99%A8)## [#](https://docs.zlmediakit.com/zh/tutorial/#支持-c-11-的编译器)支持 C++11 的编译器

ZLMediaKit 采用了 C++11 的语法和库，要求编译器支持完整的 C++11 标准：

- Linux: gcc >= 4.8 (4.7 应该也能支持)
- macOS: Clang >= ??? (我也不知道，估计大部分不会遇到这个问题)
- Windows: Visual Studio >= 2015 (vs2013 某些版本也能编译通过，如果怕麻烦建议直接 vs2017)

Debian 系 (包括 Ubuntu)CentOS7+CentOS 6.xmacOSWindows

```Bash
sudo apt install build-essential
```

[#](https://docs.zlmediakit.com/zh/tutorial/#cmake)## [#](https://docs.zlmediakit.com/zh/tutorial/#cmake)CMake

ZLMediaKit 采用 CMake 来构建项目，所以编译需要 CMake。

Debian 系 (包括 Ubuntu)CentOS7+CentOS 6.xmacOSWindows

```Bash
sudo apt install cmake
```

[#](https://docs.zlmediakit.com/zh/tutorial/#%E8%8E%B7%E5%8F%96%E4%BB%A3%E7%A0%81)# [#](https://docs.zlmediakit.com/zh/tutorial/#获取代码)获取代码

使用 Git 克隆 ZLMediaKit 的代码并初始化子模块：

```Markdown
# 国内用户推荐从 Gitee 下载git clone --depth 1 https://gitee.com/xia-chu/ZLMediaKitcd ZLMediaKit# 初始化子模块 （必须执行）git submodule update --init
```

注意

不能通过下载 zip 包的方式下载源码。因为 ZLMediaKit 依赖于第三方代码并通过 Git 子模块的方式管理。

[#](https://docs.zlmediakit.com/zh/tutorial/#%E5%AE%89%E8%A3%85%E4%BE%9D%E8%B5%96%E5%BA%93)## [#](https://docs.zlmediakit.com/zh/tutorial/#安装依赖库)安装依赖库

ZLMediaKit 依赖一些可选的第三方库。构建时，CMake 将在 path 中查找这些库，并根据检测情况决定是否开启相关特性。

- openssl

    你需要在编译前安装 openssl 库以使用相关功能。

    - flash player 播放 rtmp
    - https/rtsps/webrtc 相关功能。
- ffmpeg

    ZLMediaKit 可以通过 fork ffmpeg 进程的方式实现多种协议的拉流，编译时不需要安装 FFmpeg。
- sdl、avcodec、avutil

    这 3 个库供 ZLMediaKit 的 test_player 测试程序使用，你通常不需要安装这 3 个库。

Debian 系 (包括 Ubuntu)CentOS7+CentOS 6.xmacOSWindows

除了 openssl，其他都是可选的:

```Bash
sudo apt install libssl-devsudo apt install libsdl-devsudo apt install libavcodec-devsudo apt install libavutil-devsudo apt install ffmpeg
```

[#](https://docs.zlmediakit.com/zh/tutorial/#%E6%9E%84%E5%BB%BA%E4%B8%8E%E7%BC%96%E8%AF%91-zlmediakit)# [#](https://docs.zlmediakit.com/zh/tutorial/#构建与编译-zlmediakit)构建与编译 ZLMediaKit

webrtc

由于功能复杂，默认情况下不开启编译 webrtc，可参考 [[编译与使用 webrtc](https://docs.zlmediakit.com/zh/guide/protocol/webrtc/webrtc_compilation_and_use.html)](https://docs.zlmediakit.com/zh/guide/protocol/webrtc/webrtc_compilation_and_use.html)

LinuxmacOSWindowsAndroidiOS

```Bash
cd ZLMediaKitmkdir buildcd buildcmake ..make -j4
```

[#](https://docs.zlmediakit.com/zh/tutorial/#%E8%BF%90%E8%A1%8C-zlmediakit)# [#](https://docs.zlmediakit.com/zh/tutorial/#运行-zlmediakit)运行 ZLMediaKit

ZLMediaKit 工程主要生成 3 种二进制目标文件，他们的生成的路径在 release 目录下。

[#](https://docs.zlmediakit.com/zh/tutorial/#mediaserver-%E8%BF%9B%E7%A8%8B)## [#](https://docs.zlmediakit.com/zh/tutorial/#mediaserver-进程)MediaServer 进程

这是 ZLMediaKit 作为服务器的主进程，该进程可以在免去开发的情况下直接作为测试流媒体服务器使用。

如果你需要更复杂的业务逻辑，可以通过 [[Web HOOK](https://docs.zlmediakit.com/zh/guide/media_server/web_hook_api.html)](https://docs.zlmediakit.com/zh/guide/media_server/web_hook_api.html)和 [[RESTful API](https://docs.zlmediakit.com/zh/guide/media_server/restful_api.html)](https://docs.zlmediakit.com/zh/guide/media_server/restful_api.html)实现。你可以通过 [[配置文件](https://docs.zlmediakit.com/zh/guide/media_server/config_file.html)](https://docs.zlmediakit.com/zh/guide/media_server/config_file.html) 控制其参数。

LinuxmacOSWindows

```Bash
cd ZLMediaKit/release/linux/Debug[#](https://docs.zlmediakit.com/zh/tutorial/#c-%E6%8E%A5%E5%8F%A3%E7%9A%84-sdk) 通过 -h 可以了解启动参数./MediaServer -h# 以守护进程模式启动./MediaServer -d &
```

### [#](https://docs.zlmediakit.com/zh/tutorial/#c-接口的-sdk)C 接口的 SDK

ZLMediaKit 同时提供 C 接口的 SDK 库。

头文件位于 `ZLMediaKit/api/include`，有详细的注释，一般足够二次开发使用。

库文件为:

LinuxmacOSWindows

```C++
ZLMediaKit/release/linux/Debug/libmk_api.so
```

[#](https://docs.zlmediakit.com/zh/tutorial/#%E4%BB%A5-test-%E5%BC%80%E5%A4%B4%E7%9A%84%E6%B5%8B%E8%AF%95%E7%A8%8B%E5%BA%8F)## [#](https://docs.zlmediakit.com/zh/tutorial/#以-test-开头的测试程序)以 `test_` 开头的测试程序

相关代码在 `ZLMediaKit/tests` 目录下，你可以对照代码启动测试进程。

[#](https://docs.zlmediakit.com/zh/tutorial/#%E6%8E%A8%E6%B5%81%E6%B5%8B%E8%AF%95)# [#](https://docs.zlmediakit.com/zh/tutorial/#推流测试)推流测试

请参考 [[推流播放测试](https://docs.zlmediakit.com/zh/guide/media_server/push_test.html)](https://docs.zlmediakit.com/zh/guide/media_server/push_test.html)。