graph TD
    subgraph 供应商层
        A[生产商/供应商] -->|原材料/商品| C
        B[生鲜食品供应商] -->|新鲜食材/成品| C
        D[日配商品供应商] -->|牛奶/酸奶/面包等| C
        E[杂货/常温商品供应商] -->|零食/饮料/日用品等| C
        F[特定商品供应商] -->|报纸/部分面包/本地商品| G[门店]
    end

    subgraph 物流枢纽层 - CDC
        C[共同配送中心] -->|集约化分拣| H
        C -->|集约化分拣| I
        C -->|集约化分拣| J
    end

    subgraph 运输层
        H[常温运输车队] -->|常温商品| G
        I[冷藏运输车队] -->|冷藏商品| G
        J[冷冻运输车队] -->|冷冻商品| G
    end

    subgraph 门店层
        G[711便利店门店]
    end

    subgraph 信息流 & 管理
        K[总部/区域中心] -->|供应链策略/标准/系统| C
        K -->|供应商管理/合同| A, B, D, E, F
        K -->|门店指导/订单规则| G
        G -->|POS销售数据/订单需求| K
        K -->|需求预测/补货指令| C
        C -->|库存信息/到货计划| G
        C -->|库存信息/运作数据| K
    end

    %% 标注关键流程
    classDef highlight fill:#f9f,stroke:#333,stroke-width:2px;
    class C,H,I,J highlight
    linkStyle 0,1,2,3,4,5,6,7,8,9,10,11,12,13,14,15 stroke:#333,stroke-width:1px;
    linkStyle 16,17,18 stroke:blue,stroke-width:2px; %% 信息流用蓝色突出
