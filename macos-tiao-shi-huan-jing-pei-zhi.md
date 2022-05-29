# 🐛 macOS调试环境配置

## 下载GDB

可以在其官网或镜像下载最新的GDB源码包，本文以GDB 12.1为目标编写

{% embed url="https://ftp.gnu.org/gnu/gdb/" %}
GDB下载地址
{% endembed %}

完成后应该可以在下载文件夹中找到源码包gdb-12.1.tar.xz

## 安装依赖

编译安装GDB需要安装GMP，本文以GMP 6.2.1为目标编写

```bash
brew install gmp
```

编译含Python支持的GDB需要安装Python，本文以Python 3.9.13为目标编写

```bash
brew install python@3.9
```

列出使用brew安装的包，检查依赖是否安装完成

```bash
brew list
```

## 配置编译

假设源码包在下载文件夹中，解压gdb-12.1.tar.xz安装包，并进入目录

```bash
cd ~/Downloads/gdb-12.1
```

新建构建文件夹，并进入目录

```bash
mkdir build
cd build
```

在简介文件\~/Downloads/gdb-12.1/gdb/README中可以查看配置参数

```bash
../configure --prefix=/usr/local --with-python=/usr/local/Cellar/python@3.9/3.9.13_1/libexec/bin/python --target=riscv64-unknown-elf --enable-tui=yes --enable-werror=no
```

## 编译代码

```
make -j$(sysctl -n hw.ncpu)
```

## 编译安装

```bash
make install
```

完成之后可以在/usr/local/bin文件下找到可执行文件riscv64-unknown-elf-gdb

检查编译参数是否正确

```bash
riscv64-unknown-elf-gdb --configuration
```

运行后输出应该类似如下

```
This GDB was configured as follows:
   configure --host=x86_64-apple-darwin21.5.0 --target=riscv64-unknown-elf
	     --with-auto-load-dir=:${prefix}/share/auto-load
	     --with-auto-load-safe-path=:${prefix}/share/auto-load
	     --with-expat
	     --with-gdb-datadir=/usr/local/share/gdb (relocatable)
	     --with-jit-reader-dir=/usr/local/lib/gdb (relocatable)
	     --without-libunwind-ia64
	     --with-lzma
	     --without-babeltrace
	     --without-intel-pt
	     --without-mpfr
	     --without-xxhash
	     --with-python=/usr/local/opt/python@3.9/Frameworks/Python.framework/Versions/3.9 (relocatable)
	     --with-python-libdir=/usr/local/opt/python@3.9/Frameworks/Python.framework/Versions/3.9/lib (relocatable)
	     --without-debuginfod
	     --without-guile
	     --disable-source-highlight
	     --with-separate-debug-dir=/usr/local/lib/debug (relocatable)

("Relocatable" means the directory can be moved with the GDB installation
tree, and GDB will still find it.)
```

至此安装完成，可以调试代码了
