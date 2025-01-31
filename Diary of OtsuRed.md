
<h1 align=center>Diary of OtsuRed</h1>

#1 *2025/1/30* 当我在远程仓库（如 GitHub 网站）上直接修改了仓库的代码，并且 push 了，过了段时间又在本地修改了工作，在本地 push 的时候提示 rejected failed to push some refs to ... 。这是因为远程仓库包含了本地没有的工作，这种情况常发生在协作中另一个仓库 push 了的时候。这时可以先 git pull 将远程仓库上的改动同步到本地仓库，然后再 push 我的 commit 。

#2 GitHub 上的 md 文件嵌入的 CSS 代码貌似不能正常渲染。。。

#3 CLion 上的文件名变红是因为安装了版本控制工具（例如 git ， SVN 等），更新了代码没有 commit ，起提示作用，不影响实际功能。我 commit 以后，这些文件名就变成绿色的了。第一次以后，在 CLion 上修改文件会使文件名变蓝， add 以后还是蓝色的， commit 以后变成白色。

#4 *2025/1/31* 在 URL 上输入正斜杠好像就已经发送了请求，而不用回车键，好像是这样。
