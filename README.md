# BootImgTool

略作修改

原GitHub：[difcareer/BootImgTool: A Tool for unpack/pack android boot.img (github.com)](https://github.com/difcareer/BootImgTool)

## Usage

**要在项目根目录使用**

1. compile
```
./build.sh
```

2. unpack
```
bin/unpack-bootimg.sh path/of/boot.img
```

3. repack
```
bin/repack-bootimg.sh [boot.img-kernel.gz] [boot.img-ramdisk-dir] [out_boot.img_name]
```



## Example



### 一、解压谷歌原版镜像

### 二、打开zip压缩包，复制出`boot.img`文件


### 三、对`boot.img`进行解包
**首先要编译BootImgTool**

```bash
cd BootImgTool/
./build.sh
```


```bash
./bin/unpack-bootimg.sh ../boot.img 
```
会在boot.img同目录生成解包文件



### 五、编辑`prop.default`文件
进入`boot.img-ramdisk`文件夹，编辑`default.prop`

```bash
ro.secure=0

ro.adb.secure=0

ro.debuggable=1
```


### 六、对boot.img重打包
```bash
./bin/repack-bootimg.sh tmp/boot.img-kernel.gz tmp/boot.img-ramdisk tmp/new.img
```

### 七、刷入新img
```bash
adb reboot bootloader
fastboot flash boot new.img
fastboot reboot
```



# OTHER-bootimg.py

另一个打包解包工具

查看用法：

```bash
python bootimg.py
```



