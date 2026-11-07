---
name: edu-lead-response-routing-agent-core
display_name: '线索响应调度核心助手'
display_name_en: 'Lead Response Routing Agent Core Assistant'
description: '为线索响应调度提供输入校验、结构化整理和成果模板支持'
description_zh: '校验线索池、来源、意向标签、校区/顾问能力、响应时限和排班的完整性，并整理为可交付结构'
description_en: 'Validate structured inputs and prepare an output-ready structure for the parent agent.'
examples_zh:
  - '检查我提交的输入字段是否完整'
  - '整理这份业务资料并标出冲突项'
examples_en:
  - 'Check whether my structured input is complete.'
  - 'Organize the supplied business information and flag conflicts.'
version: 1.0.1
author: '广州金励泽科技服务有限公司'
---

# 线索响应调度核心助手

本Skill是Agent内部的结构化支持组件，不替代Agent的诊断、方案设计、人工确认和复盘职责。

## 产品契约

- 核心任务：线索响应优先级、人员分配和处理计划。
- 主要风险：自动处理真实客户信息或产生歧视性分配
- 去重边界：与MT-CRM区分：只生成一次分派方案和规则，不保存或自动操作客户记录。

## 输入

- 线索池
- 来源
- 意向标签
- 校区/顾问能力
- 响应时限和排班

## 工作流程

1. 用户提供结构化JSON时，先执行 @scripts/validate_input.js。
2. 输入缺失时返回缺失字段，不要求Agent自行编造。
3. 输入冲突时返回确认项，暂停正式结论。
4. 安全检查通过后，按 @templates/OUTPUT_TEMPLATE.md 建立空结构。
5. 将结构交回Agent继续专业处理。

## 专属检查

- 按线索阶段、客户需求、决策角色、时间窗口和最近一次有效沟通建立判断依据。
- 区分客户原话、顾问记录和推断，不能把未确认意向当作成交承诺。
- 将下一步动作写到责任人、时间、渠道和完成标准，避免只给沟通话术。
- 涉及敏感客户信息时仅保留完成当前判断所需字段，不扩大到无关画像。

## 边界

不得自动联系客户、不得替代成交决定，也不得保存或扩散不必要的客户信息。

本Skill不产生最终业务结论，不调用外部收费API，不保存用户数据。
