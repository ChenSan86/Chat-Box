# AI-ChatBox
---
## 项目介绍
这是一个基于Web Components技术构建的AI对话界面组件。通过与Moonshot API集成，组件可快速部署个性化AI助手，支持动态对话管理、多主题适配和实时流式响应。核心目标是为开发者提供开箱即用的智能对话解决方案

<details>
  <summary>目录</summary>
  <ol>
    <li>
      <ul>
        <li><a href="#构建工具">构建工具</a></li>
      </ul>
    </li>
    <li>
      <a href="#开始">开始</a>
      <ul>
        <li><a href="#密钥设置">密钥设置</a></li>
      </ul>
    </li>
    <li><a href="#标签属性">标签属性</a></li>
    <li><a href="#许可证">许可证</a></li>
    <li><a href="#参考资料">参考资料</a></li>
    <li><a href="#开发日志">开发日志</a></li>
  </ol>
</details>

### 构建工具
* [Web Components]()

## 开始
部署前阅读

### 密钥设置
在chat box sever中添加密钥，或直接修改代码添加密钥
 ```Javascript
async fetchModelResponse(prompt) {
//=======如果想自定义key，删除下代码块并将this.currentkey设置为自定义key===============        
            try {
              if(!this.currentKey){const keyResponse = await fetch(
                `${this.backendUrl}/api-keys/allocate`,
                {
                  method: "POST",
                  headers: {
                    "Content-Type": "application/json",
                  },
                  body: JSON.stringify({}), // 如果不需要参数可以传空对象
                }
              );
              if (!keyResponse.ok) throw new Error("Failed to allocate key");
              const { key } = await keyResponse.json()；
//==================================================================================
              this.currentKey = key;
            }
            }
        }
  ```

## 标签属性
| 属性            | 类型     | 默认值               | 说明                     |
|-----------------|----------|----------------------|--------------------------|
| backend-url     | String   | http://localhost:3000 | 必填，后端服务地址       |
| initial-prompt  |    -      | {"role":"system","content":""} | 系统级提示设定           |
| history-length  | Number   | 100                  | 对话历史最大轮数         |
| persist-chat    | Boolean  | false                | 是否持久化存储对话       |
| show-timestamp  | Boolean  | true                 | 是否显示时间戳           |
| greeting        | String   | ""                   | 初始化欢迎语             |
| theme           | String   | "light"              | 主题模式（dark/light，默认：light） |


## 许可证

根据 MIT 许可证分发。打开 [LICENSE.md](LICENSE.md) 查看更多内容。

## 参考资料

* [MoonShot AI开放平台 文档](https://platform.moonshot.cn/docs/intro#%E6%96%87%E6%9C%AC%E7%94%9F%E6%88%90%E6%A8%A1%E5%9E%8B)
* [OpenAI Platform](https://platform.openai.com/docs/overview)
* [DeepSeek+Chatbox+Prompt：搭建AI搭档记录](https://zhuanlan.zhihu.com/p/17651541211)
* [Chatbox AI官网：办公学习的AI好助手，全平台AI客户端，官方免费下载](https://chatboxai.app/zh)


## 开发日志

* [ai-chatbox标签的模拟实现-开发日志](https://blog.csdn.net/2401_87362551/article/details/146168935?spm=1001.2014.3001.5502)
