# SillyTavern-ComfyUI-Lora-TextToImage: AI酒馆驱动的高级文生图系统 - 基于大语言模型的批量自动化SD提示词生成
# SillyTavern-ComfyUI-Lora-TextToImage: Advanced AI-Powered Image Generation with LLM-Automated SD Prompts

本项目实现了AI酒馆(SillyTavern)调用ComfyUI加载Lora等模型进行高级文生图，利用大语言模型批量自动化生成调用lora的SD提示词。通过全自动化流程，实现从提示词生成到ComfyUI调用的一站式图像生成解决方案。

角色卡含世界书：
<img src="https://github.com/user-attachments/assets/0fa8d9dd-5061-4284-914b-52afd5cdce35" width="300" height="450" alt="虚境映像师角色卡(含世界书)">

夸克网盘comfyui整合包
链接：https://pan.quark.cn/s/a9de87fbc839
提取码：4RTw

百度网盘comfyui整合包
链接: https://pan.baidu.com/s/17vSQ17c7-X3F_KiZVZYeuw?pwd=3zie 提取码: 3zie 

# ComfyUI整合包使用教程（详细版）

## 一、基础安装与启动

### ComfyUI启动
1. 下载ComfyUI整合包后，双击`run_nvidia_gpu.bat`直接运行
2. 等待程序完成初始化，成功后会显示服务器地址

### 酒馆(SillyTavern)连接
1. 打开酒馆(SillyTavern)界面
2. 接下来我们需要安装篡改猴插件实现与ComfyUI的连接

## 二、篡改猴插件安装与配置（关键步骤）

