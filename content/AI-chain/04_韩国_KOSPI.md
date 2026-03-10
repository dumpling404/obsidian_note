# 🇰🇷 韩国综合股价指数（KOSPI）— 韩国

> **产业链角色：** 内存芯片（DRAM/NAND）· 高带宽内存（HBM）· 显示屏 · 晶圆代工
> 信息来源：CNN Business、Sourceability、Tom's Hardware/SEMI（2024–2026）

---

## 指数概览

| 指数 | 成分股数量 | 核心板块 |
|------|----------|---------|
| **KOSPI** | 约800家大中型企业 | 半导体、显示、造船 |
| **KOSDAQ** | 约1,600家中小企业 | 科技创业、生物技术 |

**KOSPI 2025年涨幅：+76%，为1999年以来最佳年份**（CNN Business，2026年1月）

---

## 产业链地位：全球存储之王

```mermaid
flowchart TD
    subgraph Korea["🇰🇷 韩国 — 存储芯片绝对主导"]
        SKH["SK海力士<br/>全球HBM供应约50%<br/>HBM3E全球首发<br/>HBM4路线图已确定"]
        SAM["三星电子<br/>DRAM + NAND全球第一<br/>HBM3资质认证（2024年）<br/>晶圆代工全球第二<br/>2025年股价+130%"]
        DISP["三星显示 / LG Display<br/>OLED面板<br/>AI设备显示屏"]
    end

    SKH -->|HBM模组送往| COWOS["🇹🇼 台积电 CoWoS<br/>先进封装"]
    COWOS -->|驱动| NVDA["🇺🇸 英伟达 H100/B100<br/>AI加速器"]
    SAM -->|DRAM + HBM| NVDA

    style SKH fill:#50c878,color:#000
    style SAM fill:#4a90d9,color:#fff
```

---

## HBM在AI训练中的层级结构

```mermaid
graph TD
    A["AI训练工作负载<br/>（LLM、视觉模型等）"] --> B["需要超大带宽<br/>与超高容量"]
    B --> C["HBM3 / HBM4<br/>高带宽内存"]
    C --> D["SK海力士 约50%份额<br/>三星加速追赶<br/>美光 2025年约23-24%"]
    B --> E["标准DRAM"]
    E --> F["三星全球第一<br/>SK海力士第二<br/>美光第三"]
    B --> G["NAND闪存 / 存储"]
    G --> H["三星全球第一<br/>3D NAND投资+45%（2025）"]

    style C fill:#ff6b6b,color:#fff
    style D fill:#50c878,color:#000
```

---

## HBM完整供应链时序

```mermaid
sequenceDiagram
    participant Design as 🇺🇸 英伟达（芯片设计）
    participant HBM as 🇰🇷 SK海力士（HBM内存）
    participant Fab as 🇹🇼 台积电（CoWoS封装）
    participant DC as 🇺🇸 数据中心

    Design->>HBM: 提交HBM4规格需求
    HBM->>HBM: 制造并堆叠HBM芯片
    Design->>Fab: 发送GPU裸片规格
    Fab->>Fab: 3nm制程制造GPU裸片
    HBM->>Fab: 交付HBM模组
    Fab->>Fab: CoWoS封装（HBM与GPU键合）
    Fab->>DC: 交付完整H100/B100模组
```

---

## 主要公司与产业链层级

| 公司 | 产业链层级 | 角色 |
|------|----------|------|
| **SK海力士** | 第四层——存储 | HBM全球第一，约50%份额 |
| **三星电子** | 第三+四层——代工+存储 | DRAM第一、代工第二、HBM追赶中 |
| **三星显示/LG Display** | 第七层——设备显示 | AI设备OLED面板 |
| **韩美半导体** | 第三层——封装设备 | HBM热压键合机设备商 |

---

## 核心数据

| 指标 | 数值 | 来源 |
|------|------|------|
| SK海力士HBM全球份额 | **约50%** | Sourceability 2025 |
| HBM交货周期（2024-25） | **6–12个月** | Sourceability |
| HBM3价格同比涨幅 | **+20–30%** | Sourceability |
| 三星电子2025年股价涨幅 | **+130%** | CNN Business 2026 |
| KOSPI 2025年回报 | **+76%** | CNN Business 2026 |
| DRAM设备销售（2025年） | **+15.4%至225亿美元** | Tom's Hardware/SEMI |

---

## 相关标签
`#韩国` `#KOSPI` `#HBM` `#内存芯片` `#SK海力士` `#三星` `#DRAM`

## 双向链接
[[00_AI产业链导航MOC]] · [[01_AI产业链总览]]
