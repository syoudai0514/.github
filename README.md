# AIエージェント共通ルール

Claude Code、Codex、その他の実装エージェントが、PCとクラウドの両方で同じ作業基準を使うための共通管理リポジトリです。

現在は **v0.1.0（試行版）** です。Kids Questと他プロジェクトで実作業を行い、効果と過剰な制約を確認してからv1.0へ正式化します。

## 管理するもの

- [共通エージェントルール](./agent-rules/COMMON_RULES.md)
- [プロジェクト固有ルールのテンプレート](./agent-rules/PROJECT_RULES_TEMPLATE.md)
- [Claude Code用テンプレート](./agent-rules/CLAUDE.template.md)
- 共通の不具合／保留作業Issueフォーム
- 共通のPull Requestテンプレート

## 各リポジトリへの導入方法

1. `agent-rules/COMMON_RULES.md` の `COMMON_RULES_START` から `COMMON_RULES_END` までを、対象リポジトリのルート `AGENTS.md` へ配置する。
2. その後ろへ、その製品だけに適用するプロジェクト固有ルールを追加する。
3. ルート `CLAUDE.md` の先頭へ `@AGENTS.md` を記載する。
4. 既存のルールがある場合は上書きせず、共通・製品固有・モデル固有へ分類して統合する。
5. 導入後は実際の作業で試し、結果を追跡Issueへ記録する。

> GitHubの `.github` リポジトリからIssue／PRテンプレートは既定値として利用されますが、`AGENTS.md` は各リポジトリへ配置する必要があります。

## ルールの分類

| 内容 | 保存先 |
|---|---|
| 複数プロジェクトで毎回守ること | `COMMON_RULES.md` |
| 製品仕様、コマンド、対応端末、公開方法 | 各リポジトリの `AGENTS.md` 固有区画 |
| Claude Codeだけの補足 | 各リポジトリの `CLAUDE.md` |
| 必ず機械的に実行すること | テスト、CI、hook |
| 今後対応すること | 対象リポジトリのGitHub Issue |
| 長い作業手順 | 別の手順書またはSkill |

## ルール追加の基準

次のいずれかを満たす場合に候補化します。

- 同種の失敗、見落とし、手戻りが2回以上起きた
- 2つ以上のプロジェクトで必要だった
- 1回でもデータ損失、セキュリティ、誤公開、主要導線停止につながり得る
- 完了報告と実際のcommit／push／公開状態が一致しなかった
- 残課題がチャットだけに残り、引き継げなかった

単発の特殊事情は共通化せず、プロジェクト固有ルールまたはIssueへ残します。

## 試行

- Pilot repository: [Kids Quest](https://github.com/syoudai0514/kids-quest)
- Tracking issue: [共通ルールの試行・正式化](https://github.com/syoudai0514/kids-quest/issues/3)
