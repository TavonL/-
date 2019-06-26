# agriwx

> 基于mpvue的农技平台小程序项目，采用wux-weapp组件库 [文档地址](https://wux-weapp.github.io/wux-weapp-docs/#/introduce)

## Setup

mpvue环境安装

``` bash
# 命令行到达项目目录
cd 对应目录

# 安装依赖
删除node_modules
npm install

# 开发时构建
npm run dev

#预览
打开微信开发者工具

```

## 目录说明

重点：src中
Page:
    index: 主页
    login: 用户/专家登录页
    classification: 用户/专家分类详情页
    myQuestions:用户提问页
    myAnswers: 专家回答页
    personalPage: 用户/专家个人主页
    questionAsk: 提问编辑页
    questionChat: 问题专家用户互动页
components:
    存放重复利用的vue组件
utils:
    存放重复使用的工具函数
app.json:全局配置文件，同微信小程序中的全局配置文件，需要引用组件库请更新这里的usingComponents
App.vue:生命周期函数可更新在这
main.js:

