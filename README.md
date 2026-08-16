# AIエージェント共通ルール

Claude Code、Codex、その他の実装エージェントが、PCとクラウドの両方で同じ作業基準を使うための共通管理リポジトリです。

現在は **共通ルールv0.3.0（試行版）** です。24リポジトリの現在内容、既定ブランチ履歴497commit、非既定ブランチ31本、Issue、CIを棚卸しし、全共通・カテゴリ別・製品固有・判断待ちへ分類しました。Kids Questと他プロジェクトで実作業を行い、効果と過剰な制約を確認してからv1.0へ正式化します。

## 管理するもの

- [全プロジェクト共通ルール](./agent-rules/COMMON_RULES.md)
- [カテゴリ別ルール](./agent-rules/CATEGORY_RULES.md)
- [AI・モデル選定と実績管理](./agent-rules/AI_ROUTING.md)
- [プロジェクト固有ルールのテンプレート](./agent-rules/PROJECT_RULES_TEMPLATE.md)
- [Claude Code用テンプレート](./agent-rules/CLAUDE.template.md)
- [全リポジトリ監査結果](./docs/repository-audit-2026-08-16.md)
- 共通の不具合／保留作業Issueフォーム
- 共通のPull Requestテンプレート

## 各リポジトリへの導入方法

1. `agent-rules/COMMON_RULES.md` の `COMMON_RULES_START` から `COMMON_RULES_END` までを、対象リポジトリのルート `AGENTS.md` へ配置する。
2. [カテゴリ別ルール](./agent-rules/CATEGORY_RULES.md)から該当カテゴリを選び、そのrepoでの正本・コマンド・公開先とともに固有区画へ要約する。
3. その後ろへ、その製品だけに適用するプロジェクト固有ルールを追加する。
4. ルート `CLAUDE.md` の先頭へ `@AGENTS.md` を記載する。
5. [AI・モデル選定と実績管理](./agent-rules/AI_ROUTING.md)を参照し、そのrepoの通常担当、高リスク時、軽量モデル範囲、独立レビュー条件を固有区画へ記載する。
6. 既存のルールがある場合は上書きせず、共通・カテゴリ・製品固有・モデル固有へ分類して統合する。
7. 導入後は実際の作業で試し、AI／モデル、切替理由、初回成功、レビュー結果を追跡Issueへ記録する。

> GitHubの `.github` リポジトリからIssue／PRテンプレートは既定値として利用されますが、`AGENTS.md` は各リポジトリへ配置する必要があります。

## ルールの分類

| 内容 | 保存先 |
|---|---|
| ほぼ全作業で守る安全・品質・Git基準 | `COMMON_RULES.md` |
| 特定技術・運用群で守ること | `CATEGORY_RULES.md`から選択し、各AGENTS.mdへ適用 |
| 製品仕様、正本、コマンド、対応端末、公開方法 | 各リポジトリのAGENTS.md固有区画 |
| AI基盤・モデル選定、切替、実績記録 | `AI_ROUTING.md`＋各Issue／PR |
| Claude Codeだけの補足 | 各リポジトリのCLAUDE.md |
| 必ず機械的に実行すること | test、CI、hook、schema、generator |
| 今後対応すること／判断待ち | 対象リポジトリのGitHub Issue |
| 長い作業手順・障害記録 | 別の手順書またはSkill |

## ルール追加の基準

次のいずれかを満たす場合に候補化します。

- 同種の失敗、見落とし、手戻りが2回以上起きた
- 2つ以上のプロジェクトで必要だった
- 1回でもデータ損失、セキュリティ、課金、誤公開、主要導線停止につながり得る
- 完了報告と実際のcommit／push／CI／公開状態が一致しなかった
- 残課題がチャットだけに残り、引き継げなかった

単発の特殊事情は共通化せず、カテゴリ／プロジェクト固有ルールまたはIssueへ残します。AGENTS.mdへ現在の進捗や長い障害履歴を溜めず、Issue／手順書へ分離します。

## 判断待ち

- [既定ブランチと未統合作業ブランチの整理](https://github.com/syoudai0514/.github/issues/2)
- [共通・カテゴリルールの配布／同期方法](https://github.com/syoudai0514/.github/issues/3)
- [全リポジトリへの導入範囲](https://github.com/syoudai0514/.github/issues/4)
- [金融・定期実行の実運用境界](https://github.com/syoudai0514/.github/issues/5)
- [追跡済みログ・ビルドキャッシュの整理](https://github.com/syoudai0514/.github/issues/6)

## 試行

- Pilot repository: [Kids Quest](https://github.com/syoudai0514/kids-quest)
- Tracking issue: [共通ルールの試行・正式化](https://github.com/syoudai0514/kids-quest/issues/3)
