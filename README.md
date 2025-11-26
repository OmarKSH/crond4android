# crond4Android

Supports running under KernelSU, APatch, and Magisk. Calls the corresponding framework Busybox to implement crond scheduling.

Starting from version `1.0.3`, it supports controlling the installation of the command line via creating a file `/sdcard/crond4android.setup` or using the volume keys.

If the content of `/sdcard/crond4android.setup` is 1, the crontab command will be automatically installed; otherwise, it will not be installed.

> Typically used for environment detection, installing the crontab command is not recommended unless absolutely necessary, and it may conflict with the lsposed beta version, causing lsposed to malfunction; the reason is currently unknown. It is recommended to use an alias.

## Data Directory

Logs: `/data/adb/crond/run.log`

Task Data: `/data/adb/crond/`

crontab: `/system/bin/crontab`

Note: If you replace the root implementation, remember to modify this script or reinstall it; otherwise, it will not execute. Creating `/data/adb/crond/KEEP_ON_UNINSTALL` allows you to retain task data when uninstalling the module.

## Usage Example

```shell

# Create a task (you can also edit the file directly)

# alias crontab="root path (refer to customize.sh)/busybox crontab -c '/data/adb/crond'"
echo '30 4 * * * echo "" > /data/adb/crond/run.log' >> /data/adb/crond/root # for root user

# View tasks
crontab -l
```
