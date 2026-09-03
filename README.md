# 学生成长管理平台

一个零依赖的单文件网页应用，用来管理多名学生的完整成长档案：基本信息、师生互动记录、学习路径、成果博客，并支持一键导出分享。

打开 `student-hub.html` 即可使用，不需要安装、不需要联网、不需要服务器。

- 仓库：https://github.com/fangxiaofen/student-growth-platform
- 在线直接用：https://fangxiaofen.github.io/student-growth-platform/student-hub.html

## 功能模块

| 模块 | 说明 |
| --- | --- |
| 总览 | 在读人数、本月互动数、成果总数、平均路径进度；最近互动、最新成果、各学生路径进度 |
| 学生管理 | 卡片列表，支持按姓名 / 班级 / 标签搜索，按分组与状态筛选；新增、编辑、删除、查看详情档案 |
| 互动记录 | 时间线展示，按学生和类型筛选（作业反馈、一对一答疑、鼓励沟通、作品点评、家长沟通）；每条记录含主题、沟通内容、下一步跟进 |
| 学习路径 | 为每位学生定制阶段目标，阶段支持待开始 / 进行中 / 已完成三态切换，自动计算完成百分比 |
| 成果博客 | 每位学生拥有独立的博客页面，含档案头与成果卡片墙（作品、获奖、证书、项目、随笔），支持发布、编辑、删除、阅读全文 |

## 快速开始

1. 下载或克隆本仓库
2. 双击 `student-hub.html`，用 Chrome / Edge 打开
3. 在「学生管理」中把内置的示例学生替换为自己的学生
4. 日常流程：课后记一条互动 → 阶段性更新学习路径 → 学生出成果时在「成果博客」发布

## 成果分享

选中学生后有三种分享方式：

- **复制分享摘要**：纯文本，可直接粘贴到微信群或邮件
- **导出博客页**：生成一个独立的 HTML 文件，自带打印按钮，可存为 PDF 发送给家长
- **浏览器打印**：直接打印当前页面

## 数据与备份

- 数据保存在浏览器的 localStorage 中，打开即自动保存，刷新不丢失
- 左下角提供「导出数据」与「导入」，导出为标准 JSON，可用于备份、迁移、多机同步

> 注意：数据仅存于当前浏览器。更换电脑或清理浏览器数据前，务必先导出备份。

## 技术说明

- 单个 HTML 文件，HTML / CSS / JS 全部内联，无任何外部依赖与 CDN
- 图标为内联 SVG，无图标字体
- 响应式布局，窄屏下侧边栏自动折叠

## 数据模型

```js
{
  students:    [{ id, name, gender, grade, group, phone, guardian, enroll, tags[], goal, status }],
  interactions:[{ id, sid, date, type, topic, content, next }],
  paths:       { [studentId]: { title, stages: [{ id, title, desc, due, status }] } },
  posts:       [{ id, sid, date, type, title, summary, content, tags[] }]
}
```

## 许可证

MIT
