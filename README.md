# esp32s3_openmv_lvgl
 
# 安装编译指南 #

## 1. 需要在Ubuntu下安装 ESP-IDF 依赖环境 ##
   当前验证过的环境：
   `idf: release v4.4`

## 2. 克隆工程 ##

   本工程代码使用submodule来管理openmv和micropython的官方代码，clone 本工程时:

   `git clone https://github.com/mengfeifly/esp32s3_openmv`

## 3. 编译工程 ##

   现在您可以从 `esp32s3_openmv_lvgl/project/openmv_ESP32S3`编译您的固件
   
   首先进入 `/project/openmv_ESP32S3` 文件目录

   - 执行 `make` 编译代码(首次编译，需要先执行make)
   
   如果编译没有出错，您在目录 `project/openmv_ESP32S3/` 中应该可以看到新创建的 `build-GENERIC_S3`文件夹。在这个文件夹中，有编译生成的 `application.bin` 等文件。
   
   其它可能经常会用到指令包括

   - 执行 `make erase` 擦除模块的flash
   - 执行 `make flash` 编译并烧录固件

## 4. 串口工具 ##
   因为本工程固件支持repl模式，所以可以使用 pytty等串口工具来进行repl调试。
   [点击下载putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)

## 5. 连接你的设备 ##

 将ESP32S3自带的USB端口连接上电脑，使用OpenMV IDE连接设备或者用Thonny IDE连接都可以进行编辑和运行。
 
## 6. 固件性能 ##

 RGB QVGA 35FPS
 JPEG VGA 40FPS
 颜色识别 35fps
 人脸检测 10fps
 数字识别 16fps
 JPEG WIFI图传 1080p 10fps

# 功能支持 #

- openmv IDE连接及USB 虚拟U盘实现，实现openmv4plus功能完全兼容；
- LCD显示屏支持ST7735s，ST7789，支持设置分辨率、显示旋转方向以及颜色反转；
- 支持tensorflow-micro，支持用户U盘导入tflite模型并实现目标检测、深度学习识别等，采用esp-nn加速；
- 支持yolo、swift-yolo目标检测算法前处理和后处理
- 支持固件内部导入yoloperson、yoloface、mnist、gesture等模型，减少内存占用；
- 支持machine_hand舵机机械臂空间逆运算，直接计算三维坐标与舵机角度得转换关系；
 
# TODO #

- 导入中文字库，实现中文显示
- 提升USB到IDE的图像传输速度，特别是RGB图像传输时由于ESP32只能软件压缩JPEG速度比较慢
- 实现WIFI_DBG，采用网络无线连接openmv IDE
