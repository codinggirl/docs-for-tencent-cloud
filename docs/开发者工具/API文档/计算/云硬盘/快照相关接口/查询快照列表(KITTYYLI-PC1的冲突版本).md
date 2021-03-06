
## 1. 接口描述

本接口(DescribeSnapshots)用于查询快照的详细信息。可根据快照ID、创建此快照的云硬盘ID，创建快照的云硬盘类型等对结果进行过滤。对于过滤条件，不同条件之间为与(AND)的关系，如果不传入则不以此条件过滤。

接口请求域名：<font style="color:red">snapshot.api.qcloud.com</font>

使用限制：

无特殊限制，具体参数限制见下表。


## 2. 输入参数

以下请求参数列表仅列出了接口请求参数，其它参数见[公共请求参数](https://cloud.tencent.com/document/product/240/8320)页面。

| 参数名称 | 必选  | 类型 | 描述 |
|---------|---------|---------|---------|
| diskType  | 否 | String | 按云硬盘类型。可选值：root（系统盘）,data（数据盘）|
| projectId | 否 | Int | 按项目ID过滤。0为默认项目，如需指定其它项目，可调用<a href="https://cloud.tencent.com/doc/api/403/4400" title="DescribeProject">DescribeProject</a>接口查询|
| storageIds.n | 否 | Array[String] | 按创建快照的云硬盘ID筛选。可调用<a href="http://cloud.tencent.com/doc/api/364/%E6%9F%A5%E8%AF%A2%E4%BA%91%E7%A1%AC%E7%9B%98%E4%BF%A1%E6%81%AF" title="DescribeCbsStorages">DescribeCbsStorages</a>接口查询|
| snapshotIds.n  | 否 | Array[String] | 按快照ID筛选。|
| offset | 否 | Int | 偏移量，不传则为0 |
| limit | 否 | Int | 一次最多可查询的快照数量，不传则为20，最大为100|


## 3. 输出参数

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| code | Int | 公共错误码, 0表示成功，其他值表示失败。详见<a href="https://cloud.tencent.com/doc/api/372/%E9%94%99%E8%AF%AF%E7%A0%81#1.E3.80.81.E5.85.AC.E5.85.B1.E9.94.99.E8.AF.AF.E7.A0.81" title="公共错误码">公共错误码</a>。|
| message | String | 错误信息|
| snapshotSet | Array[object] | 快照详情 |
| totalCount | Int | 符合查询条件的快照数量 |


snapshotSet结构

| 参数名称 | 类型 | 描述 |
|---------|---------|---------|
| createTime | Int | 快照创建时间 |
| diskType | String | 创建此快照的云硬盘类型，'root(系统盘快照)','data'(数据盘快照) |
| percent | Int | 快照创建进度百分比，快照创建成功后此字段恒为100|
| projectId | Int | 所属项目ID，跟随原云硬盘项目ID |
| snapshotId | String | 快照ID |
| snapshotName | String | 快照名称，用户自定义的快照别名。调用[ModifySnapshot](https://cloud.tencent.com/doc/api/364/2532)可修改此字段 |
| snapshotStatus | String | 快照状态为normal（已创建），creating（创建中），rollbacking（回滚中),只有normal状态的快照才可执行回滚和创建云硬盘任务 |
| storageId | String | 创建此快照的云硬盘ID |
| storageSize | Int | 创建此快照的云硬盘的大小。使用快照创建弹性云盘时，新的弹性云盘大小必须大于此大小 |


## 4. 示例

输入：
```
https://snapshot.api.qcloud.com/v2/index.php?
<公共请求参数>
&Action=DescribeSnapshots
&limit=1
```

返回示例如下。从中可以看出，totalCount为5，说明该用户在此地域下有5个快照，但是由于查询参数中limit=1则结果只返回一条快照信息。此快照(snapshotId)为数据盘快照(diskType)，创建此快照的云硬盘（storageId）大小为10GB(storageSize)，快照当前状态为正常(snapshotStatus)

```
{
    "code": 0,
    "message": "",
    "totalCount": 5,
    "snapshotSet": [
        {
            "snapshotId": "snap-ffxxxrx",
            "storageId": "disk-8rxxyy",
            "snapshotName": "ABCDEFGHHHH",
            "snapshotStatus": "normal",
            "projectId": 0,
            "percent": 100,
            "storageSize": 10,
            "createTime": "2016-05-17 19:58:48",
            "diskType": "data"
        }
    ]
}
```

