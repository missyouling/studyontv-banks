# StudyOnTV 一年级上题库

给「题了个题」（[StudyOnTV](https://github.com/chadyi/StudyOnTV)）用的一年级上学期题库，按官方[题库格式](https://github.com/chadyi/StudyOnTV/blob/main/docs/question-format.md)整理，在家长面板「题库 → 在线题库」里填地址即可添加。题目按 `一年级上期-学科-知识点` 分级，导入后可以直接按知识点筛选练习。

## 已有题库

| 名称 | 题量 | 学科 | 年级 | 知识点分组 | 题型 | 许可 | 详细说明 | 文件 |
|---|---|---|---|---|---|---|---|---|
| 一年级上 · 语文数学常识题库 | 3916 | 语文/数学/常识/英语 | 一年级 | 29 组 | 单选/判断/多选 | CC BY 4.0 | [说明](./banks/grade1-general.md) | [json](./banks/grade1-general.json) |

各学科分组数与题量：

| 学科 | 分组数 | 题量 |
|---|---|---|
| 语文 | 11 | 1793 |
| 数学 | 9 | 1853 |
| 常识 | 6 | 208 |
| 英语 | 3 | 62 |

共 **3916 道**，每题带解析。分组明细见 [题库详细说明](./banks/grade1-general.md)。

## 怎么用

**方式一：家长面板在线添加（推荐）**

1. 打开家长面板 → 题库 → 在线题库；
2. 填入题库地址：

```
https://raw.githubusercontent.com/missyouling/studyontv-banks/main/banks/grade1-general.json
```

CDN 加速地址：

```
https://cdn.jsdelivr.net/gh/missyouling/studyontv-banks@main/banks/grade1-general.json
```

3. 确认后 App 会按题干去重导入，不会和已有题目重复叠加；导入完成后在题库筛选里选择「一年级上期-…」开头的分组即可。

**方式二：本地导入**

下载 `banks/*.json`，在「题库 → 导入」里选择文件，解析预览后确认。

**方式三：API**

```bash
curl -X POST http://<设备地址>:8099/api/questions \
  -H "Authorization: Bearer <令牌>" \
  -H "Content-Type: application/json" \
  -d @banks/grade1-general.json
```

## 仓库结构

```
.
├── index.json                      # 题库索引（名称/题数/许可/sha256/下载地址）
├── banks/
│   ├── grade1-general.json         # 题库本体（version 2）
│   └── grade1-general.md           # 该题库的详细说明：选题、知识点分级、题型、例题
├── README.md                       # 本文件：方向概述、使用方法、题库清单
└── LICENSE                         # CC BY 4.0
```

## 题库规范

每份题库是一个 `.json` 文件，放在 `banks/` 下，顶部写 `name`、`version: 2`、`subject`、`level`、`author`、`license`、`description`；题目放 `items`，`bank` 字段用「<年级>-<学科>-<知识点>」命名。每份题库配一份同名 `.md` 说明（`banks/<文件名>.md`），写清选题范围、知识点分级、题型与难度、典型例题。

字段与校验细则见官方文档：[题库格式参考](https://github.com/chadyi/StudyOnTV/blob/main/docs/question-format.md)。

## 数据校验

- 题干全局唯一；选项 2–8 个、无空项；答案下标不越界；
- 判断题只写 `k`（0 正确 / 1 错误）；难度 1–5 星；
- 全部题目带解析；不含孩子姓名、学校、住址等个人信息。

## 许可

题库内容按 [CC BY 4.0](./LICENSE) 授权，转载或改编请注明来源。
