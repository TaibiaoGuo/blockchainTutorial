# 书籍编写工作流程规范

1. 项目经理根据项目开发计划表划分任务，每一个任务生成一个ISSUE，指定一个编写人员
2. 编写人员在收到任务后，从最新的`main`分支创建任务分支
```bash
git checkout main
git pull
# ISSUE_NUMBER是对应ISSUE的编号
git checkout -b feature-ISSUE_NUMBER
```
3. 在`$PROJECT_ROOT/book/xxx`文件夹中创建独立的任务文件，每一个任务一个文件有利于降低合并冲突。文件名命名规则为`章编号+节编号+ISSUE_NUMBER.md`,例如`070123.md`
> $PROJECT_ROOT 为项目仓库根目录，好让读者明白目录间关系
```bash
# 进入对应文件夹
cd $PROJECT_ROOT/book/07GeneralArchitecture
# Linux下创建文件的命令
touch 070123.md
# 如果有图片，还可以章节目录下的`figures`创建章节对应图片目录。例如在`07GeneralArchitecture`下添加图片目录：
mkdir $PROJECT_ROOT/book/07GeneralArchitecture/figures/070123
```
4. 任务完成后，自己检查无误后，提交任务相关文件至代码服务器
```bash
git add $PROJECT_ROOT/book/07GeneralArchitecture/
# commit 信息中需要包含 #ISSUE_NUMBER 的标记，以让Github关联 commit 和 issue，以进行自动化
git commit -m "完成#ISSUE_NUMBER任务"
git push 
# 如果该分支第一次提交的github，还需要在github创建远程分支，按照git push 的提示操作即可
```
5. 编写人创建分支`feature-ISSUE_NUMBER`新的Pull requests，项目经理及时指定两个Reviewer
6. Reviewer及时Review代码，检查内容质量，给出评论、同意、反对的意见
    1. 若超过两个Reviewer同意，并且没有冲突，则代码可以被合并到主分支
    4. 若Reviewer有异议，或者代码与主分支存在冲突，需分支创建者解决Reviewer提出的问题或解决冲突，然后再次发起Pull requests

