在 Debian 系统中，你可以使用 `ntp` 或 `chrony` 来同步系统时间。以下是两种方法的详细步骤：

---

### 方法 1：使用 `systemd-timesyncd`（默认轻量级服务）
Debian 默认使用 `systemd-timesyncd` 进行时间同步，配置如下：

1. **检查服务状态**：
   ```bash
   timedatectl status
   ```
   - 如果显示 `NTP service: active` 表示已启用时间同步。

2. **启用 NTP 同步**（如果未启用）：
   ```bash
   timedatectl set-ntp true
   ```

3. **手动强制同步**：
   ```bash
   systemctl restart systemd-timesyncd
   ```

4. **查看同步日志**：
   ```bash
   journalctl -u systemd-timesyncd
   ```

---

### 方法 2：使用 `ntp`（传统 NTP 服务）
1. **安装 NTP 包**：
   ```bash
   sudo apt update
   sudo apt install ntp
   ```

2. **启动并启用服务**：
   ```bash
   sudo systemctl enable --now ntp
   ```

3. **检查同步状态**：
   ```bash
   ntpq -p
   ```
   - 输出中的 `*` 表示当前使用的时间服务器。

4. **修改服务器配置**（可选）：
   - 编辑 `/etc/ntp.conf`，替换默认服务器为国内的 NTP 服务器（如阿里云）：
     ```
     server ntp.aliyun.com iburst
     server ntp1.aliyun.com iburst
     ```
   - 重启服务：
     ```bash
     sudo systemctl restart ntp
     ```

---

### 方法 3：使用 `chrony`（更适合不稳定的网络）
1. **安装 Chrony**：
   ```bash
   sudo apt update
   sudo apt install chrony
   ```

2. **启动并启用服务**：
   ```bash
   sudo systemctl enable --now chrony
   ```

3. **检查同步状态**：
   ```bash
   chronyc tracking
   chronyc sources -v
   ```

4. **修改服务器配置**（可选）：
   - 编辑 `/etc/chrony/chrony.conf`，添加国内服务器：
     ```
     server ntp.aliyun.com iburst
     server ntp1.aliyun.com iburst
     ```
   - 重启服务：
     ```bash
     sudo systemctl restart chrony
     ```

---

### 验证时间同步
无论使用哪种方法，都可以通过以下命令检查时间状态：
```bash
timedatectl
```
- 确保 `NTP synchronized: yes`。

---

### 常见问题
1. **防火墙阻止 NTP**：
   - 确保 UDP 端口 123 开放。

2. **手动强制同步**（临时）：
   ```bash
   sudo ntpdate ntp.aliyun.com  # 如果使用 ntp
   sudo chronyc makestep        # 如果使用 chrony
   ```

3. **硬件时钟同步**：
   - 将系统时间写入硬件时钟：
     ```bash
     sudo hwclock --systohc
     ```

根据你的需求选择合适的方法即可！
