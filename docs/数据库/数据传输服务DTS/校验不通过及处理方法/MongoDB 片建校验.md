
## 检查详情
- 检查要求：当目的端为分片实例时，可以在目的端预设片建，如果目的端与源端表格片建不一致，则会发出警告提示。警告不会阻塞任务的继续，但会对业务有一定影响，请用户评估后自行决定是否忽略警告。
- 业务影响：部分片建不一致场景会导致迁移或者同步任务失败。

## 修复方法
如果目的端预设片建，参考如下命令在源端进行分片操作。
```
sh.shardCollection("<database>.<collection>", { <shard key> : "hashed" } , false, {numInitialChunks: 预置的chunk个数}) 
```
重新执行校验任务。

