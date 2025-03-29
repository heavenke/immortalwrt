<img src="https://avatars.githubusercontent.com/u/53193414?s=200&v=4" alt="logo" width="200" height="200" align="right">

# 这个项目来源于immortalwrt官方仓库openwrt-23.05分支
# 仅用于本人学习代码结构之用.

## 关于ImmortalWrt

ImmortalWrt是 [OpenWrt](https://openwrt.org) 的一个分支,移植了更多的软件包，支持更多的设备，并且针对中国大陆用户设置了默认的优化配置文件以及进行了本地化修改.<br/>
与上游相比,我们允许使用(无法合并到上游的)修改/补丁,以提供更好的功能、性能和支持.

默认登录地址: http://192.168.0.1 或 http://immortalwrt.lan, 用户名: __root__, 密码: _无_.

## 开发
要构建你自己的固件,你需要一个GNU/Linux、BSD或MacOSX系统(需要区分大小写的文件系统),由于缺少区分大小写的文件系统,Cygwin不被支持.<br/>

  ### 编译环境需求
  要编译这个项目,首选 Debian 11 系统,并且你需要使用基于AMD64架构的CPU,至少配备4GB内存和25GB可用磁盘空间,确保网络连接可用.

  编译 ImmortalWrt 需要以下工具,软件包名称在不同的发行版中会有所不同.

  - 以下是给Debian/Ubuntu用户的一个示例:<br/>
    - 方法一:
      <details>
        <summary>通过高级软件包工具(APT)安装依赖项</summary>

        ```bash
        sudo apt update -y
        sudo apt full-upgrade -y
        sudo apt install -y ack antlr3 asciidoc autoconf automake autopoint binutils bison build-essential \
          bzip2 ccache clang cmake cpio curl device-tree-compiler ecj fastjar flex gawk gettext gcc-multilib \
          g++-multilib git gnutls-dev gperf haveged help2man intltool lib32gcc-s1 libc6-dev-i386 libelf-dev \
          libglib2.0-dev libgmp3-dev libltdl-dev libmpc-dev libmpfr-dev libncurses-dev libpython3-dev \
          libreadline-dev libssl-dev libtool libyaml-dev libz-dev lld llvm lrzsz mkisofs msmtp nano \
          ninja-build p7zip p7zip-full patch pkgconf python3 python3-pip python3-ply python3-docutils \
          python3-pyelftools qemu-utils re2c rsync scons squashfs-tools subversion swig texinfo uglifyjs \
          upx-ucl unzip vim wget xmlto xxd zlib1g-dev
        ```
      </details>
    - 方法二:
      ```bash
      sudo bash -c 'bash <(curl -s https://build-scripts.immortalwrt.org/init_build_environment.sh)'
      ```

  注意事项:
  - 所有操作都以普通用户身份进行,而不是以root用户身份,且不使用sudo命令.
  - 使用基于其他架构的CPU来编译ImmortalWrt理论上应该也是可行的,但这需要进行更多的修改调整 —— 并且完全不提供任何保证.
  - 你的系统路径(PATH)中或驱动器上的工作文件夹内绝对不能有空格或非ASCII字符.
  - 如果你正在使用适用于Linux的Windows子系统(即WSL),则需要从系统路径(PATH)中移除Windows文件夹,请查看: [基于WSL编译](https://openwrt.org/docs/guide-developer/build-system/wsl) 文档.
  - 不建议使用macOS编译本项目,完全不提供任何保证,你可以从……获取相关提示. [基于macOS编译](https://openwrt.org/docs/guide-developer/build-system/buildroot.exigence.macosx) 文档.
  - 欲了解更多详情,请查看. [编译说明](https://openwrt.org/docs/guide-developer/build-system/install-buildsystem) 文档.

  ### 快速入门
  1. 运行 `git clone -b <branch> --single-branch --filter=blob:none https://github.com/immortalwrt/immortalwrt` 同步本项目源码.
  2. 运行 `cd immortalwrt` 进入项目源码目录.
  3. 运行 `./scripts/feeds update -a` 同步拉取/更新feeds.conf/feeds.conf.default中定义的所有软件源.
  4. 运行 `./scripts/feeds install -a` 将拉取到的软件包创建软链接到package/feeds/目录中.
  5. 运行 `make menuconfig` 为工具链、目标系统以及固件软件包选择你偏好的配置.
  6. 运行 `make` 编译固件,这将下载所有的源代码,编译交叉编译工具链,然后针对你的目标系统对GNU/Linux内核以及所有选定的软件包进行交叉编译.

  ### 相关软件源
  主软件源使用多个子软件源来管理不同类别的软件包,所有软件包都通过名为opkg的OpenWrt软件包管理器进行安装,如果你希望开发Web界面或将软件包移植到ImmortalWrt,请在下方找到合适的软件源.
  - [LuCI Web Interface](https://github.com/immortalwrt/luci): 通过浏览器控制设备的现代且模块化的界面.
  - [ImmortalWrt Packages](https://github.com/immortalwrt/packages): 已移植软件包的社区软件源.
  - [OpenWrt Routing](https://github.com/openwrt/routing): 专注于(MESH)路由的软件包.
  - [OpenWrt Video](https://github.com/openwrt/video): 专注于显示服务器和客户端(Xorg和Wayland)的软件包.

## 支持信息
有关受支持设备的列表,请查看 [OpenWrt硬件数据库](https://openwrt.org/supported_devices)
  ### 文档
  - [快速入门指南](https://openwrt.org/docs/guide-quick-start/start)
  - [用户指南](https://openwrt.org/docs/guide-user/start)
  - [开发者文档](https://openwrt.org/docs/guide-developer/start)
  - [技术参考资料](https://openwrt.org/docs/techref/start)

  ### 支持社区
  - 支持聊天:群组 [@ctcgfw_openwrt_discuss](https://t.me/ctcgfw_openwrt_discuss) on [Telegram](https://telegram.org/).
  - 支持聊天:群组 [#immortalwrt](https://matrix.to/#/#immortalwrt:matrix.org) on [Matrix](https://matrix.org/).

## 许可证
ImmortalWrt 根据 [GPL-2.0许可证(仅)](https://spdx.org/licenses/GPL-2.0-only.html) 进行授权.

## 鸣谢
<table>
  <tr>
    <td><a href="https://dlercloud.com/"><img src="https://user-images.githubusercontent.com/22235437/111103249-f9ec6e00-8588-11eb-9bfc-67cc55574555.png" width="183" height="52" border="0" alt="Dler Cloud"></a></td>
    <td><a href="https://www.jetbrains.com/"><img src="https://resources.jetbrains.com/storage/products/company/brand/logos/jb_square.png" width="120" height="120" border="0" alt="JetBrains Black Box Logo logo"></a></td>
    <td><a href="https://sourceforge.net/"><img src="https://sourceforge.net/sflogo.php?type=17&group_id=3663829" alt="SourceForge" width=200></a></td>
  </tr>
</table>
