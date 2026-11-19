# StudyOnTV 一年级上题库

给「题了个题」（[StudyOnTV](https://github.com/chadyi/StudyOnTV)）用的一年级上学期题库，按官方[题库格式](https://github.com/chadyi/StudyOnTV/blob/main/docs/question-format.md)整理，可直接在家长面板「题库 → 在线题库」里添加。

## 内容

| 项目 | 值 |
|---|---|
| 题数 | 3916 |
| 学科 | 语文 1793、数学 1853、常识 208、英语 62 |
| 年级 | 一年级（上期） |
| 题型 | 单选 3108、判断 617、多选 191 |
| 解析 | 每题都有（`tip` 字段） |
| 题库名 | 一年级上 · 语文数学常识题库 |

知识点覆盖：拼音（声母 / 韵母 / 整体认读音节 / 声调标调 / 音节拼读）、识字写字（字音字形、笔顺笔画）、偏旁部首、词语（量词、反义词）、课文古诗、10 以内加减与比较排序、生活中的安全与文明常识、英语基础词汇。

## 怎么用

**方式一：家长面板添加（推荐）**

1. 打开「题了个题」家长面板 → 题库 → 在线题库；
2. 填入下面任一地址：

```
https://raw.githubusercontent.com/missyouling/studyontv-banks/main/banks/grade1-general.json
```

或 CDN 加速地址：

```
https://cdn.jsdelivr.net/gh/missyouling/studyontv-banks@main/banks/grade1-general.json
```

3. 确认后 App 会去重导入，同一道题不会重复加。

**方式二：本地导入**

下载 `banks/grade1-general.json`，在家长面板「题库 → 导入」里选择该文件即可。

**方式三：API**

```bash
curl -X POST http://<设备地址>:8099/api/questions \
  -H "Authorization: Bearer <令牌>" \
  -H "Content-Type: application/json" \
  -d @banks/grade1-general.json
```

## 文件结构

```
.
├── index.json                  # 题库索引（name / count / sha256 / 下载地址）
├── banks/
│   └── grade1-general.json     # 题库本体，version 2 格式
├── LICENSE                     # CC BY 4.0
└── README.md
```

`banks/grade1-general.json` 顶部字段：`name`、`version`（2）、`subject`、`level`、`author`、`license`、`description`、`items`。

## 数据来源

本仓库题目由家长自行整理与生成，含人工校对与规则校验：

- 题干唯一，无重复题；
- 选项 2–8 个、无空项、无重复项；
- 单选 `k` 与多选 `correctIndices` 全部落在选项范围内；
- 判断题选项固定为「正确 / 错误」，`k` 为 0 / 1；
- 难度统一在 1–5 星。

不包含任何孩子的姓名、学校、住址等个人信息。

## 许可

题库内容按 [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.zh) 授权，转载或改编请注明来源。
