
maintainer
====
* 持续 `1` 年向 `swoole group` 任意仓库贡献代码，并且有效 `commit` 次数高于 `10`，可以获得该仓库或对应 `team` 的 `admin/maintain/write` 操作权限 (以下简称`maintainer`权限)
* 近 `1` 年内有效 `commit` 次数低于 `5`，移除 `maintainer` 权限

> 修复拼写错误、优化错误信息、修复语法词法问题不计为有效 `commit`

owner
=====

* 持续 `3` 年持续向 `swoole-src`、`library` 两个核心仓库主分支贡献代码，每年有效 `commit` 次数高于 `100` 可以获得 `owner` 权限
* 近 `1` 年内有效 `commit` 次数低于 10，移除 owner 权限
* 当 `members` 中只有最后一个 `owner` 时，该 `owner` 自动成为看守者，直到有新的 `maintainer` 通过条件 `1` 成为新的 `owner`


swoole-src 仓库
====
* 非 owner 权限账户，不直接向 master 分支提交代码，需要先提交 `pull request` (以下简称`PR`)
* 非 owner 权限账户 `PR` 经过其他 `maintainer` `review` 并同意后并且没有其他 `owner` 明确反对的情况下才可以 `merge` 到 `master`
* owner 权限账户重大变更必须提交 `PR`，经过其他 `maintainer` `review` 并且接受后才可以 merge 到 `master`
* owner 权限账户认为是轻微修改而直接提交到 `master`，其他 `maintainer` 明确提出反对意见，则需要要 `revert commit`，并按照第三条约定重新发起流程
* 若 `PR` 在超过 `3` 天以上时间没有其他 `maintainer`，发起者可以将此 `PR` 自行合并到 `master`


友好合作
====
* 不得恶意提交代码，如：提交存在病毒的代码，恶意覆盖其他人的 `commit` 代码，提交带有色情、暴力、政治敏感、辱骂攻击他人注释的代码 等
* 不对他人进行语言攻击，不得辱骂、伤害其他 `member` 
* 违反友好合作条款的账户应立即移除一切权限，并从 `swoole group members` 中移除
