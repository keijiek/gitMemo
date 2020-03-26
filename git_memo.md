Git Memo
====================================================

Git commands
----------------------------------------------------
- git init
    - ワークツリーのディレクトリで実行すると、そこに、リポジトリが作成される

- git status
    - ワークツリー傘下のファイルの状態を確認

- git add ファイル/ディレクトリ名
    - ステージングエリアに移動
    - git add . で、そこにある全部

- git diff
    - addした後のワークツリーでどんな変更が行われたかを確認
    - --cached : ステージングエリアにどんな変更が登録されているか

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
    - -a   :隠しファイルも見る

- mkdir ディレクトリ名 : ディレクトリ作成

- rm 対象名 : 削除
    - -r : 傘下に何かあっても消す
    - -rf : 上記の確認なしバージョン

- less ファイル名 : ファイルのテキストを閲覧
