<blockquote class="d-mod-alarm">
              <div class="d-mod-title d-alarm-title">
                <i class="d-icon-alarm"></i>公告：
              </div>
               <p>QUIC 访问功能已在内侧中，CDN 官网通用日志字段 - HTTP 协议标识（离线日志第14个字段；实时日志 proto 字段）将增加值“HTTP/3”，此变更将于 2021-09-13 起灰度发布，不会影响控制台及接口的数据监控统计，若您使用离线日志下载包进行数据统计，请关注并确认具体影响，按需调整。非常感谢您的理解与配合，谢谢！详情请参见 <a href="https://cloud.tencent.com/document/product/228/42136">日志服务</a>。</p>
            </blockquote>



## 功能介绍

QUIC (Quick UDP Internet Connections) 是一个通用的网络协议，能够保障网络安全性，同时减少传输和连接时的延时，避免网络拥塞。您可开启 QUIC 协议，保障客户端访问 CDN 节点时数据传输的安全性，提升访问效率。

当前默认支持 h3 Draft 28, h3-Q050, h3-Q046, h3-Q043, Q046, Q043 版本。

腾讯云 CDN 已开启 QUIC 内测，若您已开通 CDN 服务，您可以使用主账号 [提交申请表](https://cloud.tencent.com/apply/p/2j0i34wqyw8) 申请试用。如果您已经提交申请，我们将在15个工作日对您的申请进行审核。

## 内测时间
腾讯云 CDN 将于 **2021-08-31 23:59:59** 结束第一轮 QUIC 访问 内测申请，感谢您的参与！请关注等待后续启动第二轮内测或全量发布。


## 内测指南

若您通过了内测审核，则可以在控制台上为新添域名开启 QUIC 平台，进行测试。
>!
>- 通过内测后，仅支持对新添加域名开启QUIC平台，不支持存量已添加的域名。
>- QUIC 平台现为测试平台，尚未全量，建议您仅对测试域名开启 QUIC 平台，不要使用业务域名。
>- 业务类型切换涉及资源平台调度，接入 QUIC 平台后，建议您不要再切换域名的业务类型。
>- 当前不支持 QUIC 回源。


登录 [CDN 控制台](https://console.cloud.tencent.com/cdn)，新添域名时，您可通过选中 QUIC 平台项，为域名接入 QUIC 平台：
![](https://main.qcloudimg.com/raw/cb7d9ab0a9026574363f7308047c04c6.png)
**配置约束：**

- 流媒体点播加速业务类型的域名暂不支持 QUIC。
- 开启IPv6访问后不可开启 QUIC。


成功添加域名后，可进入域名管理，切换 Tab 至【HTTPS 配置】，即可找到【QUIC】配置：默认为关闭状态，您可自助开启。
**注：**开启前请先配置 HTTPS 证书。
![](https://main.qcloudimg.com/raw/b90da5a37968a594ed9c81768fb72ab5.png)



## 计费规则

QUIC 访问属于增值服务，目前腾讯云 CDN 正在免费内测中，暂不进行收费。后续进行线上计费时，我们会提前推送消息给您，请您关注确认。

