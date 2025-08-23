# Debian 时间同步教程

1. 下载 ntp（任选一个）

```bash
sudo apt install ntp
sudo apt install ntpsec
```

2. 设置时钟为本地时钟

```bash
sudo timedatectl set-timezone "Asia/Shanghai"
sudo timedatectl set-local-rtc 1
```

3. 设置强制同步：

```bash
sudo apt install ntpdate
sudo ntpdate -d ntp.ntsc.as.cn
```
