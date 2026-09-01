# ArcVita-Data — 人物传记结构化数据

> ArcVita 主仓库的数据子模块：人物-时间-地点，做事时间流。
> 主库：https://github.com/est/ArcVita

## 目录结构

```
.
├── seed_persons.yaml        # 人物清单（qid / role / sensitivity）
├── curated/                 # 离线精编（curated.py 的真源）
│   └── classical/           # 先秦-秦汉等分朝代精编
├── extracted/               # AI 从古籍提取的中间产物（pre_qin / qin_han / king_tables）
├── processed/               # 流水线产出（persons/events/endeavors/highlights/timelines）
│   ├── persons.yaml
│   ├── events.yaml
│   ├── endeavors.yaml
│   ├── highlights.yaml
│   ├── historical_contexts.yaml
│   ├── king_tables.yaml
│   └── timelines/
├── raw/                     # Wikidata/Wikipedia 原始缓存（默认不入库，可重建）
└── biography.db             # SQLite 衍生库（可重建，默认不入库，见 .gitignore）
```

## 协议

- **Code 归属**：本仓库仅存数据，不含代码，许可证见 `LICENSE-DATA.md`。
- **数据许可**：**CC BY-SA 4.0** — 复用需署名 `Data from ArcVita (https://github.com/est/ArcVita), derived in part from Wikidata (CC0) and Wikipedia (CC BY-SA 4.0), curated additions CC BY-SA 4.0.`
- **上游**：Wikidata (CC0) + Wikipedia (CC BY-SA 4.0) + 自编 `curated/` (CC BY-SA 4.0)。

## 使用方式

### 作为主库 submodule（推荐）

```bash
git clone --recursive git@github.com:est/ArcVita.git
# 或已克隆后
git submodule update --init --recursive
```

主库 `config.yaml` 的 `paths.*` 默认指向 `data/...`，挂载后无需改配置。

### 单独使用

```bash
uv run python -m arcvita.cli --help  # 在主库执行，读取本仓库的 yaml
```

## 贡献

- `curated/` 需人工审核，`extracted/` 为 AI 中间产物勿直接改，`processed/` 由流水线生成勿手改。
- 详见主库 `README.md` 与 `tests/` 校验规则。

## 版本

- `main` 分支为最新全量，历史版本用 tag 归档（如 `v0.1.0`）。
