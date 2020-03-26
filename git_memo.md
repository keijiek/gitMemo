Git Memo
====================================================

Git commands
----------------------------------------------------
- **git init**
    - WorkTreeのディレクトリで実行すると、そこにリポジトリが作成される

- git status
    - WorkTree傘下のファイルの、登録状態を確認

- **git add** ファイル/ディレクトリ名
    - 対象をStagingAreaに登録
    - git add **.** で、そこにある全てを対象にする

- **git reset HEAD** ファイル/ディレクトリ
    - 直前(HEAD)のaddを無かったことにする。
    - WorkTreeへの影響はない。

- git diff
    - addした後のWorkTreeでどんな変更が行われたかを詳しく確認(テキストタイプ)
    - **--cached** : Staging Areaにどんな変更が登録されているか

- **git Commit**
    - Staging Areaへの登録状態を、Git directoryへコミット。
    - 対応エディタが自動起動するので、3行ほどコメントを書いて保存、閉じるとコミット開始。
    - **-m "comment"** => コマンド入力時に1行コメントを書いてしまう。

- **git checkout** **--** ファイル/ディレクトリ
    - Work Treeにある対象を、直前にコミットした状態(Git directoryの状態)に戻す
    - ファイル新規作成時やファイル名変更時の後など、思った通りの挙動にならない状況もある

- git rm ファイル/ディレクトリ
    - 対象をWorkTreeから削除し、かつ、削除した状態をStagingAreaに登録する。
    - (rmに頼らず手動で削除した場合は、自分でaddでその状態を登録する必要がある)

Git config
----------------------------------------------------
- git config --list => 設定一覧の確認
- git config 項目名 => 項目名(user.name / user.email等)の値を見る
- git config --global **user.name** xxxx => ユーザー名xxxxさんの登録
- git config --global **user.email** xxxx@xxx.com => メールアドレス登録
- git config --global **core.editor** "code --wait" => git命令中に自動起動するエディタの起動命令文

ファイルの位置
----------------------------------------------------
- home directory(~)に、[.gitconfig]というユーザー用の設定ファイルが存在する。
- git config **--global** 項目名 値 => 項目に値を登録。[.gitconfig]がそのように修正される
- 確認は、[less ~/.gitconfig] => ホーム(~)にある.gitconfigを閲覧、の意

Linux commands
----------------------------------------------------
- ls :ファイルを見る
    - -a   :隠しファイル(.xxx)も見る

- mkdir ディレクトリ名 : ディレクトリ作成

- rm 対象名 : 削除
    - -r : 傘下に何かあっても消す
    - -rf : 上記の確認なしバージョン

- less ファイル名 : ファイルのテキストを閲覧
