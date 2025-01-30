
<h1 align=center>Diary of OtsuRed</h1>

#1 当我在远程仓库（如 GitHub 网站）上直接修改了仓库的代码，并且 push 了，过了段时间又在本地修改了工作，在本地 push 的时候提示 rejected failed to push some refs to ... 。这是因为远程仓库包含了本地没有的工作，这种情况常发生在协作中另一个仓库 push 了的时候。这时可以先 git pull 将远程仓库上的改动同步到本地仓库，然后再 push 我的 commit 。
