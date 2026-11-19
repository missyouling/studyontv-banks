# StudyOnTV 一年级上题库
给「题了个题」（[StudyOnTV](https://github.com/chadyi/StudyOnTV)）用的一年级上学期题库集合，按官方[题库格式](https://github.com/chadyi/StudyOnTV/blob/main/docs/question-format.md)整理，在家长面板「题库 → 在线题库」里填地址即可添加。

## 已有题库
| 名称 | 题量 | 学科 | 年级 | 题型 | 许可 | 详细说明 | 文件 |
|---|---|---|---|---|---|---|---|
| 一年级上 · 语文数学常识题库 | 3916 | 语文/数学/常识/英语 | 一年级 | 单选/判断/多选 | CC BY 4.0 | [说明](./banks/grade1-general.md) | [json](./banks/grade1-general.json) |

- 总题量 **3916 道**，每题带解析；
- 学科：语文 1793、数学 1853、常识 208、英语 62；
- 知识点：拼音（声母/韵母/整体认读/声调/拼读）、识字写字、偏旁部首、词语、课文古诗、口算与应用、生活常识、英语基础。

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

3. 确认后 App 会按题干去重导入，不会和已有题目重复叠加。

**方式二：本地导入**

下载对应的 `banks/*.json`，在「题库 → 导入」里选择文件，解析预览后确认导入。

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
│   └── grade1-general.md           # 该题库的详细说明：选题、题型、难度、例题
├── README.md                       # 本文件：方向概述、使用方法、题库清单
└── LICENSE                         # CC BY 4.0
```

## 题库规范
每份题库是一个 `.json` 文件，放在 `banks/` 下，顶部字段 `name`、`version: 2`、`subject`、`level`、`author`、`license`、`description`，题目放在 `items` 里；每份题库配一份同名 `.md` 说明文档（`banks/<文件名>.md`），写清选题范围、题型与难度、典型例题和使用建议。

字段与校验细则见官方文档：[题库格式参考](https://github.com/chadyi/StudyOnTV/blob/main/docs/question-format.md)。

## 数据校验
- 题干全局唯一；选项 2–8 个、无空项；答案下标不越界；
- 判断题选项固定「正确 / 错误」；难度统一 1–5 星；
- 全部题目带解析；不含孩子姓名、学校、住址等个人信息。

## 许可
题库内容按 [CC BY 4.0](./LICENSE) 授权，转载或改编请注明来源。
