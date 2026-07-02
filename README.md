# 美团生活助手 (Meituan Living Assistant)

> 从 WorkBuddy 提取的独立 Agent Skill，专注于美团优惠券领取、团购搜索与下单。
> 适用于 Claude、Codex、Cursor 等各类 AI Agent 平台。

**提取日期**: 2026-06-18

---

## 简介

美团生活助手是一个通用 Agent Skill，帮助用户一键领取美团各类优惠券、搜索附近团购美食并完成下单。覆盖餐饮、饮品、咖啡、奶茶、火锅、烧烤、日料等生活服务场景。

## 功能特性

- 🎫 **一键领券** - 自动领取美团各品类优惠券
- 🔍 **团购搜索** - 根据位置和偏好搜索附近美食
- 📦 **在线下单** - 选品后直接下单支付

## 技术架构

- **入口**: `skills/meituan-living/scripts/run.js` - 统一 Node.js 入口
- **认证**: `skills/meituan-living/scripts/auth.py` - 设备 Token 管理
- **依赖**: `skills/meituan-living/scripts/vendor/cliguard/` - CLIGuard 签名模块
- **文档**: `skills/meituan-living/SKILL.md` - Skill 定义与流程说明

## 环境要求

- Node.js >= 18
- Python 3
- npm

## 安装

```bash
cd skills/meituan-living/scripts
npm install
```

## 使用方式

将本目录放置于 Agent 的 Skill/Plugin 目录下即可使用。各平台接入方式请参考对应平台的 Skill 配置文档。

### 命令行调用

```bash
# 环境初始化
node skills/meituan-living/scripts/run.js init

# 领券
node skills/meituan-living/scripts/run.js issue

# 搜索商品
node skills/meituan-living/scripts/run.js search --keyword "火锅" --lat "39.9" --lng "116.3" --city-id "1"

# 下单
node skills/meituan-living/scripts/run.js order --product-id <pid> --poi-id <pid> --city-id <id> --uuid <uuid>
```

## 目录结构

```
meituan-living/
├── README.md                   # 本文件
└── skills/
    └── meituan-living/
        ├── SKILL.md            # Skill 定义文档
        ├── references/
        │   ├── DOCTOR.md      # 诊断手册
        │   └── mt_login.png   # 登录二维码
        └── scripts/
            ├── run.js         # 统一入口
            ├── auth.py        # 认证模块
            ├── config.json    # 配置文件
            ├── package.json   # 依赖声明
            ├── *.py           # 各功能脚本
            └── vendor/
                └── cliguard/  # CLIGuard SDK
```

## 数据存储

| 文件 | 路径 | 说明 |
|------|------|------|
| 凭证 | `~/.meituan-living/credentials/token.json` | 用户 Token |
| 日志 | `os.tmpdir()/meituan-living/` | 运行日志 |

## 许可

本项目从 WorkBuddy 提取，仅供学习研究使用。
