# git branch 怎麼用

`git branch` 是 Git 中用來**管理與切換分支**的核心指令。分支可以讓你從主程式碼庫分流出來，獨立開發新功能或修復 Bug，而不影響主要程式碼。

以下是常見的使用情境與常用指令整理：

---

### 1. 檢視分支

* **查看本地所有分支**：
```bash
git branch

```


*(畫面上開頭有 `*` 號且呈綠色的分支，代表你當前所在的分支)*
* **查看包含遠端（Remote）的所有分支**：
```bash
git branch -a

```


* **查看各分支最後一次的 Commit 訊息**：
```bash
git branch -v

```



---

### 2. 新增與切換分支

* **新建分支**（但仍在原本的分支）：
```bash
git branch <分支名稱>

```


*範例：`git branch feature-login*`
* **切換到指定分支**：
```bash
git checkout <分支名稱>
# 或使用較新的指令：
git switch <分支名稱>

```


* **【常用小捷徑】新建並直接切換過去**：
```bash
git checkout -b <分支名稱>
# 或使用較新的指令：
git switch -c <分支名稱>

```



---

### 3. 修改與刪除分支

* **重新命名當前分支**：
```bash
git branch -m <新分支名稱>

```


* **刪除已合併的分支**（一般安全刪除）：
```bash
git branch -d <分支名稱>

```


* **強制刪除分支**（即使該分支有未合併的修改）：
```bash
git branch -D <分支名稱>

```



---

### 4. 基本工作流程示範

假設你要開發一個「登入頁面」功能：

1. **建立並切換至新分支**：
```bash
git checkout -b feature-login

```


2. **在這個分支上修改程式碼，並進行 commit**：
```bash
git add .
git commit -m "完成登入頁面 UI"

```


3. **完成後，切換回主分支（例如 `main` 或 `master`）**：
```bash
git checkout main

```


4. **將新功能分支合併進主分支**：
```bash
git merge feature-login

```


5. **合併完成後，刪除已不再需要的新功能分支**：
```bash
git branch -d feature-login

```

# git checkout -b和branch有甚麼關係

`git checkout -b` 和 `git branch` 的關係非常直接：**`git checkout -b` 其實就是將建立分支與切換分支這兩步操作，合編成一個快捷指令。**

---

### 指令對照表

| 操作需求 | 方法 A：分開執行 | 方法 B：快捷指令 |
| --- | --- | --- |
| **1. 建立新分支** | `git branch <分支名稱>` | `git checkout -b <分支名稱>` |
| **2. 切換到新分支** | `git checkout <分支名稱>` | *(自動完成)* |

* `git branch <分支名稱>` 只會**建立分支**，但你依然停留在原本的分支上。
* `git checkout -b <分支名稱>` 會**建立分支，並立刻切換過去**。

---

### 補充：現代 Git 的新語法

在較新的 Git 版本中，官方推薦使用語意更明確的 `git switch`：

* **傳統寫法**：`git checkout -b <分支名稱>`
* **現代寫法**：`git switch -c <分支名稱>`（`-c` 代表 create）

這兩種寫法效果完全一致，都是「建立並切換」的意思。