---
title: 【Godot】Godot 引擎学习笔记
categories:
- 学习
- 游戏
tags:
- 游戏引擎
- Godot
---

# Godot 引擎学习笔记



## 足迹

。。。

核心概念：场景，节点，树，信号。简单来说就是一个巨大的树。

目前为止，有一说一，相比通过看视频学 Unity 哪会，现在通过看文档感觉更适合我的节奏。

界面：项目管理器、Godot 编辑器。

## 源码

研究源码环节，目前，使用 VSCode（插件：C/C++，clangd）、MinGW-w64/GCC、SCons、cppdbg，达成了对源码进行编译、运行、调试。

跑`scons platform=windows compiledb=yes -j6`语句，为了生成 compile_commands.json 文件

控制台输出与 debug 断点的路径。

```c++
	{
		AllocConsole();
		freopen("CONOUT$", "w", stdout);
		freopen("CONOUT$", "w", stderr);
		printf("ccc111ccc\n");
	}
```

> C++ 工程开发
>
> - 开发工具（IDE）：VSCode、VS
> - 编译器与工具链：MSVC、MinGW-w64/GCC、Clang
> - 构建系统：CMake、Makefile、SCons
> - 编译链接：（tasks.json：g++、cl、scons）
> - 调试：GCB、LLDB、Visual Studio Debugger、(launch.json：cppdbg、cppvsdbg)

> VSCode，clangd 插件：链接标准库
>
> VSCode 的 setting.json 中：
>
> ```json
>     "clangd.arguments": [
>         "--query-driver=C:\\Program Files\\mingw64\\x86_64-15.2.0-release-win32-seh-ucrt-rt_v13-rev0\\mingw64\\bin\\g++.exe",
>     ]
> ```
>
> 然后在`%LocalAppData%\clangd`下创建文件`config.yaml`，并写入：
>
> ```yaml
> CompileFlags:
>   Add:
>     - --target=x86_64-w64-windows-gnu
> ```
>

## GDExtension

以下全程在 cursor 的指导下。

1. 使用 SCons 创建 C++ 工程。

2. 使用 `git submodule add https://github.com/godotengine/godot-cpp.git modules/godot-cpp`语句将 godot-cpp 作为依赖引入。

3. 将项目根目录的 `SConstruct` 改成可直接编译 `godot-cpp` 静态库并链接 `src/*.cpp`。之后编译。生成 compile_commands.json 文件。

   ```
   scons platform=windows target=template_debug mode=debug -j6
   scons platform=windows compiledb=yes -j6
   ```

4. 将生成的 dll 加载到 Godot 项目。

   ```
   [configuration]
   entry_symbol = "example_library_init"	// 对应 register_types.cpp 下的 example_library_init
   compatibility_minimum = "4.2"
   
   [libraries]
   windows.debug.x86_64 = "res://bin/windows/mirror.windows.template_debug.x86_64.dll"
   windows.release.x86_64 = "res://bin/windows/mirror.windows.template_release.x86_64.dll"
   ```

5. 函数调用测试。通过 ClassDB 类，可以用类似 Java 反射的方法操作对象。

   ```
   RefCounted runner = ClassDB.Instantiate("MirrorRunner").AsGodotObject() as RefCounted;
   runner.Call("test","abc");
   ```

6. 成功创建一个自定义类。

7. 1







