# Git 工作流速查手册

## 铁律

1. 操作前先 `git status`，确认在哪个分支
2. 切分支前必须 commit，否则改动会跟着你跑，文件错乱
3. 开工前先 `git pull`，拉最新代码
4. 一个分支 = 一件事，做完合并就删，不复用旧分支

## 每日工作流程

```bash
# 1. 开工准备
git checkout main             # 回到主线
git pull                      # 拉最新

# 2. 开始新任务
git checkout -b 0324/任务名    # 日期+描述，创建新分支

# 3. 干活，每完成一小步就存档
git add .                     # 所有改动加入暂存
git commit -m "feat: 说明"    # 存档

# 4. 推到 GitHub + 提 PR
git push -u origin 分支名      # 推上去（第一次需要 -u）
# CC 帮你提 PR，或 gh pr create

# 5. 合并后清理
git checkout main
git pull
git branch -d 分支名
```

## commit message 规范

```
feat: 新功能
fix: 修 bug
docs: 改文档
refactor: 重构
```

## .gitignore — Git 的黑名单

放在项目根目录，写进去的东西 Git 永远无视。

### 终端创建

```bash
echo "drafts/" > .gitignore           # 创建并写入（覆盖）
echo ".DS_Store" >> .gitignore        # 追加一行（>> 是追加，> 是覆盖）
cat .gitignore                        # 查看内容，确认写对了
git status                            # 验证：被忽略的文件不会出现
```

### Cursor 创建

```
1. Cursor 打开项目文件夹
2. 右键 → New File → 输入 .gitignore
3. 写入要忽略的内容，每行一个
4. ⌘+S 保存
```

### 常见忽略内容

```
secrets/
drafts/
.DS_Store
node_modules/
.env
```

### 两种"不提交"

- 永远不提交 → 写进 `.gitignore`
- 暂时不提交 → 不写 `.gitignore`，add 时指定文件夹：`git add cases/`

## 分支命名

```
日期/描述
0324/add-login-page
0324/fix-button-bug
0324/wip              # 不确定做什么时用
```

## 终端速查

```
pwd                   # 我在哪
ls                    # 这里有什么
cd ~/repos/xxx        # 去某个地方（绝对路径最保险）
cd ..                 # 返回上一层
mkdir xxx             # 创建文件夹
open .                # Finder 打开当前目录
```

## macOS 快捷键

```
⌘+Space    搜索打开任何应用
⌘+Tab      切换应用
⌘+C/V      复制/粘贴
⌘+Q        退出应用
⌘+W        关闭标签页
Ctrl+C     终端里中断命令
```
