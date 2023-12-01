# reuse_wf
Reusable Github workflow

![](https://byob.yarr.is/JS2IIU-MH/reuse_wf/passing_lints)
![](https://byob.yarr.is/JS2IIU-MH/reuse_wf/time1)
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](LICENSE)

## Github workflowの再利用
- 異なるリポジトリでの共通のworkflow管理を簡略化するために、本リポジトリのymlファイルを参照してworkflowを流すことを試しています。
- 同じリポジトリ内では正しく動作することを確認しておりますが、別リポジトリからの実行は確認できておりません。
- BYOBバッジの設置についてはこの`README.md`のソースを参照してください。
    ```raw
    ![](https://byob.yarr.is/{your_github_account}/{your_repo}/passing_lints)
    ![](https://byob.yarr.is/{your_github_account}/{your_repo}/time1)
    ```

| ファイル        | 内容 | Workflow | 
| --------------- | ---- | --- | 
| `re_flake8.yml`   | 呼び出されるymlファイル | push時にいくつかのPythonバージョンでflake8テストを実行。リポジトリ内すべての*.pyファイルが対象。テスト状況をREADMEのBYOBバッジで表示する。 | 
| `call_flake8.yml` | 呼び出す側のymlファイル | このファイルを呼び出す側のリポジトリに設置する。`./github/workflow/`の下に。おそらくこのファイルを置くだけで良いはず。 | 
|                 |      |     | 

## Reference
- [ワークフローの再利用 - GitHub Docs](https://docs.github.com/ja/actions/using-workflows/reusing-workflows)
- [Check! GitHub Actions 再利用可能なワークフローのポイントを抑える](https://zenn.dev/dzeyelid/articles/fc4bd999fbccd8)
- [GitHub Actions の「ワークフローの再利用」をプライベートリポジトリで使う - kakakakakku blog](https://kakakakakku.hatenablog.com/entry/2023/01/10/081119)