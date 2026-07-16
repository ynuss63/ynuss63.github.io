# 管理指南

## 本地项目位置
`C:\Users\Administrator\Desktop\ynu-math-exam\website\`

网站源码、配置、PDF 都在这个文件夹里。

## 常用操作

### 如何 push（上线）
每次修改完文件，打开 Git Bash，依次运行：
```bash
export PATH="/c/Ruby32-x64/bin:$PATH"
cd "/c/Users/Administrator/Desktop/ynu-math-exam/website"
git add -A
git commit -m "描述你的修改"
git push origin master
```
推送后等 1-2 分钟，网站自动更新到 https://ynuss63.github.io/

### 添加新试卷
把 PDF 放入 `assets/pdfs/{对应拼音课程}/`（拼音对照见下表），文件名按规范改好，然后 push。

### 修改网站配置
编辑 `_config.yml`（标题、邮箱、URL 等），然后 push。

### 修改导航栏
编辑 `_data/navigation.yml`，然后 push。

### 修改首页内容
编辑 `index.md`，然后 push。

### 修改投稿指南
编辑 `_pages/contribute.md`，然后 push。

### 如何找我帮忙
把需求描述清楚发给我就行，比如：
- "帮我把 X 课程的所有试卷年级从 24 改成 22"
- "帮我在导航栏新增一门课"
- "帮我修复某页面的分组显示"

## 试卷命名规范
`{年级}级_{课程}_{考试类型}.pdf`

例如：`24级_拓扑_期末1.pdf`

## 课程名与拼音对照

| 中文 | 拼音（PDF目录）|
|------|---------------|
| 数学分析 | shuxue-fenxi |
| 高等代数 | gaodeng-daishu |
| 概率论 | gailv-lun |
| 拓扑 | tuopu |
| 泛函分析 | fanhan-fenxi |
| 微分几何 | weifen-jihe |
| 傅里叶分析 | fuliye-fenxi |
| 实变函数 | shibian-hanshu |
| 复变函数论 | fubian-hanshulun |
| 抽象代数 | chouxiang-daishu |
| 数论 | shulun |
| 数学物理方程 | shuxue-wuli-fangcheng |
| 集合论 | jihe-lun |
| 数理统计 | shuli-tongji |
| 数学建模 | shuxue-jianmo |
| 现代几何基础 | xiandai-jihe-jichu |
| 电动力学 | diandong-lixue |
