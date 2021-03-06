## View the Demo
To open the mini program demo, you need to upgrade WeChat to the latest version, go to **Discover** => **Mini Programs** => and search "Tencent Video Cloud":

| Feature | Mini Program Component | Experience on PC | Dependent Cloud Service | Description |
|:--------:|:--------------:|:-----------------:|:------------------:| :---------:|
| Mobile LVB | [&lt;live-room&gt;](https://cloud.tencent.com/document/product/454/15368) | N/A | LVB+IM | Demonstrate personnel live video solution based on Mini Program | 
| PC LVB | [&lt;live-room&gt;](https://cloud.tencent.com/document/product/454/15368) | [WebEXE](http://img.qcloud.com/open/qcloud/video/act/liteavWeb/webexe/webexe.html) | LVB+IM | Demonstrate features related to live classroom broadcasting and teacher-student interaction (in combination with PC) |
| One-on-one video chat | [&lt;rtc-room&gt;](https://cloud.tencent.com/document/product/454/15364) | [WebEXE](http://img.qcloud.com/open/qcloud/video/act/liteavWeb/webexe/webexe.html) | LVB+IM | Demonstrate one-on-one video chat feature which is applicable to online customer service |
| Multi-person video chat | [&lt;rtc-room&gt;](https://cloud.tencent.com/document/product/454/15364) | N/A | LVB+IM | Demonstrate multi-person video chat feature which is applicable to temporary meetings |
| WebRTC | [&lt;webrtc-room&gt;](https://cloud.tencent.com/document/product/454/16914) | [Chrome](http://img.qcloud.com/open/qcloud/video/act/liteavWeb/webrtc/webrtc.html) | Real-Time Audio/Video | Demonstrate the capability of interconnection between Mini Program and Chrome browser |
| RTMP Push | [&lt;live-pusher&gt;](https://cloud.tencent.com/document/product/454/12518) | N/A | LVB | Demonstrate basic RTMP push feature |
| LVB Player | [&lt;live-player&gt;](https://cloud.tencent.com/document/product/454/12519) | N/A | LVB | Demonstrate LVB playback feature based on RTMP and FLV protocols |

![](https://mc.qcloudimg.com/static/img/9851dba2c86161bc9e14a08b5b82dfd2/image.png)


## Register a Mini Program and Open a Relevant Interface
For policy and compliance considerations, &lt;live-pusher&gt; and &lt;live-player&gt; are not supported by all WeChat mini programs:

Mini programs of personal and enterprise accounts only support the categories in the following table:
<table>
<tr align="center">
<th width="200px">Primary Category</th>
<th width="700px">Sub-category</th>
</tr>
<tr align="center">
<td>"Social"</td>
<td>LVB</td>
</tr>
<tr align="center">
<td>"Education"</td>
<td>Online education</td>
</tr>
<tr align="center">
<td>"Healthcare"</td>
<td>Internet hospital and public hospital</td>
</tr>
<tr align="center">
<td>"Government Affairs and Livelihood"</td>
<td>All secondary categories</td>
</tr>
<tr align="center">
<td>"Finance"</td>
<td>Funds, trusts, insurance, banking, securities/futures, micro-credit of non-financial institutions, credit investigation, and consumer finance</td>
</tr>
</table>

Open [WeChat MP Platform](https://mp.weixin.qq.com), register and log in to the mini program, and enable the component permissions in <font color='red'>**Settings** -> **API Settings**</font> of the mini program management backend, as shown below:

![](https://mc.qcloudimg.com/static/img/a34df5e3e86c9b0fcdfba86f8576e06a/weixinset.png)

> Note: If a mini program cannot work properly while the above settings are correct. That may be because the cache within the WeChat is not updated. Delete the mini program, restart WeChat, and try again.

## Install WeChat Mini Program Development Tools

Download and install the latest version of [WeChat Developer Tools](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html), and scan the QR code using the WeChat account bound to the mini program to log in to the Developer Tools.

<img style="border:0; max-width:100%; height:auto; box-sizing:content-box; box-shadow: 0px 0px 0px #ccc; margin: 0px 0px 0px 0px;" src="https://main.qcloudimg.com/raw/8e1eeee23aec979f346d4b4c05e62571.png" />


## Obtain Demo and Source Codes and Debug

- Step 1: Access [SDK+Demo](https://cloud.tencent.com/document/product/454/7873#XiaoChengXu), and obtain the mini program demo and source codes.

- Step 2: Open WeChat Developer Tools installed, and click the **Mini Program Project** button.

- Step 3: Input the AppID of mini program, select the code directory downloaded in the previous step in the project directory (**Note:** Select the **root directory** instead of just the `wxlite` directory. The root directory contains the `project.config.json` file.), click **OK** to create a mini program project.

- Step 4: Click **OK** again to enter Developer Tools.

- Step 5: Directly scan the QR code generated by the Developer Tools to perform the test using a mobile phone.

- Step 6: <font color='red'>Enable the debug mode</font> to experience and debug internal features. By enabling the debug mode, you do not need to add these domain names to the whitelist of mini program.

<img style="border:0; max-width:100%; height:auto; box-sizing:content-box; box-shadow: 0px 0px 0px #ccc; margin: 0px 0px 0px 0px;" src="https://main.qcloudimg.com/raw/c05e7942a54a2ad41ec2066459edb528.png" />

## Test Address to be Visited by Demo
The demo mini program will access the test server addresses in the following table. We offer you an experience account to access the cloud services of these servers. Usually, many customers will do tests on it. If you want to use your own backend server to avoid being disturbed by other customers, please see the following section of the document:

- **The demos related to &lt;live-room&gt; and &lt;rtc-room&gt; need to access the following addresses:**

| URL | Corresponding Server Address | Server Feature Description |
|:------:|:------:| :---------------: |
| `https://webim.tim.qq.com` | IM backend server address | Used to support the messaging feature in the mini program |
| `https://room.qcloud.com` | RoomServicebackend server address | RoomService is the room management logics for supporting [&lt;rtc-room&gt;](https://cloud.tencent.com/document/product/454/15364) (Video Call) and [&lt;live-room&gt;](https://cloud.tencent.com/document/product/454/15368) (LVB Joint Broadcasting) |

- **The demos related to &lt;webrtc-room&gt; need to access the following addresses:**

| URL | Corresponding Server Address | Server Feature Description |
|:------:|:------:| :---------------: |
| `https://webim.tim.qq.com` | IM backend server address | Used to support the messaging feature in the mini program |
| `https://official.opensso.tencent-cloud.com/v4/`<br>`openim/jsonvideoapp` | WebRTC test backend | Used to request the userSig and privateMapKey needed to enter [&lt;webrtc-room&gt;](https://cloud.tencent.com/document/product/454/16914) |
| `https://xzb.qcloud.com/webrtc/`<br>`weapp/webrtc_room` | WebRTC room list backend | A simple room list feature for Demo testing and use. |


## Build Your Own Account and Backend Server
In this section, we will introduce how to replace Demo's default test server address with your own server. In this way, you can use your own Tencent Cloud account to implement the above features, and it is also convenient for you to carry out secondary development.


#### 1. Build the server of &lt;webrtc-room&gt;

##### 1.1 What can this server do?

- You will see a list of rooms after clicking the interactive classroom **&lt;webrtc-room&gt;** feature in the demo. How is this room list implemented?

- After seeing the video room list, if you want to create a video room, or enter a video room created by others, you need to pass valid parameter values for the attributes (`sdkAppID`, `userID`, `userSig`, `roomID` and `privateMapKey`) corresponding to [&lt;webrtc-room&gt;](https://cloud.tencent.com/document/product/454/16914). How to get these several parameter values?

##### 1.2 How to set up this server?

- Download [webrtc_server](https://github.com/TencentVideoCloudMLVBDev/webrtc_server_java), which are java source codes. The instructions in README.md will show you how to use these source codes.

##### 1.3 How to use the built server?

-  In the source codes of [Mini Program](https://github.com/TencentVideoCloudMLVBDev/MiniProgram), modify the `webrtcServerUrl` in the file `wxlite/config.js` to:
```
https://??????????????????/webrtc/weapp/webrtc_room
```

- The mini program's ability to implement WebRTC is definitely for video calls with Chrome. The browser-end source codes can be downloaded by clicking [Chrome(src)](https://github.com/TencentVideoCloudMLVBDev/webrtc_pc). Modify the `serverDomain` in the file `component/WebRTCRoom.js` to:
```
https://??????????????????/webrtc/weapp/webrtc_room
```

#### 2. Build the server of &lt;live-room&gt; and &lt;rtc-room&gt;

##### 2.1 What can this server do?
-  Both [&lt;live-room&gt;](https://cloud.tencent.com/document/product/454/15368) (for LVB joint broadcasting) and [&lt;rtc-room&gt;](https://cloud.tencent.com/document/product/454/15364) (for video calls) are extensions based on Tencent Cloud's LVB and IM services and require a backend component called RoomService for running.

##### 2.2 How to set up this server?
- Download the java source codes of [RoomService](https://github.com/TencentVideoCloudMLVBDev/rtcroom_server_java). The instructions in README.md will show you how to use these source codes.

##### 2.3 How to use the built server?
- In the source codes of [Mini Program](https://github.com/TencentVideoCloudMLVBDev/MiniProgram), modify the `serverUrl` and `roomServiceUrl` in the file `wxlite/config.js` to:
```
https://??????????????????/roomservice/
```

- If the mini program uses both the &lt;live-room&gt; and &lt;rtc-room&gt; tags, it cannot be paired with the Chrome browser on PC. Instead, the [WebEXE](https://cloud.tencent.com/document/product/454/17004) hybrid solution shall be used. Modify the `RoomServerDomain` in the files liveroom.html and double.html in the source codes of [GitHub (WebEXE)](https://github.com/TencentVideoCloudMLVBDev/webexe_web) to:
```
https://??????????????????/roomservice/
```

#### 3. Wafer zero-cost server deployment solution (Node.js)

If you are a senior web frontend engineer and you do not find the proper server for the moment, but want to have your own debugging backend quickly, you can use Tencent Cloud's Wafer feature to implement a zero-cost quick deployment solution (Wafer only supports Node.js backend codes). You only need to perform the following steps:
- Step 1: Download the??source codes of [mini program](https://github.com/TencentVideoCloudMLVBDev/MiniProgram).

- Step 2: Complete the deployment according to [Quick Deployment Guide](https://github.com/TencentVideoCloudMLVBDev/RTCRoomDemo/blob/master/doc/%E4%B8%80%E9%94%AE%E9%83%A8%E7%BD%B2_NodeJS.md).

- Step 3: Modify the `RoomServerDomain` in the files liveroom.html and double.html in the source codes of [GitHub (WebEXE)](https://github.com/TencentVideoCloudMLVBDev/webexe_web) to:
```
https://??????????????????/roomservice/
```

