# GradleStudy
GradleStudy

## 给Gradle相关文件添加了注释

### Gradle 设置文件

`settings.gradle` 文件位于项目的根目录下，用于定义项目级代码库设置，并告知 Gradle 在构建应用时应将哪些模块包含在内。
在这个文件中，还添加了 **配置项目全局属性**

### 顶层 build 文件

顶层 `build.gradle` 文件位于项目的根目录下，用于定义适用于项目中所有模块的依赖项。默认情况下，顶层 build 文件使用 plugins 代码块定义项目中所有模块共用的 Gradle 依赖项。此外，顶层 build 文件还包含用于清理 build 目录的代码。

### 模块级 build 文件
模块级 `build.gradle` 文件位于每个 project/module/ 目录下，用于为其所在的特定模块配置 build 设置。您可以通过配置这些 build 设置提供自定义打包选项（如额外的 build 类型和产品变种），以及覆盖 main/ 应用清单或顶层 build.gradle 文件中的设置。

### Gradle 属性文件

- `gradle.properties`  可以在这里配置项目全局 Gradle 设置，如 Gradle 守护程序的最大堆大小。如需了解详情，请参阅[构建环境](https://docs.gradle.org/current/userguide/build_environment.html)。
- `local.properties` 为构建系统配置本地环境属性，其中包括：
  1. `ndk.dir` - NDK 的路径。此属性已被废弃。NDK 的所有下载版本都将安装在 Android SDK 目录下的 `ndk` 目录中。
  2. `sdk.dir` - SDK 的路径。
  3. `cmake.dir` - CMake 的路径。
  4. `ndk.symlinkdir` - 在 Android Studio 3.5 及更高版本中，创建指向 NDK 的符号链接，该符号链接的路径可比 NDK 安装路径短

### 将 NDK 重新映射到较短的路径（仅限 Windows）

Windows 长路径最常见的问题就是 NDK 安装文件夹中的工具（如 ld.exe）会产生非常深的路径，但工具对于长路径的支持并不佳。

在 local.properties 中，您可以设置 ndk.symlinkdir 属性以请求 Gradle 插件创建指向 NDK 的符号链接。该符号链接的路径可比现有 NDK 文件夹的路径短。例如，ndk.symlinkdir = C:\ 将生成以下符号链接：C:\ndk\19.0.5232133