# 向工具商店投稿

## 作者步骤

1. 在工具仓执行 `pnpm pack:store`，得到 `.tfpkg` 与 `.artifact.json`。
2. 上传到**自有** GitHub/Gitee Release（版本不可变）。
3. Fork 本仓，在 `catalog.json` 的 `plugins` 中新增或追加 `versions` 条目：
   - `id` / `version` 与 manifest 一致
   - `artifacts[].url` 为 Release 永久下载地址
   - `artifacts[].sha256` / `size` 与本地 `.artifact.json` 一致
   - `target` 使用 `universal`
4. 开 PR，说明源码 tag、冒烟结果、联系方式。

## 维护者

1. 下载候选包，核对本机 sha256。
2. 安装到本机 `{appData}/tools/<id>/` 或经应用「工具商店」冒烟。
3. 合并 PR；同步 `catalog.json` 到 Gitee 公开 raw。
