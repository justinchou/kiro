# 工作流程图和可视化辅助工具

本文档提供了规范驱动开发流程的可视化表示，包括完整的工作流程图、决策树和阶段转换流程。

## 完整流程图

以下图表展示了从初始想法到实施的完整规范驱动开发工作流程：

```mermaid
stateDiagram-v2
    [*] --> Idea : 功能请求
    
    Idea --> Requirements : 开始规范流程
    
    state Requirements {
        [*] --> Draft_Req : 创建初始需求
        Draft_Req --> Review_Req : 完成草稿
        Review_Req --> Revise_Req : 反馈/修改
        Revise_Req --> Review_Req : 更新草稿
        Review_Req --> [*] : 明确批准
    }
    
    Requirements --> Design : 需求已批准
    
    state Design {
        [*] --> Research : 确定研究需求
        Research --> Draft_Design : 创建设计文档
        Draft_Design --> Review_Design : 完成草稿
        Review_Design --> Revise_Design : 反馈/修改
        Revise_Design --> Review_Design : 更新草稿
        Review_Design --> [*] : 明确批准
    }
    
    Design --> Tasks : 设计已批准
    
    state Tasks {
        [*] --> Draft_Tasks : 创建任务分解
        Draft_Tasks --> Review_Tasks : 完成草稿
        Review_Tasks --> Revise_Tasks : 反馈/修改
        Revise_Tasks --> Review_Tasks : 更新草稿
        Review_Tasks --> [*] : 明确批准
    }
    
    Tasks --> Implementation : 任务已批准
    
    state Implementation {
        [*] --> Execute_Task : 选择下一个任务
        Execute_Task --> Test_Task : 完成任务
        Test_Task --> More_Tasks : 任务完成
        More_Tasks --> Execute_Task : 是
        More_Tasks --> [*] : 否
    }
    
    Implementation --> [*] : 功能完成
    
    note right of Requirements : EARS 格式\n用户故事\n验收标准
    note right of Design : 架构\n组件\n数据模型
    note right of Tasks : 编码任务\n测试驱动\n增量式
```

## 阶段转换决策树

此决策树帮助确定何时在阶段之间移动以及何时进行迭代：

```mermaid
flowchart TD
    A[阶段完成] --> B{用户审查}
    B -->|明确批准| C[进入下一阶段]
    B -->|反馈/修改| D[修改当前阶段]
    B -->|重大问题| E{修改范围}
    
    E -->|小幅调整| D
    E -->|根本性变更| F{回到哪个阶段？}
    
    F -->|需求问题| G[返回需求]
    F -->|设计问题| H[返回设计]
    F -->|任务问题| I[修改任务]
    
    D --> J[更新文档]
    G --> K[更新需求]
    H --> L[更新设计]
    I --> M[更新任务]
    
    J --> A
    K --> A
    L --> A
    M --> A
    
    C --> N{最终阶段？}
    N -->|否| O[开始下一阶段]
    N -->|是| P[开始实施]
    
    O --> A
    P --> Q[执行任务]
```

## 需求阶段流程

需求收集阶段的详细工作流程：

```mermaid
flowchart TD
    A[功能想法] --> B[分析初始请求]
    B --> C[创建初始需求草稿]
    C --> D[使用 EARS 语法格式化]
    D --> E[添加用户故事]
    E --> F[定义验收标准]
    F --> G[考虑边缘情况]
    G --> H[呈现给用户]
    
    H --> I{用户反馈}
    I -->|已批准| J[需求完成]
    I -->|需要修改| K[确定修改区域]
    I -->|需求不明确| L[提出澄清问题]
    
    K --> M[更新需求]
    L --> N[收集额外信息]
    
    M --> H
    N --> M
    
    J --> O[进入设计阶段]
    
    style A fill:#e1f5fe
    style J fill:#c8e6c9
    style O fill:#fff3e0
```

## 设计阶段流程

设计阶段的详细工作流程：

```mermaid
flowchart TD
    A[需求已批准] --> B[确定研究需求]
    B --> C[进行研究]
    C --> D[分析发现]
    D --> E[创建架构概述]
    E --> F[定义组件]
    F --> G[设计数据模型]
    G --> H[规划错误处理]
    H --> I[定义测试策略]
    I --> J[向用户展示设计]
    
    J --> K{用户反馈}
    K -->|已批准| L[设计完成]
    K -->|需要修改| M[更新设计]
    K -->|需求差距| N[返回需求]
    
    M --> J
    N --> O[更新需求]
    O --> P[更新设计]
    P --> J
    
    L --> Q[进入任务阶段]
    
    style A fill:#fff3e0
    style L fill:#c8e6c9
    style Q fill:#f3e5f5
```

## 任务阶段流程

将设计分解为实施任务的详细工作流程：

```mermaid
flowchart TD
    A[设计已批准] --> B[分析设计组件]
    B --> C[确定实施顺序]
    C --> D[创建任务层次结构]
    D --> E[定义任务依赖关系]
    E --> F[添加需求引用]
    F --> G[确保测试驱动方法]
    G --> H[验证任务完整性]
    H --> I[向用户展示任务]
    
    I --> J{用户反馈}
    J -->|已批准| K[任务完成]
    J -->|需要修改| L[更新任务]
    J -->|设计问题| M[返回设计]
    J -->|需求问题| N[返回需求]
    
    L --> I
    M --> O[更新设计]
    N --> P[更新需求]
    
    O --> Q[更新任务]
    P --> R[更新设计和任务]
    
    Q --> I
    R --> I
    
    K --> S[开始实施]
    
    style A fill:#f3e5f5
    style K fill:#c8e6c9
    style S fill:#ffecb3
```

## 实施执行流程

从实施计划执行单个任务的工作流程：

```mermaid
flowchart TD
    A[任务已批准] --> B[选择下一个任务]
    B --> C{有子任务？}
    C -->|是| D[先执行子任务]
    C -->|否| E[阅读需求和设计]
    
    D --> F[完成所有子任务]
    F --> G[标记父任务完成]
    
    E --> H[实施任务]
    H --> I[编写测试]
    I --> J[根据需求验证]
    J --> K[标记任务完成]
    
    G --> L{还有更多任务？}
    K --> L
    
    L -->|是| B
    L -->|否| M[功能完成]
    
    style A fill:#ffecb3
    style M fill:#c8e6c9
```

## 反馈循环模式

处理反馈和迭代的常见模式：

```mermaid
flowchart LR
    subgraph "正向反馈循环"
        A1[完成阶段] --> B1[用户审查]
        B1 --> C1[批准]
        C1 --> D1[下一阶段]
    end
    
    subgraph "修改循环"
        A2[完成阶段] --> B2[用户审查]
        B2 --> C2[反馈]
        C2 --> D2[修改]
        D2 --> A2
    end
    
    subgraph "回溯循环"
        A3[当前阶段] --> B3[重大问题]
        B3 --> C3[上一阶段]
    end
```