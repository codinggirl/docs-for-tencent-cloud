## 操作场景
堡垒机支持运维用户使用动态口令（OTP）认证进行登录，使用 OTP 认证之前需先配置 OTP 服务，下面将为您详细介绍如何在堡垒机配置 OTP 服务。




## 操作步骤

堡垒机支持 [本地 OTP 服务](#.E6.9C.AC.E5.9C.B0-otp-.E6.9C.8D.E5.8A.A1) 和 [第三方 OTP 服务](#.E7.AC.AC.E4.B8.89.E6.96.B9-otp-.E6.9C.8D.E5.8A.A1)。本地 OTP 服务为堡垒机系统内建 OTP 服务，并提供微信小程序“数盾OTP”用于获取登录口令。第三方 OTP 服务需要额外的 OTP 服务器。




#### 本地 OTP 服务

1. 登录腾讯云 [堡垒机控制台](https://console.cloud.tencent.com/dsgc/bh)，并使用管理员账号登录堡垒机。
2. 在右上角单击【系统管理】，进入系统管理页面。
3. 在系统管理页面，选择【安全设置】>【OTP认证配置】，进入 OTP 认证配置页面。
4. 在 OTP 认证配置页面，勾选【本地OTP服务】，单击【保存】，即可开启本地 OTP 服务。
![](https://main.qcloudimg.com/raw/c083620ff2b262bac2e44037d638d877.png)

#### 第三方 OTP 服务

1. 登录腾讯云 [堡垒机控制台](https://console.cloud.tencent.com/dsgc/bh)，并使用管理员账号登录堡垒机。
2. 在右上角单击【系统管理】，进入系统管理页面。
3. 在系统管理页面， 选择【安全设置】>【OTP认证配置】，进入 OTP 认证配置页面。
4. 在 OTP 认证配置页面，勾选【第三方OTP服务】，输入相关第三方OTP服务器地址,认证端口，认证方法等信息。
 - **OTP 服务器主机地址**：填写真实的 OTP 服务器主机地址。
 - **OTP 服务器备机地址**：OTP 备机地址，可不填。
 - **OTP 主机认证端口**：默认的 OTP 端口为1812，请根据实际环境填写。
 -  **OTP 备机认证端口**：OTP 备机认证端，请根据实际环境填写。
 - **OTP 认证方法**：请根据实际环境填写。例如 PAP。
 - **通信密钥**：OTP 认证密码。请根据实际环境填写。
![](https://main.qcloudimg.com/raw/c70e270202b30bcae354cd8154909ca0.png)
4. 单击【保存】，即可完成 OTP 服务配置。





