# OneWiki V2 知识库 (Cold-Hot Architecture)

本知识库采用**冷热物理隔离**架构，兼顾当前极致检索效率与未来跨周期资产重生能力：

```text
one-wiki-v2/
├── wiki/    # ⚡【热层·日常检索】分级地图与自包含深度知识文档（日常检索与交互唯一入口）
│   ├── INDEX.md
│   ├── ai/
│   ├── finance/
│   └── tech/
│
└── raw/     # 🧊【冷层·永久档案】原始长文、文献与语料不可变快照备份（日常检索坚决不读）
    ├── ai/
    ├── finance/
    └── tech/
```
