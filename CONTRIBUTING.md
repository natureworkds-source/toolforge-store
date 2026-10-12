# 向工具商店投稿

## 作者步骤（公开仓库）

1. 在工具仓执行 `pnpm pack:store`，得到 `.tfpkg` 与 `.artifact.json`。
2. 上传到**自有公开** GitHub/Gitee Release（同版本字节不可变）。
3. Fork 本仓，在 `catalog.json` 的 `plugins` 中新增或追加 `versions` 条目：
   - `id` / `version` 与 manifest 一致
   - `artifacts[].url` 为**可匿名下载**的永久 Release 地址
   - `artifacts[].sha256` / `size` 与本地 `.artifact.json` 一致
   - `target` 使用 `universal`
4. 开 PR，说明源码 tag、冒烟结果、联系方式。

## 作者步骤（私有仓库）

维护者**默认无法**访问你的私有仓与私有 Release，审核不依赖它们。

1. 本地 `pnpm pack:store`。
2. （可选）在自有私有仓发 Release 仅作作者归档，**不要**把私有 URL 当作客户端或审核下载入口。
3. 在本仓开 **Issue**（推荐）或 PR，提供：
   - `id`、`version`、`sha256`、`size`、源码 tag
   - **直接附上 `.tfpkg`**（或短期可匿名下载的网盘/对象存储链接）
   - 注明：「源码仓私有，请维护者镜像到本仓公开 Release 后再写入 catalog」
4. 不要在 `catalog.json` 里填写私有 Release URL；公开永久 `url` 由维护者镜像后填写。

## 维护者（公开投稿）

1. 从作者公开 Release 下载候选包，核对本机 sha256。
2. 安装到本机 `{appData}/tools/<id>/` 或经应用「工具商店」冒烟。
3. 合并 PR；同步 `catalog.json` 到 Gitee 公开 raw。

## 维护者（私有投稿）

1. **只使用投稿附件（或作者提供的临时公开链接）**，不要依赖作者私有仓权限。
2. 核对本机 sha256 / size 与投稿元数据一致；解压或宿主安装冒烟。
3. 将同一字节的 `.tfpkg` 上传到本仓**公开** Release（建议 tag：`store-<id>-<version>`）。
4. 在 `catalog.json` 写入条目，`artifacts[].url` 指向该公开 Release；合并 PR 后同步 Gitee。
5. 同版本禁止改字节；修复发新 version。
