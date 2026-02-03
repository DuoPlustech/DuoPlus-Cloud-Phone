本文介绍了常用的adb ssh命令，您可以通过以下2种方式执行adb命令：
1. DuoPlus的命令执行接口：https://help.duoplus.cn/docs/execute-the-adb-command
2. adb客户端：https://help.duoplus.cn/docs/adb

## 文件传输
### 从URL下载文件到云手机
> 下载文件比较耗时，通过命令后面加：> /dev/null 2>&1 & 来让命令在后台执行
```sh
wget --no-check-certificate -O /sdcard/test.apk https://YOUR_APK_URL/test.apk > /dev/null 2>&1 &
```
### 从云机上传文件到中转站
上传文件比较耗时，通过命令后面增加`> /sdcard/upload.log`可以将上传进度写入日志文件中；通过命令后面增加`2>&1 &`来让命令在后台执行，避免命令执行超时
```sh
curl -F "file=@/sdcard/test.apk" https://temp.sh/upload > /sdcard/upload.log 2>&1 &
```
上传完毕后，通过以下命令获取上传进度，如果上传成功能在log文件中看到文件下载URL ：
```sh
cat /sdcard/upload.log
```
### 从本地电脑推送文件到云机
```sh
# 使用方式
adb push [本地电脑文件位置] [云手机文件位置]
# 例如
adb push C:\Users\YourUsername\Documents\example.txt /sdcard/example.txt
```
### 从云机下载文件到本地电脑
```sh
# 使用方式
adb pull [云手机文件位置]  [本地电脑文件位置]
# 例如
adb pull /sdcard/example.txt C:\Users\YourUsername\Documents\
```
### 截图手机屏幕到本地电脑
```sh
adb exec-out screencap -p > screenshot.png
```
## 应用
### 获取已安装包名列表
```sh
pm list packages -3 | cut -d ":" -f 2
```
### 安装应用
```sh
pm install /sdcard/test.apk
```
### 启动应用
```sh
am start -n $(dumpsys package 包名 | grep -A 1 'MAIN' | grep '包名' | sed -n 's/.*\(包名\/[^ ]*\).*/\1/p')
```
### 关闭应用
```sh
am force-stop 包名
```
### 卸载应用
```sh
pm uninstall 包名
```
### 清理应用数据
```sh
pm clear 包名
```
### 授予应用权限
权限名称列表：https://developer.android.com/reference/android/Manifest.permission#summary
```sh
pm grant 包名 android.permission.权限名称
```
## 系统日志
### 清除系统日志
建议在生成系统日志前先清除系统老旧日志，否则日志内容过多会比较难观察日志，可以通过以下命令清除系统日志
```sh
logcat -c
```
### 上传系统日志
```sh
cat logcat | nc termbin.com 9999
```
返回的content内容中将包含logcat日志内容的URL

> 小技巧，此命令可以上传任意文本内容，例如：`cat /sdcard/test.txt | nc termbin.com 9999`
## 模拟按键
### 通用按键
通过调用 `input keyevent 代码 `即可模拟按键操作。

以下是一些常用的 KeyEvent 代码，供参考：

| KeyEvent 代码 | 对应按键          | 描述                       |
|--------------|-------------------|----------------------------|
| 4            | 返回键（BACK）     | 模拟按下返回按钮             |
| 19           | 上方向键（DPAD_UP） | 模拟按下上方向键             |
| 20           | 下方向键（DPAD_DOWN）| 模拟按下下方向键             |
| 21           | 左方向键（DPAD_LEFT）| 模拟按下左方向键             |
| 23           | 选择键（DPAD_CENTER）| 模拟按下选择键（类似于点击确认）|
| 82           | 菜单键（MENU）    | 打开设备的菜单选项           |
|  KEYCODE_VOLUME_UP（24） | 音量加键           | 模拟增加设备音量             |
| KEYCODE_VOLUME_DOWN（25） | 音量减键           | 模拟减少设备音量             |

使用示例

```bash
input keyevent 19    # 上方向键
input keyevent 66    # 回车键
input keyevent 3     # Home 键
```
### 点击坐标
```sh
# 点击坐标(500,300)
input tap 500 300
# 点击坐标(500,300)并保持200ms
input swipe 500 300 500 300 200
# 从坐标(500,500)滑动到(500,100)总耗时200ms（即向上滑动400）
input swipe 500 500 500 100 200
```
