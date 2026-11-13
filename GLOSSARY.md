# GLOSSARY

本仓库的领域术语。**新增概念先查这里**；不在表里且影响设计的，加进来，不要就地发明。

| 术语 | 含义 | _Avoid_ |
|---|---|---|
| **标注** | 一条用户记录的意见，含目标元素、可选的尺寸/位置变化、以及用户写的文字。一条标注最终变成输入框里的一段 markdown。 | 批注、comment、note、feedback |
| **条目** | 标注在列表里的单条记录（发送前的中间态）。一次会话可以攒多条条目，一次性发给模型。 | item、entry、mark |
| **标注器** | 浮在目标页面上的那层 UI：读取元素、拖手柄、写说明。它不进入页面 DOM 的业务结构，只叠加自己的 overlay。 | annotator、overlay、toolbar |
| **目标页** | 用户点扩展图标时所在的那个标签页，也就是批注对象。 | target page、被标注页 |
| **宿主页** | dsh 自己的页面（`http://127.0.0.1:3081`）。它接收条目并写进输入框。 | host page、dsh 页 |
| **注入** | 扩展把内容脚本加载进某个页面。目标页靠 `activeTab` 用户手势触发，宿主页靠 manifest 的 `matches` 常驻。 | injection、挂载 |
| **草稿** | dsh 输入框里的待发文本。扩展只往草稿里追加，从不直接发送。 | draft、draftText、prompt |
| **填充** | 把条目序列化成 markdown 并写进草稿的动作。实现用 `document.execCommand('insertText')`（已验证在 ISOLATED world 可用）。 | fill、insert、write |
| **变换** | 用户对目标元素做的尺寸/位置/旋转改动，记成「旧值 → 新值」。 | transform、mutation、change |
| **还原** | 变换预览结束后把元素样式恢复原状。标注器**不留痕迹**。 | revert、undo、restore |
| **吸附** | 拖动或缩放时，元素边缘接近其他元素边缘或容器中线，自动贴过去并画辅助线。 | snap、magnet、guide |
| **手势** | 用户鼠标动作的类别：拖动 / 缩放 / 旋转。第一期做这三类。 | gesture、action、operation |

## 边界说明

- 「标注」是**用户意图**，「条目」是**传输单位**，「草稿」是**落地位置**。三者不要混用。
- 「标注器」是 UI 层的名字，不是插件名。插件叫 **dsh-ui-annotate**。
