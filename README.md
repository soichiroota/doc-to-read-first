# doc-to-read-first

## Issueの管理方法

1. 実装要件の提案を行う際には、必ずIssuesに新しいIssueを作成する
1. Issueの説明は最初のコメント欄に実装内容の詳細のみを簡潔に記述し、メンションや長いログなどは含めないようにする
1. Issueを作成したあとにコメント欄で、バグの原因や取り組む仕様の詳細について議論する
1. 十分に議論が進んだら、その要件の責任者が採用の可否を決定し、Assigneeを決定し、対象のIssueを参照してPull Requestを作成した後に開発を始めるかIssueをCloseする

注：開発が完了したIssueはCloseすること

## 開発の進め方

### はじめに

コミュニケーションの主体はオンライン上でのものとなります。1回1回のコミュニケーションコストを下げるためにも、コミットメッセージやIssue・PullRequest内のコメントは誤解のないようにローコンテキストを心がけた形でお願いします。

### ブランチの管理方法

- 開発者間で開発途中のブランチもスムーズに委譲できるよう、レポジトリのforkは作成せず、メインレポジトリに直接各々の開発用ブランチを作成する形で開発を行います。

- 新しい機能の開発やバグ修正など、何かしらのコミットを行う際には必ずその際のdevelopブランチから自分の作業用ブランチを作成し、ブランチのマージは必ずPullRequestによって行います。

### PullRequestの管理方法

#### 1. WIP(work in progress) Pull Requestの作成

まず、ブランチは原則Issueと一対一対応とし、ブランチ名は`issue-#X`としてください（`X`は対応するIssue番号で読み替えます）。

ブランチを切ってコミットを始めたら、まずWIPのPull Requestを作成します。 WIPのPull Requestはまだレビューの必要のない作業中のPull Requestで、現在の作業の進捗状況をdiffベースで共有するために作成します。

WIPのPull Requestではタイトルの先頭に"WIP: "と付け、変更内容に関連するIssue(必ずAssigneeを自分に設定すること)を紐付けた上で、実装する内容などを書くようにしてください。

#### 2. 機能の作成

WIPのPull Requestを作成したら、そのブランチに対して普通に変更をコミット・プッシュしていきます。

コミットは大きくなり過ぎないように意味単位でまとめ、後でコミットログを見る人にとって有意義なコミットメッセージを書くよう心がけてください。

コミットメッセージは下記のフォーマット（[Angularから拝借](https://github.com/angular/angular/blob/main/CONTRIBUTING.md#commit)）に従って書いてください。

```
<type>: <summary>
  │            │
  │            └─⫸ Summary in present tense. Not capitalized. No period at the end.
  │       
  │
  └─⫸ Commit Type: build|ci|docs|feat|fix|perf|refactor|test
```

##### Type

Must be one of the following:

* **build**: Changes that affect the build system or external dependencies (example scopes: gulp, broccoli, npm)
* **ci**: Changes to our CI configuration files and scripts (examples: CircleCi, SauceLabs)
* **docs**: Documentation only changes
* **feat**: A new feature
* **fix**: A bug fix
* **perf**: A code change that improves performance
* **refactor**: A code change that neither fixes a bug nor adds a feature
* **test**: Adding missing tests or correcting existing tests

#### 3. レビューの要請

予定していた実装が終わったら、他の開発者をメンションしてレビューの要請を行ってください。

レビューを要請する段階になったら、タイトルの"WIP: "を外します。

他の開発者をメンションするコメントでは、特に注意してレビューして欲しい点を解説するなど、コミュニケーションの回数が少なくなるように工夫してください。

#### 4. レビューの反映・マージ

レビューコメントをもらったら、基本的には1レビューに付き1コミットを作成し、コメントでどのコミットによって対応したかを明示してください。

すべての修正が完了したら、レビューをくれた人に再度のレビューを要請します。

最終的にレビュアーが問題無しと判断したら対象branchへのマージをします。
