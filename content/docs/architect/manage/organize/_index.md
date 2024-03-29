---
Categories : ["设计"]
title: "组织"
date: 2018-10-10T20:12:11+08:00
---

# 组织 
    系统划分与组织划分
        康威定律
            系统架构是公司组织架构的反映
            按业务闭环进行系统拆分/组织架构划分，实现闭环/高内聚低耦合，减少沟通成本
            沟通出现问题，考虑调整组织架构
            在该拆分时拆分
    为了简单
        开发和运维分离
        业务和基础架构分离
        无状态和有状态分离
        业务间乘法(正交)而非加法                # 升维的特点, 正交叠加
        多层抽象, 不断隐去底层(约定大于配置)    # 升维的特点, 抽象观察
# 管理 
## 责任
    提供
        问题: 定义, 分解, 什么是问题, 前人如何处理
            # 工程为解决问题
        思考: 方向, 为了解决问题, 找到关键, 找到应学知识
            # 创造性工作要思考
        体系: 领域的体系, 领域体系形成原因, 为了高效思考和学习, 有体系的做事
        参考: 参考书籍, 如何筛选, 如何搜索, 社区
    不提供
        知识点, 答案, 规定, 代码
    分任务
        出问题，写相关文档
        砸需求，看弹性
        任务列表: 难度, 优先级, 排期, 地平线目标, 现状, wishlist
        nice to have给新人
## 方法
    人员
        TeamLeader -> Owner
        需求磨砺核心业务资产(事情成就精英团队，而非精英团队成就事)
    问题定义
        完成不动点需求
            正交、简单(要求想清楚、灵活)
        维护概念完整性、一致性(纯洁)
            术语不变、不矛盾、不重叠
            考虑上下游
    代码问题
        问题原因：开发的碎片化(重复的代码、由于不知道或怕改错)
        解决方法
            代码Review，集体评审
            持续集成(*lint, CI/CD): 早合并、自动构建、测试
        问题管理
            需求池
                优先级、排期、checklist、周update
            文档知识库(Confluence, Notion)
            问题追踪（Jira)
            迭代(周冲刺, hackson)
    产出评估角度
        口碑、解决问题。
            良心，内驱力
        Owner,  鼓励设计、技术自由(开发人员诉求技术，厌倦业务)
        效率第一: 加班是能力问题
            时间，代码量
        犯错问题: 总会犯错，多做多错
            不能赶期，不怕delay
## 制度
# 模型
## 开发模型
    TDD(test-driven development)
        先单元测试
    BDD(behavior-driven development)
        TDD的变种, 重点描述行为
    面向需求
        组织上小而全
        开发全栈减少沟通
        设计上面向领域
## 迭代模型
    极限编程（XP）  # eXtreme Programming
        4大价值
            沟通：鼓励口头沟通，提高效率
            简单：够用就好
            反馈：及时反馈、通知相关人
            勇气：拥抱变化，敢于重构
        5个原则
            快速反馈
            简单性假设
            逐步修改
            提倡更改（小步快跑）
            优质工作（质量是前提）
        5个工作
            阶段性冲刺
            冲刺计划会议
            每日站立会议
            冲刺后review
            回顾会议
    结对编程
    PDCA循环质量管理
        Plan, Do, Check, Act
    FMEA
        分析潜在的失效模式
## 工程模型
    历史
        程序设计阶段1946-1955  节省空间
        软件设计阶段1956-1970  硬件发展，软件危机
        软件工程阶段1970-今    组件化
###  瀑布模型
    # 每一次执行工作流的深度不同
    可行性分析
        实现会不会复杂，尽量简单
    需求分析
        分类
            生存点
            痒点
            兴奋点
        # 不会按时交付（只完成主要，然后延期，用户测试）
        客户沟通，同类产品比较，行业标准
        功能
            正确, 可行, 必要, 有序, 明确, 一致
        性能
        完善, 简短
    设计
        先出成果再优化
        任务分配(进度条)
        命名标准
        文档
        可移植、可维护易扩展
        排期
    实现
    测试
    运维
### 螺旋模型
    # 边分析边开发边交付（一环一环向目标实现）
    敏捷开发
        项目面临的问题
            人员流动
            代码维护
        种类
            极限编程(xp)
        特点
            简易、交流、回馈
        方法
            解耦低速设备，提高响应速度
    迭代
        迭代周期
            一个迭代周期中不新添加需求
            一个迭代周期中包含多次迭代
            一个阶段的结束称之为里程碑
        初始化阶段增量
            项目启动
            建立业务模型
            定义业务问题域
            找出主要风险因素
            定义项目需求的外延
            创建业务问题域的相关说明文档
        细代阶段增量
            高层的分析与设计
            建立项目的基础框架
            监督主要的风险因素
            制订达成项目目标的创建计划
        构建阶段增量
            代码及功能的实现
        移交阶段增量
            向用户发布产品
            beta测试(alpha测试是内部测试， beta测试是用户测试)
            执行性能调优，用户培训和接收测试
## 转型
    流程
        (2-4)周实地调研痛点
        确定目标
            要求: 领先、高效、高品质
            列出实际问题
        评估
            cmmi(敏捷成熟度模型): 代码、架构、工具
        实施变化
            战略
            试点团队(灰部应用于组织): 完成产品指标
# 工具功能
    控制面板
        项目
        分配给我
        活动日志
    人员
        团队
        权限
    项目
        配置
            事务
                类型
                布局            # 列表项，详细项
                时间追踪
                配置链接关系
                优先级
                解决方案
            工作流              # 对不同项目和事务类型, 配置状态转换图
            页面方案            # 对不同项目和事务类型，不同状态转换时，配置字段布局
            自定义字段          # 对不同页面
            权限
                权限
                角色、应用程序、组、用户、项目负责人、当前经办人、自定义字段值等
    事务(issue)
        状态
            todo, 正在进行, done
            打开, 已重新打开, 已解决, 已关闭
            backlog, in review, selected for development, building, build broken
            waiting for support, respond to customer, escalate, cancel, canceled, done
            waiting for approval, work in progress
            [工作流状态]
        类别
            待办
            正在进行
            完成
            无类别
        名称
            长篇故事(史诗)
            故事
                分类: 需求, 设计
                验收条件
            任务, 子任务, 缺陷, 新增功能, 改进
            服务请求, 服务请求审批, 问题, 事件(系统中断)
        订单
            全局顺序
        属性
            经办人，报告人
            优先级
                highest, hign, medium, low, lowest
        链接
            clones
            is cloned by
            duplicates
            is duplicated by
            blocks
            is blocked by
            causes
            is caused by
            relates to
        csv导入
        筛选器
            未清, 我发起, 已完成, 最近
        活动
            评论, 历史, 工作日志
    冲刺(sprint)
        状态
            待办, 进行, 完成
    发布
        版本
    报告(report)
        敏捷
            燃耗图, 燃尽图, 版本报告, 长篇故事报告, 控制图，长篇故事燃尽图, 发布燃尽图
            冲刺报告, 速率表
            累积流程图
        事务
            饼图, 单次分组, 解决时间, 平均周期, 事务持续时间, 已创建已解决对比, 最新创建
        预测
            版本工作量, 人员工作量, 时间跟踪
        其它
            工作负荷
    服务台(itsm)
        分类
            对内
            对外
        途径
            邮件, 帮助中心, 小程序
        队列
            分类
            状态workflow
            经办人
        客户
        报告
    系统
        审计日志