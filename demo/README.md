# 5 分钟演示

用一份**虚构的示例论文**（`papers/sample-paper.md`）跑通"读论文 → 卡片"，不需要你自己找 PDF。

## 步骤

1. 在 DSH 里打开这个 `demo/` 目录作为工作区。
2. 新会话，发：

   > 读 `papers/sample-paper.md`，用 literature-card 技能生成一张文献卡片，写到 `cards/` 下。

3. 对比 `expected/cards/rag-long.md`，检查：
   - 十个字段是否齐全；
   - 数字是否与原文一致（72.4% / 66.2% / 1.9s / 2.3s）；
   - 缺失信息是否标【原文未提及】；
   - 原文文件路径能否回找到 `papers/sample-paper.md`。

## 说明

示例论文是虚构的（文中已注明），只用于验证流程，不可引用。真实使用时把 PDF 放进 `papers/`，其余步骤相同。
