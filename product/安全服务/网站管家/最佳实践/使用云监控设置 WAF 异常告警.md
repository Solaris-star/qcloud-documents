本文档将介绍如何在云监控平台进行告警配置，当 Web 应用防火墙（以下简称为：WAF）出现异常情况，可以及时提醒。

## 前提条件
- 已开通 [ Web 应用防火墙](https://buy.cloud.tencent.com/buy/waf)。
- 已配置完 [实例域名](https://cloud.tencent.com/document/product/627/53628)。

## 操作步骤
### 步骤1：设置触发条件模板[](id:CFTJ)
1. 登录 [云监控控制台](https://console.cloud.tencent.com/monitor/overview)，在左侧导航中，单击告警管理菜单下的 【触发条件模板】，进入触发条件模板页面。
2. 在触发条件模板页面，单击【新建】，弹出新建弹窗。
![](https://main.qcloudimg.com/raw/17047d0b49518adb14bf61793a5223d9.png)
3. 在新建弹窗中，配置所需内容后，单击【保存】，即成功创建触发条件模板。
>?
>- 模板名称：输入模板名称。
>- 备注：输入模板备注。
>- 策略类型：**选择 Web 应用防火墙**。
>- 使用预置触发条件：云监控内置对应监控项的触发条件，勾选规则开启。
>- 触发条件：
>  - 分为指标告警和事件告警。在其下方单击【添加】，可以设置多个告警项。
>  - WAF 可以监控的条件包括：访问次数、Web 攻击数、CC 攻击数、上下行带宽、QPS、BOT 攻击数、Web 攻击占比、BOT 攻击占比和 CC 攻击占比。
>
![](https://main.qcloudimg.com/raw/45d8578279798d3d4a6276a2ec36492f.png)


### 步骤2：设置通知模板[](id:TZMB)
1. 登录 [云监控控制台](https://console.cloud.tencent.com/monitor/overview)，在左侧导航中，单击告警管理菜单下的 【通知模板】，进入通知模板页面。
2. 在通知模板页面，单击【新建】，进入新建通知模板页面。
![](https://main.qcloudimg.com/raw/f79a01b444223df260bc562cde8b554d.png)
3. 在新建通知模板页面，配置所需内容后，单击【完成】，即成功创建通知模板模板。
>?
> - **模板名称**：自定义模板名称。
> **通知类型**：
>  - 告警触发：告警触发时发送通知。
>  - 告警恢复：告警恢复时发送通知。
> - **语言**：可以选择中文或英文。
> - **用户通知**：
>  - 接收对象：可选接收组或接收人。
>  - 通知时段：定义接收告警时间段。
>  - 接收渠道：支持邮箱、短信、微信、电话四种告警渠道。
>- 接口回调：填写公网可访问到的 URL 作为回调接口地址，最多可填写3个告警回调地址。云监控将及时把告警信息推送到该地址，当 HTTP 返回 200为验证成功。告警回调字段说明请参考 [告警回调说明](https://cloud.tencent.com/document/product/248/50409#.E5.91.8A.E8.AD.A6.E5.9B.9E.E8.B0.83.E5.8F.82.E6.95.B0.E8.AF.B4.E6.98.8E)。
>
![](https://main.qcloudimg.com/raw/f34de0482428d4e3aea6acb26bad05a8.png)

### 步骤3：配置告警策略
1. 登录 [云监控控制台](https://console.cloud.tencent.com/monitor/overview)，在左侧导航中，单击告警管理菜单下的 【告警策略】>【告警策略】，进入告警策略页面。
>?可在告警策略页面页面新增，修改复制以及查看策略的告警历史，对于每条策略，可以绑定刚设置的 [触发条件](#CFTJ) 和 [通知模板](#TZMB)。
2. 在告警策略页面，单击【新建】，进入新建告警策略页面。
![](https://main.qcloudimg.com/raw/b0849fa979d0728072d5f40a6f6aff44.png)
3. 在新建告警策略页面，需完成以下步骤：
  1. 基本信息：配置名称和备注等信息，其中策略类型选择 Web 应用防火墙。
    ![](https://main.qcloudimg.com/raw/226b5a7cf9234f46ff56ca17c8a97a81.png)
  2. WAF 告警对象：选择WAF 支持以实例为监控告警的最小粒度，同时支持实例分组对象，需要手动配置分组。
>?
>- 选择实例 ID，则该告警策略绑定用户选中的实例。
>- 选中选择实例组，则该告警策略绑定用户选中的实例分组。
>- 选择全部对象，则该告警策略绑定当前账号拥有权限的全部实例。
>
![](https://main.qcloudimg.com/raw/d65f9fa4c18b1aac728f75ac02033907.png)
  3. 触发条件：选择刚设置的 [触发条件模板](#CFTJ)，或手动配置。
  ![](https://main.qcloudimg.com/raw/0598800855f24310a879a167274a9533.png)
  4. 通知模板：选择刚设置的 [通知模板](#TZMB) 后，单击【确定】保存。
  ![](https://main.qcloudimg.com/raw/f2ef6daa873ced928a26769264aa2c6b.png)
  5. 高级配置（可选）：单击![](https://main.qcloudimg.com/raw/ad0958699f9a6b2f6a153205fb865a22.png)启用弹性伸缩后，达到告警条件可触发弹性伸缩策略。
4. 完成以上步骤后，单击【完成】，即成功创建告警策略。
![](https://main.qcloudimg.com/raw/8fe5609618eb6f31f710edeac905a7a4.png)
