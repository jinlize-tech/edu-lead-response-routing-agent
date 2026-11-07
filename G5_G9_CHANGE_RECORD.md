# G5/G9 产品修改记录

- 产品编号：$(@{number=25; product_id=JLZ-EDU-AG-004; chinese_name=线索响应调度; english_name=Lead Response Routing Agent; repository_name=edu-lead-response-routing-agent; repository_url=https://github.com/jinlize-tech/edu-lead-response-routing-agent; product_type=Agent; category_code=02; category=02 销售转化中心; description=线索响应优先级、人员分配和处理计划。; target_users=System.Object[]; core_input=线索池、来源、意向标签、校区/顾问能力、响应时限和排班; main_output=优先级规则、分派表、响应SLA、超时升级路径和负载检查; product_risk=自动处理真实客户信息或产生歧视性分配; dedup_label=需要明确差异化; dedup_note=与MT-CRM区分：只生成一次分派方案和规则，不保存或自动操作客户记录。; development_status=Planned / 待研发; license=Apache-2.0; spec_version=1.0.0; workbuddy_status=PLANNED_FOR_WORKBUDDY}.product_id)
- 产品名称：线索响应调度
- 基线：EDUCATION_BASELINE_V1.0.0
- 基线提交：$BaselineCommit
- 原版本：1.0.0
- 新版本：1.0.1

## 本次修改

1. 强化产品专属执行流程、输入核对和输出验收规则。
2. 新增 scripts/validate_input.js，实际检查必填字段、冲突、未确认数据和敏感信息。
3. 新增正常、缺失、冲突、敏感信息和非法JSON场景输入。
4. 测试升级为 T1–T7 分层并保存逐项检查结果。
5. 安装包加入 Apache-2.0 LICENSE 和 THIRD_PARTY_NOTICES.md。
6. 安装包升级为 1.0.1，加入许可证、第三方声明和输入校验脚本，保留 1.0.0 ZIP。
7. 按本产品冻结规格补充专属处理规则、输入到成果的核对矩阵和去重边界。

## 产品专属增强

- 核心任务：线索响应优先级、人员分配和处理计划。
- 主要风险：自动处理真实客户信息或产生歧视性分配
- 去重边界：与MT-CRM区分：只生成一次分派方案和规则，不保存或自动操作客户记录。

- 按线索阶段、客户需求、决策角色、时间窗口和最近一次有效沟通建立判断依据。
- 区分客户原话、顾问记录和推断，不能把未确认意向当作成交承诺。
- 将下一步动作写到责任人、时间、渠道和完成标准，避免只给沟通话术。
- 涉及敏感客户信息时仅保留完成当前判断所需字段，不扩大到无关画像。

## 运行边界

- 本地模型行为：NOT_RUNTIME_VERIFIED
- WorkBuddy平台验证：WORKBUDDY_VALIDATION_NOT_IN_SCOPE
- 本轮不执行上传、安装、审核或正式发布。
