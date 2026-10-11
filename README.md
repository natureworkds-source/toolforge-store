# Tool Forge Store（策展目录）

天工智钥 / NatureWork Tool Forge 外部工具商店的**目录元数据仓**。

- 本仓只存 `catalog.json`（及投稿说明），**不托管** `.tfpkg` 二进制。
- 作者把候选包放到自有 GitHub/Gitee Release，再向本仓提 PR。
- 维护者审阅合并后，将 `catalog.json` 同步到公开 Gitee（客户端默认读取处）。

## 客户端读取

| 环境 | URL |
| --- | --- |
| GitHub raw（审稿 / 联调） | `https://raw.githubusercontent.com/natureworkds-source/toolforge-store/main/catalog.json` |
| Gitee（正式默认，待同步） | `https://gitee.com/natureworkds/toolforge-store/raw/master/catalog.json` |

## 投稿

见 [CONTRIBUTING.md](./CONTRIBUTING.md)。
