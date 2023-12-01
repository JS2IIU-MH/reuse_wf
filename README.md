# reuse_wf
Reusable Github workflow

![](https://byob.yarr.is/JS2IIU-MH/reuse_wf/passing_lints)
![](https://byob.yarr.is/JS2IIU-MH/reuse_wf/time1)
[![License: MIT](https://img.shields.io/badge/License-MIT-brightgreen.svg)](LICENSE)

## Github workflowの再利用
異なるリポジトリでの共通workflow管理を簡略化するために、本リポジトリのymlファイルを参照してworkflowを流すことを試しています。

| ファイル        | 内容 |     | 
| --------------- | ---- | --- | 
| re_flake8.yml   |  呼び出されるymlファイル  |     | 
| call_flake8.yml |  呼び出す側のymlファイル  |     | 
|                 |      |     | 

## Reference
- [ワークフローの再利用 - GitHub Docs](https://docs.github.com/ja/actions/using-workflows/reusing-workflows)
- [Check! GitHub Actions 再利用可能なワークフローのポイントを抑える](https://zenn.dev/dzeyelid/articles/fc4bd999fbccd8)
- [GitHub Actions の「ワークフローの再利用」をプライベートリポジトリで使う - kakakakakku blog](https://kakakakakku.hatenablog.com/entry/2023/01/10/081119)