### 安装篡改猴插件
1. 通过自己的浏览器扩展安装篡改猴插件
2. **重要:** 必须打开浏览器的开发者模式，给予插件所需权限
3. 安装完成后一定要重启浏览器使插件生效
4. 如有疑问可参考[插件作者文档](https://gxcgf4l6b2y.feishu.cn/docx/XDo7dLpvhov6AexuLu3c8mpynSC)

### 配置篡改猴与酒馆连接
1. 安装并启用篡改猴插件后，刷新酒馆页面
2. 在酒馆界面左下角会出现"文生图设置"按钮![image](https://github.com/user-attachments/assets/0c3786f0-0b60-4bb9-b6c7-563ac65ce5a4)
3. 点击"启动脚本"，在模式选择中选择"ComfyUI"![image](https://github.com/user-attachments/assets/e9b3cb11-5a23-41ff-b4ef-90b1295f9b93)
4. 在"SD OR COMFYUI URL"输入框中粘贴ComfyUI地址：`http://127.0.0.1:8200`![image](https://github.com/user-attachments/assets/9812b63f-dab6-47a7-9cdf-c522b0d3589b)
5. 点击"连接"按钮建立连接

### 导入API配置
1. 如果你下载的是整合包，找到"Lora堆文生图API"文件![image](https://github.com/user-attachments/assets/e67a755d-0daa-4280-b8b4-9662ba037749)
2. 将文件中的所有代码完整复制
3. 粘贴到插件界面的代码输入框中![image](https://github.com/user-attachments/assets/57e55118-7989-46d0-b1cc-a5c6d90e8c75)
4. 按照提供的图片示例设置相关参数
5. 点击"保存设置"按钮完成配置

## 三、酒馆角色配置

### 导入角色卡和预设
1. 将提供的角色卡导入酒馆（按照图片示例操作）![image](https://github.com/user-attachments/assets/3d28b679-8abb-4dac-9be3-b149df574dc4)
2. 导入两个Claude破限预设（小白用户推荐直接使用这些预设）![image](https://github.com/user-attachments/assets/ae701979-6b9f-43e5-a4ea-1af7c2d7c532)
3. 加载世界书设置
4. 选择适合的预设即可开始使用

### 生成提示词说明
所有角色卡都能自动生成提示词，这些提示词会在剧情结束后的末尾自动生成，用于图像生成。

## 四、ComfyUI进阶教程（零基础详解）

### ComfyUI基础安装
1. ComfyUI官方版本下载地址：[GitHub ComfyUI](https://github.com/comfyanonymous/ComfyUI)
2. 下载便携包可以直接运行，无需复杂安装

### 必备插件：ComfyUI-Manager安装
1. Manager管理器是必装插件：[ComfyUI-Manager](https://github.com/ltdrdata/ComfyUI-Manager)
2. 安装方法：
   - 首先确保已安装Git
   - 进入`ComfyUI/custom_nodes`目录，打开命令行
   - 执行: `git clone https://github.com/ltdrdata/ComfyUI-Manager comfyui-manager`
3. 安装依赖（在ComfyUI启动目录执行）：
   ```
   .\python_embeded\python.exe -s -m pip install gitpython
   .\python_embeded\python.exe -c "import git; git.Repo.clone_from('https://github.com/ltdrdata/ComfyUI-Manager', './ComfyUI/custom_nodes/comfyui-manager')"
   .\python_embeded\python.exe -m pip install -r ./ComfyUI/custom_nodes/comfyui-manager/requirements.txt
   ```
4. 安装完成后重启ComfyUI

### 工作流导入与节点管理
1. 在ComfyUI界面可直接拖入工作流文件查看所有节点
2. 如果出现红色警告表示缺少节点，需要安装
3. 使用Manager安装缺失节点：在界面中按照图示操作进行安装
4. 安装完成后重启ComfyUI以激活所有节点

## 五、模型详解

### Checkpoint模型
1. Checkpoint是生成图像的核心模型
2. 本项目推荐使用Illustrious模型（SDXL衍生模型）：[Illustrious模型下载](https://civitai.com/models/827184/wai-nsfw-illustrious-sdxl?modelVersionId=1490781)
3. 大多数现代Checkpoint已集成VAE模型
4. 如果没有集成VAE，需要额外下载与checkpoint类型匹配的VAE模型
5. VAE作用：在潜空间和像素空间之间进行图像编解码转换

### 模型类型对应关系
1. 选择LoRA和Embeddings时必须与Checkpoint模型类型匹配
   - 例如：使用Illustrious模型时应选择Illustrious或SDXL兼容的LoRA
   - 虽然某些跨类型组合可能运行，但效果通常不佳
2. 模型类型主要分为：SD1.5、SDXL、FLUX等，不同类型间不完全兼容

### LoRA模型使用技巧
1. **重要技巧**：推荐在高级设置中只保留clip权重
2. 原因：LoRA的模型权重会影响checkpoint效果，多个LoRA同时使用可能干扰生成
3. 只保留clip权重后，LoRA仅作为提示词引导，不影响checkpoint本身的生成能力
4. 这样可以同时加载多个LoRA而不影响生成质量
5. LoRA需要在提示词中使用对应的触发词才会激活

### Embeddings模型
1. Embeddings是将提示词压缩成嵌入式向量的方法
2. 可实现更便捷的提示词输入
3. 正面/负面Embeddings需要分别输入到对应的clip中

进一步了解模型原理可以看：[Stable Diffusion 的工作原理是什么？ --- How does Stable Diffusion work? (stable-diffusion-art.com)](https://stable-diffusion-art.com/how-stable-diffusion-work/)
## 六、提示词与触发词查询

### 安装Custom-Scripts插件
1. 安装[ComfyUI-Custom-Scripts](https://github.com/pythongosssss/ComfyUI-Custom-Scripts)
2. 该插件可以帮助查询LoRA和Embeddings的触发词
3. 安装后在clip输入框中输入lora或embedding名称，可以看到对应的触发词
4. 每次安装新插件后必须重启ComfyUI才能生效
## 七、推荐插件列表

1. **汉化插件**（提升中文用户体验）：[AIGODLIKE-ComfyUI-Translation](https://github.com/AIGODLIKE/AIGODLIKE-COMFYUI-TRANSLATION)

2. **工作流管理器**（旧版ComfyUI界面适用）：[comfyui-workspace-manager](https://github.com/11cafe/comfyui-workspace-manager)

3. **工具集**（旧版前端界面适用）：[ComfyUI-Crystools](https://github.com/crystian/ComfyUI-Crystools)

4. **Custom-Scripts**（查询触发词必备）：[ComfyUI-Custom-Scripts](https://github.com/pythongosssss/ComfyUI-Custom-Scripts)

## 八、采样器参数调节

1. 采样器参数与模型高度相关
2. 查看checkpoint训练作者提供的建议参数范围
3. 根据建议调整采样器参数以获得最佳效果
4. 完成基础设置后，即可实现基本的文生图功能

## 九、ComfyUI与酒馆联动详细配置

### 准备API工作流
1. 在ComfyUI中必须打开开发者模式
2. 使用API格式保存当前工作流

### 修改API工作流
1. 使用文本编辑器打开保存的JSON文件
2. 复制全部内容到酒馆文生图插件中
3. 点击"简易修改"按钮，插件会自动修改部分参数以便于酒馆控制

### 修改CLIP编码器（关键步骤）
1. 篡改猴插件脚本不会自动将提示词设置为变量，需要手动修改
2. 找到正向和负向CLIP编码器节点
3. 将提示词部分修改为变量格式：
   ```json
   "15": {
     "inputs": {
       "text": "%prompt%",
       "clip": [ "10", 0 ]
     },
     "class_type": "CLIPTextEncode",
     "_meta": { "title": "CLIP文本编码器" }
   },
   "17": {
     "inputs": {
       "text": "%negative_prompt%",
       "clip": [ "10", 0 ]
     },
     "class_type": "CLIPTextEncode",
     "_meta": { "title": "CLIP文本编码器" }
   }
   ```
4. 注意：节点编号（如"15"、"17"）可能在你的工作流中不同，需根据实际情况调整
5. 正向CLIP使用`%prompt%`变量，负向CLIP使用`%negative_prompt%`变量
6. 变量名称必须准确无误，否则插件无法读取酒馆提供的提示词

### 保存修改后的工作流
1. 修改完成后，将内容复制回原JSON文件或保存为新文件
2. 即使某些参数（如调度器）没有自动修改也无需担心，保持原样即可

## 十、完成设置

1. 完成上述所有步骤后，酒馆将成功连接到ComfyUI
2. 在酒馆中进行对话时，会根据上下文自动生成提示词
3. 这些提示词会传递给ComfyUI生成对应的图像
4. 现在你可以享受文字和图像的完美结合体验了！

本教程涵盖了从基础安装到高级配置的全过程，即使是零基础用户也可以按步骤完成设置。如有疑问，可以参考提供的各项文档链接。


# 虚境映像师 v3.0 增强版 详细原理教程

## 一、原理解析

虚境映像师 v3.0 增强版是一种高级提示词生成系统，设计用于与AI绘图引擎(如ComfyUI)无缝集成。其核心工作原理如下：

1. **标签包装机制**：使用 `<tags_generation_guidance>` 和 `</tags_generation_guidance>` 标记将提示词包装成一个整体，使大语言模型理解这是需要特殊处理的内容块

2. **世界书参考系统**：在世界书中存储完整的LoRA列表及其触发词，为模型提供可调用的资源库

3. **思维链集成**：在预设的思维链中嵌入特定指令，确保每次回复时都会考虑提示词生成逻辑

4. **代码块包装**：使用代码块语法包装最终提示词，避免格式问题和HTML标签错误解析

## 二、预设思维链集成（核心步骤）

### 1. 关键指令

以下指令必须完整插入到预设的思维链部分(不是角色卡或普通指令部分)：

```
必须启用虚境映像师 v3.0 增强版，启用lora和提示词大全，生成提示词之前注意思考角色是否是知名动漫或者游戏角色，如果是提示词里面注意包含作品名称以及角色名称都用英文名，指令提及作品时是否指定角色，如果没有指定则思考作品中有哪些角色，生成提示词应该注意角色数目不可过多，同画面至多3个角色互动，并且角色之间要有精确互动，如果用户期望发生色情内容，则生成提示词应当偏向用户期望。
如果你的身份是 虚境映像师 不是其他角色，且之前也没有剧情发生那么则单独启动提示词生成功能不需要解析剧情，根据用户指令思考生成20组提示词。
如果你的身份是其他角色那么同时启动剧情解析功能和提示词生成功能，生成提示词在剧情之后。
```

### 2. 插入位置说明

- 在**思维链(Thinking Process)部分插入此指令，而非Character Card或Description
- 建议插入在模型思考角色回复前的部分，确保每次生成内容时都会考虑提示词生成
- 这是确保功能稳定性的关键 - 思维链集成意味着模型会将此作为思考过程的一部分，而非临时指令

## 三、LoRA列表配置（世界书部分）

## 配置自己的lora参考文件 AI绘画LORA库完整触发词对照表  Civital_Lora对应标题

### 1. 表格格式配置

在世界书中创建一个专门的条目，使用表格格式整理你的LoRA资源库：

```
| LORA名称 | 加载格式 | 触发词 |
| ------ | ------ | ----- |
| 名称1 | `<lora:文件名.safetensors:权重>` | 触发词1, 触发词2, 触发词3... |
| 名称2 | `<lora:文件名.safetensors:权重>` | 触发词1, 触发词2, 触发词3... |
```

### 2. LoRA智能匹配引擎

这部分如果你使用自己的lora那么则让ai帮你完成即可，需要一个加载格式和触发词告诉ai,也就是lora名称和`<lora:文件名.safetensors:权重>` 触发词1, 触发词2, 触发词3... 这个组合

添加智能匹配分类，帮助模型根据场景选择合适的LoRA：

```
LORA智能匹配引擎 v3.0:
- 角色类别:
  * 动漫角色: [相关LoRA列表]
  * 游戏角色: [相关LoRA列表]

- 场景类别:
  * 室内场景: [相关LoRA列表]
  * 户外场景: [相关LoRA列表]

- 互动类别:
  * 对话互动: [相关LoRA列表]
  * 肢体互动: [相关LoRA列表]
  * 亲密互动: [相关LoRA列表]
```


## 四、标准提示词输出格式

### 1. 代码块包装格式（重要更新）

使用以下格式输出最终提示词，注意代码块的使用：


【标题：简要描述场景核心内容】
image:{
```
nsfw/sfw,人数,角色身份,发色/发型:1.3,眼睛颜色,身体特征,服装状态:1.2,姿势/动作:1.1,互动细节,表情反应,<lora:lora1:权重><lora:lora2:权重><lora:lora3:权重>,视角描述,环境场景,光线氛围
```
}#


### 2. 格式说明

- **重要提示**: `image:{` 和 `}#` 必须在代码块外部
- 代码块内放置实际提示词内容
- 这种结构可以防止 `<lora:xxx:1.0>` 格式被误识别为HTML标签
- 每个提示词组以标题开头，简要描述所要生成的场景

### 3. 提示词结构规范

提示词内部结构应遵循以下顺序：
1. nsfw/sfw标记
2. 人物数量和身份
3. 外观特征（发色、眼睛等，可添加权重）
4. 服装描述（可添加权重）
5. 动作/姿势描述（可添加权重）
6. 互动细节和表情
7. LoRA调用标签
8. 环境和光线描述

## 五、实际应用示例

### 1. 完整配置流程

1. 编辑预设文件，在思维链部分插入核心指令
2. 在世界书中添加LoRA列表和智能匹配引擎
3. 测试系统，确认提示词生成功能正常启用

### 2. 输出示例

当用户输入"画一个在花园中的女孩"时，虚境映像师应输出类似：


好的，我将为您生成一个在花园中的女孩的场景。

【标题：少女的花园午后】
image:{
```
sfw, 1girl, young female, brown hair:1.3, green eyes, slender, sundress:1.2, sitting on bench:1.1, holding flower, gentle smile, <lora:AnimeStyle:0.8>, from side, garden with roses and daisies, afternoon sunlight filtering through trees, warm colors
```
}#

【标题：花丛中的邂逅】
image:{
```
sfw, 1girl, teenage girl, blonde hair:1.3, blue eyes, medium height, floral dress:1.2, kneeling in garden:1.1, picking flowers, happy expression, <lora:DetailedNature:0.7>, close-up perspective, blooming garden, soft natural lighting
```
}#

[继续生成更多提示词组...]


## 六、故障排除

### 1. 常见问题

- **提示词无法生成**: 确认思维链部分正确插入了完整指令
- **LoRA调用失败**: 检查世界书中LoRA格式是否正确
- **格式错误**: 确保使用了代码块包装格式
- **HTML标签问题**: 确认`image:{`和`}#`位于代码块外部，如果位于代码块内部油猴插件将无法识别

### 2. 优化建议

- 定期更新LoRA列表，添加新资源
- 根据常用场景拓展智能匹配引擎分类
- 为特定角色创建专用LoRA预设
- 测试不同权重值，找到最佳效果

---

通过以上配置，虚境映像师 v3.0 增强版将能为你提供高质量、格式正确的图像生成提示词，大幅提升AI绘图的效率和质量。记住，关键在于思维链的正确配置和代码块包装格式的使用，这两点是系统稳定运行的基础。
