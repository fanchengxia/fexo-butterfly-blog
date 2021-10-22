---
title: vsCode自定义代码块
abbrlink: 1
---
# vscode自定义代码块
## 1.打开用户代码片段
文件 -》首选项 -》用户片段   **或者**   左下角齿轮设置 -》 用户代码片段
## 2.选择 新建全局代码片段文件

![新建全局代码片段文件](../../../img/vscode-code-1.png)
<!-- {%asset_img 图片名称.jpg examplename%} -->

## 3.输入代码段文件名，例如：vue.json 点击回车
## 4.输入代码片段
如下：直接全选复制粘贴
prefix是指：快捷键提示名
```
{
	"demo": {
		"prefix": "vue",
		"body": [
			"<template>",
			" <div class=\"$1\">",
			" ",
			" </div>",
			"</template>",
			" ",
			"<script>",
			"export default {",
			" data () {",
			" return {",
			" }",
			" }",
			"}",
			"</script>",
			" ",
			"<style scoped lang = \"less\">",
			" ",
			"</style>"
		],
		"description": ""
	}
}
```
## 5. 直接输入vue则出现提示
![输入vue](../../../img/vscode-code-2.png)
![双击展示结果](../../../img/vscode-code-3.png)



