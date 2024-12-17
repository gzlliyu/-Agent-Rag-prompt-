# 目的

笔者开发了一年半的大模型项目（LLM、Agent、vectorDB、Rag、prompt、langchain、langgraph、llamaindex等），期间发现了很多有用且有意思的小技巧，但是当我想分享发现的喜悦时，周围同事朋友都没有做大模型相关的，很是无奈，遂编写本项目。
会持续更新，也希望和代码前的你一起分享。

## 目录

- [prompt 技巧](#prompt 技巧)
- [langchain 技巧](#langchain 技巧)

## prompt技巧

```bash
1、当写好prompt后，AI没有按照既定的Workflow回复，可以尝试让AI说出来他的思考过程。
例如：
- 原prompt："请扮演医助导诊，第一步询问患者症状、第二步询问患者年龄，第三部询问患者既往病史，第四部导诊到科室，回复内容为json格式，包含科室名称department、回复患者内容content"
- 出现问题：AI没有按照既定的顺序回复，会偶尔忘记某步骤
- 解决方法：在prompt中添加一个解释字段，让AI说出来他的思考过程
- 修改prompt："请扮演医助导诊，第一步询问患者症状、第二步询问患者年龄，第三部询问患者既往病史，第四部导诊到科室，回复内容为json格式，包含你的思考过程desc、科室名称department、回复患者内容content"
心得：笔者之前尝试了各种方法，如在prompt中加入条件Constrains，Workflow中加入设定或者提示，效果都不好，但是当加入desc返回字段时，AI的回复效果极好。AI有不吐不快的小毛病，在让AI回复你想要的结果前，先给AI一个机会让他说下自己的想法。