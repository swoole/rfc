
English
====

Maintainer
----
* Continuously provides code to any base in swoole group for 1 year and its effective higher than 10 commit times, and can obtain the access to `admin/maintain/write` from the repo or its opposite team.
* within 1 year effective commit times are lower than 5, remove access to maintainer.

> Fix typo, fix grammar and wrong words, optimize error message, all above are not seen as effectual commit.  
> Add account to swoole group members as soon as get the access to maintainer

Owner
----
* Obtained maintainer permission, meanwhile offer code for 3 years to these two core warehouse branches from swoole-src, library and annual effective commit times are higher than 100; then you become the owner.
* Within 1 year effective commit times lower than 10, cancel the owner permission and downgrade to maintainer.
* When group members only have 1 owner, the owner automatically becomes guard, not close the access until new maintainer upgrade to new owner

The swoole-src repository
-----
* Non-owner access account ,not directly submit code to branches of master, firstly provide pull request.(here in after referred to as PR)
* The `PR` couldn't merge to master until other maintainers review and agree, meanwhile, other owners obviously disagree.
* Big changes in owner's access account, must submit PR; not merge to master until other maintainer review and accept.
* Tiny changes in owner's access account, can directly submit to master, however other maintainers obviously make averse opinions, need to `revert commit` and  restart a new process.
* If PR is not reviewed by other maintainers beyond 3 days, then the operator self merge to master.

Friendly cooperation
----



中文
====

maintainer
-----
* 持续 `1` 年向 `swoole group` 任意仓库贡献代码，并且有效 `commit` 次数高于 `10`，可以获得该仓库或对应 `team` 的 `admin/maintain/write` 操作权限 (以下简称 `maintainer` )
* 近 `1` 年内有效 `commit` 次数低于 `5`，移除 `maintainer` 权限

> 修复拼写错误、优化错误信息、修复语法词法问题不计为有效 `commit`  
> 获得 `maintainer` 权限后会将此账户添加到 `swoole group members`  

owner
-----

* 拥有 `maintainer` 权限，并且持续 `3` 年向 `swoole-src`、`library` 两个核心仓库主分支贡献代码，每年有效 `commit` 次数高于 `100` 可以获得 `owner` 权限
* 近 `1` 年内有效 `commit` 次数低于 `10`，移除 `owner` 权限，降级为 `maintainer` 权限
* 当 `members` 中只有最后一个 `owner` 时，该 `owner` 自动成为看守者，不移除 `owner` 权限，直到有新的 `maintainer` 符合条件 `1` 成为新的 `owner`

swoole-src 仓库
-----
* 非 `owner` 权限账户，不直接向 master 分支提交代码，需要先提交 `pull request` (以下简称`PR`)
* 非 `owner` 权限账户 `PR` 经过其他 `maintainer` `review` 并同意后并且没有其他 `owner` 明确反对的情况下才可以 `merge` 到 `master`
* `owner` 权限账户重大变更必须提交 `PR`，经过其他 `maintainer` `review` 并且接受后才可以 merge 到 `master`
* `owner` 权限账户认为是轻微修改而直接提交到 `master`，其他 `maintainer` 明确提出反对意见，则需要要 `revert commit`，并按照第三条约定重新发起流程
* 若 `PR` 在超过 `3` 天以上时间没有其他 `maintainer` 进行 `review`，发起者可以将此 `PR` 自行合并到 `master`


友好合作
-----
* 不得恶意提交代码，如：提交存在病毒的代码，恶意覆盖其他人的 `commit` 代码，提交带有色情、暴力、政治敏感、辱骂攻击他人注释的代码 等
* 不对他人进行语言攻击，不得辱骂、伤害其他 `member` 
* 违反友好合作条款的账户应立即移除一切权限，并从 `swoole group members` 中移除
