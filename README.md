# myaml

> **个人自用 OpenClash 配置模板。** 主要用于自己的配置备份、同步与日常使用，同时公开供有相似需求的人参考。不同网络环境、OpenClash/Mihomo 版本和订阅节点命名可能存在差异，请按自己的环境调整。
>
> 🤖 **由 ChatGPT 强力驱动** —— 配置整理、规则审查、结构优化与文档维护均由 ChatGPT 协助完成。

## 上游同步维护规则

本仓库基于并参考 `Aethersailor/Custom_OpenClash_Rules`。

维护原则：

- 跟踪上游规则变化，但不直接覆盖本仓库个人化配置。
- 只同步必要的规则集、规则顺序优化和规则兼容性更新。
- 不同步上游策略组结构，避免覆盖本仓库的个人策略组设计。
- `自有域名`、`手动选择2`、`手动选择3`、`链式前置`、`链式落地` 等个人扩展始终独立维护。
- Full / Lite 版本分别保持自身定位，不因为上游更新而互相合并。
- Full / Lite 的 YAML 与 INI 必须同步修改，禁止只更新其中一种格式。

## 上游项目

本仓库基于并参考：

- **Aethersailor/Custom_OpenClash_Rules**  
  https://github.com/Aethersailor/Custom_OpenClash_Rules
- Full 上游模板：`cfg/Custom_Clash_Full.ini`  
  https://github.com/Aethersailor/Custom_OpenClash_Rules/blob/main/cfg/Custom_Clash_Full.ini
- Lite 上游模板：`cfg/Custom_Clash_Lite.ini`  
  https://github.com/Aethersailor/Custom_OpenClash_Rules/blob/main/cfg/Custom_Clash_Lite.ini

规则集、地区分组、服务分流和基础结构主要沿用上游设计；本仓库在其基础上按照个人实际使用习惯进行调整。感谢上游作者及相关项目维护者。

## 本仓库定位

- **以自用为主**，不是通用订阅配置。
- 用于 OpenClash 的模板/覆写场景，代理节点由 OpenClash 后续注入，因此 YAML 中保留 `proxies: null`。
- 仓库中不保存机场订阅地址、节点密码、UUID、Token 等敏感信息。
- 配置公开主要是为了方便自己跨设备同步和分享参考，不保证直接复制后适用于其他人的环境。

## 配置版本

### Full

完整运行配置：`config/OpenClash_Full.yaml`  
订阅转换规则：`config/OpenClash_Full.ini`

基于上游 `Custom_Clash_Full.ini`，适合需要较完整服务分流、流媒体/AI/社交/电商等独立策略组的场景。

### Lite

完整运行配置：`config/OpenClash_Lite.yaml`  
订阅转换规则：`config/OpenClash_Lite.ini`

基于上游 `Custom_Clash_Lite.ini`，定位与上游一致：只保留基础分流与基本直连规则。

## YAML 与 INI 的关系

- `.yaml`：给 OpenClash/Mihomo 直接加载，包含完整运行参数。
- `.ini`：用于 subconverter/订阅转换，重点描述 ruleset 与 custom_proxy_group。
- 两种格式的规则顺序、策略组名称、默认候选顺序和节点筛选逻辑保持等效。
- INI 不替代完整 YAML。

## 主要自定义内容

- 增加 `手动选择2`、`手动选择3`。
- 增加 `链式前置`、`链式落地`。
- 使用 `小鸡` 作为落地节点标识。
- `漏网之鱼` 默认优先选择 `手动选择`。
- `非标端口` 默认优先选择 `全球直连`。
- 增加 `自有域名` 策略组，独立管理 `choner.eu.org`。

## 文件说明

```text
myaml/
├── README.md
├── CHANGELOG.md
└── config/
    ├── OpenClash_Full.yaml
    ├── OpenClash_Full.ini
    ├── OpenClash_Lite.yaml
    └── OpenClash_Lite.ini
```

## 使用提醒

1. 节点由 OpenClash/订阅注入，仓库不保存真实代理节点。
2. `小鸡` 是个人命名约定。
3. 修改策略组名称后，需要同步调整外部链式配置。
4. 更新配置前建议保留可用版本方便回滚。

## 变更记录

见 [CHANGELOG.md](CHANGELOG.md)。
