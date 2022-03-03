#### **windows驱动**  

选择对应版本下载

https://www.mellanox.com/products/adapter-software/ethernet/windows/winof-2

![image](https://github.com/Turnedback/OCP2-Pcie/raw/master/img/winof.png)

#### **下载刷固件工具 MFT**  

一般选择图示版本即可

https://www.mellanox.com/products/adapter-software/firmware-tools


![image](https://github.com/Turnedback/OCP2-Pcie/raw/master/img/mft.png)

#### **下载固件**

https://www.mellanox.com/support/firmware/connectx3en

需要用到的固件已经上传github，需要复制固件到MFT根目录

```
C:\Program Files\Mellanox\WinMFT
```


![image](https://github.com/Turnedback/OCP2-Pcie/raw/master/img/cx341firmware.png)

#### **-----刷写固件，以下均在以管理员身份运行的cmd输入-----**

执行命令

```
cd "C:\Program Files\Mellanox\WinMFT"
```

查看设备名称

```
mst status -v
```

查看当前固件

```
flint.bat -d {设备名称} q
eg:
flint.bat -d mt4099_pci_cr0 q
```

备份原有固件（可选）

```
flint -d /dev/mst/mt4099_pci_cr0 rb 0 2097152 341A-XCEN_MT_1270112023.bin
```
或，备份全部
```
flint.bat -d {设备名称} ri {备份出来的固件的文件名称}
```

---XCEN a3 a6 刷最新的cx342a xccn即可，---

```
flint.bat -d mt4099_pci_cr0 -i fw-ConnectX3-rel-2_42_5000-MCX342A-XCC_Ax-UEFI-14.11.45-FlexBoot-3.4.752.bin --allow_psid_change b
```

---XCGN a9 刷最新的cx342a xcgn即可---

```
flint.bat -d mt4099_pci_cr0 -i fw-ConnectX3-rel-2_42_5000-MCX342A-XCG_Ax-UEFI-14.11.45-FlexBoot-3.4.752.bin --allow_psid_change b
```

然后一路Y下去就可以看到刷写读条了，等待完成后重启即可
