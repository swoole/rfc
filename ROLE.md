group owner 权限
=====

* 持续 3 年持续向 swoole-src、library 主分支贡献代码，每年有效 commit 次数高于 100
* 近1年内有效 commit 次数低于 10，移除 owner 权限
* 修复拼写错误、优化错误信息语法词法问题不计为有效 commit

swoole-src 仓库
====
* 非 owner 权限账户，不直接向 master 分支提交代码，需要先提交 `pull request` (以下简称`PR`)
* 非 owner 权限账户 `PR` 经过其他 `maintainer` review 同意后并且没有其他 owner 反对的情况下才可以 merge 到 master
* owner 权限账户重大变更也应提交 `PR`，经过其他 `maintainer` review 并且接受后才可以 merge 到 master
* owner 权限账户认为是轻微修改而直接提交到 `master`，其他 `maintainer` 明确提出反对意见，则需要要 `revert commit`，并按照第三条约定重新发起流程


repo admin/maintain/write 权限
=====

* 持续 1 年持续向此仓库主分支贡献代码，commit 次数高于 10 
* 近1年内 commit 次数低于 5，移除 admin/maintain/write 权限

友好合作
====
* 不得恶意提交代码，如：提交存在病毒的代码，恶意覆盖其他人的 `commit` 代码，提交带有色情、暴力、政治敏感、辱骂攻击他人注释的代码 等
* 不对他人进行语言攻击，不得辱骂、伤害其他 `maintainer`
* 存在上述不友好行为的账户应立即移除一切权限
