# ADR-0002：写进草稿，不直接发送消息

- **Status**: accepted
- **Date**: 2026-11-13

## 背景

既有的 `dsh-annotated-browser` 选择直接发消息（`conversation.send(text)` 或 `session.prompt([...], 'queue')`）。那样用户没有机会改措辞、加附件、或者把多条标注合成一次请求。

用户的原始表述是「批注要能落进 dsh 的**输入框**」，不是「直接发出去」。

## 决定

条目只写进**草稿**，用户自己按发送。第一期用 `document.execCommand('insertText', false, text)` 追加；

- 实测可用，且在 content script 的 **ISOLATED world** 里也成功（`world: isolated / execok: true`）。
- 草稿会**持久化**（刷新后还在），用户不会丢内容。
- `InputActions.insertText` 有 revision 守卫（`span.draftRev !== this.rev` 返回 false）和 phase 门（非 `plain` 时拒写），而且它只对**当前会话**有效——扩展知道的是标签页，不一定知道会话。绕开它更稳。

## 后果

- 不能自动发送，也不会抢焦点或替用户按回车。
- 草稿是**异步**更新的：写完立刻读 `innerText` 是空。判据必须等一次渲染。
- `document.execCommand('delete')` 在这套 Lexical 编辑器里**不生效**，清空要用真实按键事件。
