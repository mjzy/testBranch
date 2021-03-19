## Git 查看分支

```bash
/* 查看本地分支 */
git branch
// 实例：
master
* test

/* 查看全部分支-包括远程和本地 */
git branch -a
master
* test
remotes/origin/master
remotes/origin/test
```

以 `remotes` 开头的代表是远程分支

## Git 切换分支

```bash
git checkout branch_name
```

`branch_name` 就是你想切换的分支名称

## Git 新建分支

```bash
/* 创建本地分支 */
git branch new_branch_name

/* 创建远程分支 */
// 1. 创建本地分支
git branch new_branch_name
// 2. 本地分支推送到远程仓库
git push origin new_branch_name
或者
git push origin new_branch_name: rename_new_branch_name
```

`new_branch_name` 就是你想要创建的分支名，比如 `git branch test` 就在本地创建了一个 `test` 分支
远程分支的创建需先在本地建一个分支，再将本地分支推送到远程仓库
`rename_new_branch_name` 表示 “将 `new_branch_name` 推送远程仓库时，重命名的分支名”
例如 `git push origin test:test2`

+ `git branch new_branch_name` 是以当前分支为基础创建的新分支

  ```bash
  假设两个分支，且默认在master分支：
  master
  test
  
  // 0. 以master为基础创建分支dev1
  git branch dev1
  // 1. 进入test分支
  git checkout test
  // 2. 以test为基础创建分支dev2
  git branch dev2
  ```

+ 创建分支后，还需使用命令切换到创建的分支，可以使用组合的命令，创建的同时切换到对应分支

  ```bash
  git checkout -b new_branch_name
  ```

+ 本地分支推送到远程后，本地分支仍存在

  ```bash
  /* 假设远程仓库仅 master 一个分支 */
  // 1. 拉取仓库代码
  git clone https://....
  // 2. 创建一个名为test的本地分支
  git branch test
  // 3. 创建一个test远程分支
  git push origin test
  // 4. 查看分支
  git branch -a
  * master
  test
  remotes/origin/master
  remotes/origin/test
  ```

## Git 删除分支

```bash
/* 删除本地分支 */
git branch -d test

/* 删除远程分支 */
git push origin --delete serverfix
```

## Git合并分支

```bash
/* 本地分支合并 */
// 1. 确定以谁为主体进行合并，切换到对应分支
git checkout master
// 2. 将test分支合并到master分支
git merge test
// 3. 删除test本地分支
git branch -d test

/* 远程分支合并 */
```

