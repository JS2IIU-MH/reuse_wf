# reuse_wf
Reusable Github workflow

![](https://byob.yarr.is/JS2IIU-MH/reuse_wf/passing_lints)
![](https://byob.yarr.is/JS2IIU-MH/reuse_wf/time1)
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](LICENSE)

## Github workflowの再利用
- 異なるリポジトリでの共通のworkflow管理を簡略化するために、本リポジトリのymlファイルを参照してworkflowを流すことを試しています。
- このリポジトリでは`flake8`によるコードチェックを異なるPythonバージョンで実行させるActionと、このページの上のほうにあるBYOBバッジ（flake8/passingのバッジ）を生成するActionを走らせるサンプルを公開しています。
- ~~同じリポジトリ内では正しく動作することを確認しておりますが、別リポジトリからの実行は確認できておりません。~~
- BYOBバッジの設置についてはこの`README.md`のソースを参照してください。
    ```raw
    ![](https://byob.yarr.is/{your_github_account}/{your_repo}/passing_lints)
    ![](https://byob.yarr.is/{your_github_account}/{your_repo}/passing_pytest)
    ![](https://byob.yarr.is/{your_github_account}/{your_repo}/time1)
    ```

| ファイル        | 内容 | Workflow | 
| --------------- | ---- | --- | 
| [`.github\workflows\call_flake8.yml`](.github\workflows\call_flake8.yml) | 呼び出す側のymlファイル | このファイルを呼び出す側のリポジトリに設置する。`./github/workflows/`の下に。~~おそらくこのファイルを置くだけで良いはず。~~<br>呼び出すテスト内容に応じて書き換える。 | 
| [`.github\actions\create_env_cache\action.yml`](.github\actions\create_env_cache\action.yml) | Actionの設定ファイル | `.github\actions\create_env_cache\`以下に配置してください。Actionsの実行を高速化するためキャッシュを生成します。 | 
| **以下、テスト内容に応じて使い分ける** | |
| [`.github\workflows\re_flake8.yml`](.github\workflows\re_flake8.yml)   | 呼び出されるymlファイル | push時にいくつかのPythonバージョンでflake8テストを実行。リポジトリ内すべての*.pyファイルが対象。テスト状況をREADMEのBYOBバッジで表示する。 | 
| [`.github\workflows\re_flake8_pytest.yml`](.github\workflows\re_flake8_pytest.yml) | 呼び出されるymlファイル | トリガされると、`flake8`, `pytest` を実行。リポジトリ内すべての*.pyファイルが対象。テスト状況をREADMEのBYOBバッジで表示する。|


## 対象リポジトリの設定
- 呼び出し側リポジトリの一番上の階層に`requirements.txt`を置いてください。Actionsの実行に必要です。仮想環境を使われている方は問題ないと思いますが、仮想環境を使わずに開発されている場合でいろいろインストールしているとActionsの実行に時間がかかる場合があります。
- 呼び出し側リポジトリの[Setting]-[Actions]-[General]の設定で[Workflow permissions]を確認してください。Read and write permissionsにチェックしているか確認してください。この設定がされていないとActionがうまく動きません。

  <img src="./doc/004.png" width=600>

- Read and write permissionsを設定してもダメな場合は、同じ[General]の設定の[Actions permissions]を確認してください。Allow all actions and reusable workflowsを選択してください。デフォルトではDisable actionsになっているかもしれません。

  <img src="./doc/003.png" width=600>

## 実行時イメージ
  <img src="./doc/workflow_diagram.png" width=700>

## Change Log

| date | change |
| --- | --- |
| 2024/12/29 | Python `3.11.11`, `3.12.8`, `3.13.1`で`flake8`テストするように変更しました。Linux/Unix向けのStable Releasesのバージョンに合わせています。 |
| 2024/12/31 | `flake8`と`pytest`を実行するための[`.github\workflows\re_flake8_pytest.yml`](.github\workflows\re_flake8_pytest.yml)を追加しました。 |

## Reference
- [ワークフローの再利用 - GitHub Docs](https://docs.github.com/ja/actions/using-workflows/reusing-workflows)
- [Check! GitHub Actions 再利用可能なワークフローのポイントを抑える](https://zenn.dev/dzeyelid/articles/fc4bd999fbccd8)
- [GitHub Actions の「ワークフローの再利用」をプライベートリポジトリで使う - kakakakakku blog](https://kakakakakku.hatenablog.com/entry/2023/01/10/081119)
- [RubbaBoy/BYOB: Bring Your Own Badge - Create dynamic README badges based off of your GitHub Actions](https://github.com/RubbaBoy/BYOB)
- [Bring Your Own Badge · Actions · GitHub Marketplace](https://github.com/marketplace/actions/bring-your-own-badge)
