# 3Jane Farm 收益计算器

一个可直接部署到 GitHub Pages 的静态收益计算器，用于估算 3Jane Farm 相关策略的收益。

作者 X/Twitter：<https://x.com/MengLayer>

## 数据来源

- 3Jane Convex：`https://opulent-crocodile-74.convex.cloud`
- 3Jane Farm：`https://app.3jane.xyz/farm`
- Pendle API：`https://api-v2.pendle.finance`
- Morpho API：`https://api.morpho.org/graphql`
- Curve API：`https://api.curve.finance/api`

## 计算说明

- 默认持有天数为今天到 `2026-12-17`，也就是 Pendle YT 到期日。
- 默认参数为 `100M` JANE FDV 和 `3.33B` JANE 数量。
- JANE 价格按 `JANE FDV / JANE 数量` 计算。
- JANE 奖励按页面/接口的每周 JANE 分配计算：`每周 JANE 分配 * 用户资产 / 该资产 reward TVL * 持有周数`。
- 3Jane 实时 emissions APR 先从项目原始口径 `250M FDV / 6.66B supply` 归一化。
- YT 策略使用 Pendle 实时 YT 价格计算可买到的 YT 数量。
- YT 的用户资产按 `本金 / YT 实时价格` 换算为 YT notional，再参与每周 JANE 分配。
- YT 最终盈亏按 `YT 底息收益 + 到期 JANE 数量 * JANE 价格 - 到期归零的 YT 成本` 计算。
- YT TVL 优先显示 `rewards denominator notional * 实时 YT 价格` 的资本口径。
- Pendle PT TVL 在 3Jane emissions TVL 为 0 时，会回退到 Pendle 市场流动性加订单簿规模。

## GitHub Pages

1. 将 `index.html`、`styles.css`、`app.js`、`README.md` 和 `.nojekyll` 放在仓库根目录。
2. 打开 GitHub 仓库 `Settings` -> `Pages`。
3. 选择 `Deploy from a branch`。
4. 选择 `main` 分支和 `/root` 目录。

本项目不需要构建步骤。
