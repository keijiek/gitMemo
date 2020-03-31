# Git Commands

---
## WorkTree で使う

- git status
    - WorkTree傘下のファイルの、登録状態を確認

- **git checkout** **--** *fileName*
    - Work Treeにあるファイルを、直前にコミットした状態(Git directoryの状態)に戻す
    - ファイル新規作成時やファイル名変更時の後など、思った通りの挙動にならない状況もある

- **git init**
    - WorkTreeのディレクトリで実行すると、そこにリポジトリが作成される

- git rm ファイル/ディレクトリ
    - 対象をWorkTreeから削除し、かつ、削除した状態をStagingAreaに登録する。
    - Git管理下のファイル等は、この方法で削除するのが望ましい。
    - (git rmに頼らず削除した場合は、自分でaddしてその状態を登録する必要がある)

- git rm **-r** ディレクトリ
    - 中身を持つディレクトリを削除する場合、-r optionを書く。recursive.

---
## WrokTree から StageArea へ

- **git add** *file/Directory'sPath*
    - 対象をStagingAreaに登録
    - [git add **.**] と命令すれば、カレントディレクトリが対象になる

- **git reset HEAD** *file/Directory'sPath*
    - 直前(HEAD)のaddを無かったことにする。
    - WorkTreeへの影響はない。

- git diff
    - addした後のWorkTreeでどんな変更が行われたかを詳しく確認(テキストタイプ)
    - **--cached** : Staging Areaにどんな変更が登録されているか

---
## Committng ( StageArea => GitDirectory )

- **git Commit**
    - Staging Areaの登録状態を、Git directoryへコミット。
    - VScodeが自動起動する。コメントを書き、保存(ctrl+s)=>閉じる(ctrl+w)、でコミット開始。
    - 1行目にタイトル、2行目は空行、3行目に詳細、というコメントが望ましい。
    - **-m "hogeHoge"** => コマンド入力時に1行コメントを書いて、すぐコミット。

---
## GitDirectory(ローカル)で使用するコマンド

- git **log**
    - GitDirectoryに対するコミットの履歴を見る

- git **checkout** *branchName*
    - 例: git checkout master
    - 操作するブランチを対象ブランチに切り替える

---
## Git Config
- git config --list => 設定一覧の確認(item名と値の組み合わせで一覧表示)
- git config *item'sName* => そのitemの値を見る
- git config **--global** *Item* *Value* =>項目の値を登録/変更
    - git config **--global user.name** *userName* => ユーザ名の登録/更新
    - git config **--global user.email** *mailAddress* => メールアドレス登録/更新
    - git config **--global core.editor** "code --wait" => git命令中に自動起動するエディタの起動命令文
---
## .gitconfig fileの位置    (~/.gitconfig)
- そのユーザーのhome directory[**~**]の下に[**.gitconfig**]という設定ファイルが存在する。
- 内容の登録/更新は上記の[git config --global item value]で行う。
- 確認は、[less ~/.gitconfig] => ホーム(~)にある.gitconfigを閲覧(less)、の意

---
# GitHubを絡めたGitコマンド

---
## GitHubで他のリポジトリをフォークする

- 対象リポジトリのページで、右上の[Fork]を押す。アカウント選択をせまられたら自分のを選択。

---
## GitHub.com上の自分のリポジトリを、ローカル・リポジトリとして取得

- **git clone** *address*
    1. addressの取得(ブラウザ):
        1. ローカル・リポジトリにしたいリモート・リポジトリのページをブラウザで開く
        1. リモート・リポジトリのページの、緑ボタン[Clone or download]を押す
        1. [Clone with SSH]の状態であることを確認。そうでなければ変更。
        1. 表示URLの横にあるコピーアイコンを押すと、URLがクリップボードに保存される
    1. bashでgit clone と書き、クリップボードのURLをペースト
        - **[Shift]+[Insert]** ： GitBash上にペーストするショートカット
    1. 実行すると、カレント(.)にローカル・リポジトリのディレクトリが作成される。

---
## Branch (ブランチ) 関係

- **git branch**
    - いま存在するbranchを表示。「*」接頭文字はいま使用中のbranchであることを示す

- **git branch** *newBranch'sName*
    - その名称のbranchを作成

- **git checkout** *targetBranc'shName*
    - 対象ブランチに操作を切り替える。
    - ブランチを切り替えた後のコミット等の操作は、そのブランチに対して行われる。

- **git diff** *targetBranch'sName*
    - 操作中のbranchと、対象branch名との差分を表示する。

---
## Pull Request 関連

- **git push** remote-repository名 branch名
    - Remote-Repositoryのbranchに対し、Local-Repositoryから該当branchをプッシュ。
    - Remote-Repository内にそのbranchが無いなら、同名のbranchが作られる。
    - 1つのRepositoryには、同名のbranchは1つしか存在できない。

---
## Remote repositoryのデータをLocalに反映

- git **pull** *remoteRepository'sName* *branch'sName*
    - 例：git pull origin master
    - [リモートリポジトリ => ローカルリポジトリ => ワークツリー] まで一気に反映

- git **fetch** *remoteRepository'sName*
    - 例：git fetch origin
    - [リモートリポジトリ => ローカルリポジトリ] まで反映

---
## Linux commands

- ls :ファイルを見る
    - -a    :隠しファイル(.xxx)も見る
    - -l    :パーミッション等の詳細も同時に見る。

- mkdir ディレクトリ名 : ディレクトリ作成

- **rm** *target*
    - 対象を削除する。
    - **-r** : 傘下に何かあっても消す。確認あり。
    - **-rf** : 上記の確認なしバージョン。

- less *file'sPath*
    - 対象ファイルのテキストを閲覧

---
## VScode の起動

- **code** *file'sPath*
    - VScodeが起動し、対象ファイルを開く。
    - 対象ファイルが無いなら、その名前を持つ新規ファイルの編集が始まる。
        - それを上書き保存すれば、その名前のファイルが作られる

- **code** *directory'sPath*
    - VScodeが起動し、対象ディレクトリが左側に展開されるので、そこで作業。
    

---
## ファイルをwindows既定のプログラムで開く

- **start** *file'sPath*
    - 例: start index.html  (そのhtmlを既定ブラウザで開く)