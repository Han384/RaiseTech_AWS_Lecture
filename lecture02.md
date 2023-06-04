# 【lecture02  課題：講座での学び】
## 《Git/GitHubを用いたチーム開発におけるバージョン管理の手順整理》

\--------------------------------<br>
**■ Git/GitHub (※初めにやること)**<br>
\--------------------------------<br>
<GitHub(リモートリポジトリ)にて操作>
- アカウント作成
- リモートリポジトリの作成

\--------------------------------<br>
<Git(ローカルリポジトリ)にて操作><br>

(操作)<br>
- git clone [リモートリポジトリのURL]　：リモートリポジトリのクローンを作成

(初期設定)<br>
- git config --list　：設定を確認
- git config --global user.name "GitHubのユーザー名"　：ユーザー設定
- git config --global user.email "GitHubに登録しているメールアドレス"　：メールアドレス設定
- git config --global init.defaultBranch main　：新規リポジトリのデフォルトブランチ名をmainに変更

\--------------------------------<br>
**■ GitHub-Flow に沿ったバージョン管理作業手順**<br>
\--------------------------------<br>
<Git (ローカルリポジトリでの作業)><br>
1. 　[branch:main]　git pull (origin main)　：リモートリポジトリより、マージされた最新のブランチ内容を反映<br>
2. 　[branch:main]　git branch -d < old branch >　：マージ済みの古いブランチの削除<br>
3. 　[branch:main]　git switch -c < new branch >　：新規ブランチ作成し、ブランチを切替<br>
4. 　[branch:< new branch >]　(編集作業)<br>
5. 　[branch:< new branch >]　git add . (ファイル名)　：変更をステージに追加<br>
6. 　[branch:< new branch >]　git commit (-m "コミットコメント")　：ステージに追加された変更をコミット<br>
7. 　[branch:< new branch >]　git push (origin < new branch >)<br>
      ：リモートリポジトリに新規ブランチの内容を作成し、送信 (※個人アクセストークンが必要)<br>
8. 　[branch:< new branch >]　git push --set-upstream origin < new branch >　：※リモートリポジトリにないブランチの設定<br>

\--------------------------------<br>
<GitHub (リモートリポジトリでの作業)><br>
　9. 　プルリクエスト＆マージ<br>
　10. 　マージした< new branch >の削除<br>

\--------------------------------<br>
<Git (ローカルリポジトリでの作業)><br>
　11. 　[branch:< new branch >]　git switch main　：mainブランチへ切替<br>
　12. 　上記 1. に戻る<br>

\--------------------------------<br>
**■ その他**<br>
\--------------------------------<br>
【Git (確認コマンド)】<br>
- git branch　：現在のブランチを確認
- git status　  ：現在の状態を確認
- git diff　　 ：差分を表示
- git log   　　：(commit等の)ログを確認

---
## 【感想】
講義内容のほか、副教材の内容や調べたことを実際にコマンドを打って確認。<br>
一連のコマンドを整理し、後日見返すことのできるよう自分なりに一連の手順をフロー化してみました。<br>
Markdownは想定通りの記述とならないこともあり苦戦しましたが、調べて記述し、表示を確認。<br>
これを繰り返し想定通りの見栄えになるよう工夫をしてみました。<br>
今回、知識の整理や定着を図る目的で手順(フロー)化してみましたが、良いアウトプットとなりました。<br>

## 【参考リンク】
- [Qiita：GitHubがパスワード認証を廃止するらしいので](https://qiita.com/shiro01/items/e886aa1e4beb404f9038)
- [GitHub Docs：Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/creating-a-personal-access-token)　⇨(※git push 時にアクセストークン(パスワードの代わり)の発行が必要！)
- [GitHub Gitチートシート](https://training.github.com/downloads/ja/github-git-cheat-sheet.pdf)
- [Qiita：gitコマンド チートシート](https://qiita.com/TaaaZyyy/items/b2b68aec99789374a204)
- [Zenn：Gitチートシート](https://zenn.dev/shey0624/articles/316c01647358c4)
- [日本語Markdownユーザー会](https://www.markdown.jp/syntax/)
- [backlog：【マークダウン記法とは？】マークダウンの書き方を網羅的に解説](https://backlog.com/ja/blog/how-to-write-markdown/)
- [Qiita：マークダウン記法 一覧表・チートシート](https://qiita.com/kamorits/items/6f342da395ad57468ae3)
- [Qiita：Markdown 記法 サンプル 一覧](https://qiita.com/jkjoluvjlajelljicvjzojieoaid/items/01cd7ff819bc2e69b652)
- [ktMarkDown.js](https://sitearo.com/soft/ktMarkDown.js/ktmd_doc/gd_whats.html)
