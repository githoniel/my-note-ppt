title: Git && GitLab
speaker: githoniel
transition: kontext
files: /js/demo.js

[slide style="background-image:url('/git/git.jpg');background-position:center center"]


[slide style="background-image:url('/git/git2.jpg');background-position:center center"]

# 事实上的 {:&.flexbox.vright}
# 版本控制系统标准
# 更是IM/名片
[slide style="background: #fff"]

<div class="block">
    <div class="mid-pic"></div>
    <div class="title">
        <h1>在软件工程中</h1>
        <h1>没有什么是添加中间层</h1>
        <h1>解决不了的</h1>
    </div>
</div>
<style>
.block {
    display: flex;
    flex-direction: row;
}
.block .title {
    width: 750px;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.block .title h1 {
    font-size: 42px;
    color: #666;
    text-shadow: 2px 2px 2px #999;
}
.mid-pic {
    background: url('/git/midware.png') center center no-repeat;
    background-size: 100%;
    position: relative;
    float: left;
    width: 700px;
    height: 700px;
}
</style>

[slide style="background: #fff"]

<div class="local-pic"></div>
<style>
.local-pic {
    background: url('/git/midware.png') center center no-repeat;
    background-size: 100%;
    width: 800px;
    height: 800px;
    margin: 0 auto;
}
</style>

[slide]

# 分布式的优势

- 告别单点故障
- 告别蛋疼的lock/clear问题
- 本地处理commit/branch/differ/blame速度极快
- 只有pull/fetch需要联网
- 提交前整理提交内容，commit信息，随意reset

[slide]

# 真正的必杀 - 强大的分支管理

<div class="commit-pic"></div>
<style>
.commit-pic {
    background: url('/git/commit.png') center center no-repeat;
    background-size: 100%;
    width: 800px;
    height: 800px;
    margin: 0 auto;
}
</style>

[slide]

# Git-Flow

<div class="flow-pic"></div>
<style>
.flow-pic {
    background: url('/git/flow.png') center center no-repeat;
    background-size: 100%;
    width: 800px;
    height: 800px;
    margin: 0 auto;
}
</style>

[slide]

# 命令行固然好，GUI也不可少
<div class="sg-pic"></div>
[操作指南](http://arke.landicorp.com/zh/git-introduction)
<style>
.sg-pic {
    background: url('/git/smartgit.png') center center no-repeat;
    background-size: 100%;
    width: 800px;
    height: 800px;
    margin: 0 auto;
}
</style>

[slide style="background-image:url('/git/gitlab-blog-cover.png');background-position:center center"]

[slide]

# 基本操作

- new Group/Project
- Clone
- Permissions/Members
- Issue
- CI
- Milestone
- Folk/merge

[slide]
# Activity
<div class="end-pic"></div>
<style>
.end-pic {
    background: url('/git/ac.png') center center no-repeat;
    background-size: 100%;
    width: 800px;
    height: 200px;
    margin: 0 auto;
}
</style>





