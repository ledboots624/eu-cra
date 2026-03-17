# EU CRA対策（SEMI規格準拠企業向け戦略立案）

## テーマ

**調査テーマ**: EU CRA対策（SEMI規格準拠企業向け戦略立案）

**説明**: SEMI規格を遵守する日本の半導体装置ソフトウェア企業が、EUサイバーレジリエンス法（CRA）に低コストかつ確実に準拠するための段階的ロードマップと技術戦略を策定する。

### 前提条件

> EU CRA（サイバーレジリエンス法）への対応戦略を立案する。SEMI規格を既に遵守している日本の半導体装置向けソフトウェア開発企業がEU輸出を継続しながら、最低限のコストでCRA準拠を達成するための段階的ロードマップを策定する

- **purpose**: SEMI規格遵守を基盤としつつ、EU CRAの必須要件（Must）を明確化し、学習から導入までの段階的な実施計画とコスト最適化戦略を策定する。法的ペナルティ回避を確保しながら、顧客・パートナーからの変動的なコンプライアンス要求にも対応できる体制を構築する
- **focus**: CRA規制スコープの確認：EU輸出販売製品への適用条件・責任主体（製造者・輸入者・販売者）の整理、OSS除外要件・重要製品分類（Class I/Class II）の判定基準, SEMI規格（SEMI E187/E188等）とCRA要件のマッピング：既存SEMI準拠資産の再利用可能範囲の特定とギャップ分析, CRA必須要件のMust/Want分類：製品設計（セキュアバイデザイン・デフォルトセキュリティ）・脆弱性管理（5年間サポート義務・パッチ提供）・ドキュメント適合宣言（CE宣言・SBOM・技術文書）の3領域ごとの最低対応ライン, IEC 62443・ISO 27001等の関連規格とCRAの重複活用によるコスト削減パターン分析, 段階的導入ロードマップ：フェーズ別（学習→ギャップ分析→体制構築→技術対応→適合宣言・審査準備）の優先順位付き実施計画と工数概算, SBOM要件の詳細分析：CRAが求めるSBOM形式・管理運用の最低要件と実装コスト, 脆弱性開示・インシデント報告義務の運用設計：ENISAへの24時間通知義務等の運用負荷最小化策, 未対応リスクシナリオ：罰則（最大1500万ユーロまたは売上高2.5%）および市場アクセス停止リスクの評価, 批評的検証：日本の中小製造業がCRAに対応した実績・先行事例の収集、実現可能性の多角的評価
- **research_strategy**: ①まず「CRA規制スコープ確認」でEU輸出販売済み製品への適用条件・責任主体・製品クラス分類を確定し、調査の前提を固める（抽象化リスクを排除）。②次に「SEMI規格×CRA要件マッピング」を実施し、E187/E188等のSEMI規格が既に充足しているCRA要件を特定して再利用可能な資産を洗い出す。③「3領域のMust/Want分類」として、製品設計・脆弱性管理・ドキュメント適合宣言の各領域でCRA法文および技術規格（EN 18031等）を参照しながら最低対応ラインを明確化する。④「関連規格の重複活用分析」でIEC 62443・ISO 27001との重複領域を特定し、コスト削減パターンを数値・工数ベースで整理する。⑤「段階的導入ロードマップ策定」でフェーズ別の優先順位付き実施計画（学習→体制構築→技術対応→審査準備）を具体化し、工数・コスト概算を付記する。⑥最後に「批評的検証」として日本企業の先行事例・実現可能性・想定リスクをレビューし、ロードマップの実効性を評価する。収集→分析→比較→批評の段階的フローで網羅性と実用性を両立する
- **constraints**: MUST=["EU輸出販売済み製品に対するCRA適用要件を明確化すること（直接輸出のため製造者責任が適用される前提で分析）","SEMI規格（E187・E188等）との要件マッピングを含め、既存準拠資産の再利用を最大化すること","法的ペナルティ回避のための必須対応（Must）と推奨対応（Want）を明確に区別すること","CRAの適合宣言（DoC）・CEマーキング・SBOM・技術文書の最低要件を具体的に示すこと","段階的導入ロードマップに工数・コスト概算を含めること"], WANT=["IEC 62443・ISO 27001等の関連規格との重複活用によるコスト削減策を提示すること","SBOM生成・管理ツールの選定候補（OSS優先）を含めること","顧客・パートナーからの変動的なCRAコンプライアンス要求に対応するための文書整備方針を提示すること","日本の製造業における先行対応事例・参考情報を収集すること","経営層への説明に使える罰則リスクの定量的整理を含めること"]
- **background**: company_profile=日本の半導体装置関連ソフトウェア開発会社。EU向け輸出販売済み。製造者責任が適用される立場, existing_compliance=SEMI規格遵守済み（E187・E188等を想定）, current_cra_status=CRA未対応。学習フェーズから導入まで一貫したサポートが必要, primary_driver=法的ペナルティ回避（罰則回避）＋顧客・パートナーからの変動的なコンプライアンス要求への対応
- **output_artifacts**: CRA要件×SEMI規格マッピング表（既存資産の再利用可能範囲を明示）, 3領域別Must/Want対応チェックリスト（製品設計・脆弱性管理・ドキュメント適合宣言）, 段階的導入ロードマップ（フェーズ別・優先順位付き・工数概算付き）, コスト削減パターン分析（関連規格の重複活用）, リスクシナリオ整理（未対応時の罰則・市場リスク）, 社内共有用スライド（開発メンバー向け）

---

## 本資料について

本資料は **[AI Research Agent](https://github.com/ledboots624/ai-research-agent)** により自動生成されたリサーチ結果です。複数のAIモデル（claude-opus-4.6, claude-sonnet-4.6, gemini-3-pro-preview, gpt-5.3-codex）がリレー方式で調査・分析・検証を行い、エビデンスベースの構造化された調査資料を生成しています。

### 生成プロセス

1. **情報収集**: AIが学習データに基づいて関連情報を収集・整理します
2. **深層分析**: 収集した情報を多角的に分析し、根拠と確信度を付与します
3. **品質検証**: 第三者視点で論理的整合性・根拠の裏付け・情報の偏りを検証します
4. **統合レビュー**: 全ステップの結果を統合し、最終的な結論を導出します

### 読み方の注意

- **AIの学習データに基づく調査です**: Web検索やデータベース照会ではなく、AIモデルの学習データから情報を抽出・推論しています。そのため、情報の正確性は保証されません
- **確信度（Confidence）を参照してください**: 各主張には high / medium / low の確信度が付与されています。low の情報は特に裏取りが必要です
- **品質検証レビューを確認してください**: 調査結果の弱点・未検証事項・情報ギャップが明示されています
- **最終判断は読者が行ってください**: 本資料は判断材料を提供するものであり、結論を押し付けるものではありません

---

## 主要ドキュメント

| ドキュメント | 説明 |
|------------|------|
| [最終レポート（統合レビュー）](./steps/06-integration-review-claude-opus-4.6.md) | 全調査結果を統合した最終結論 |
| [品質検証レビュー](./steps/05-critic-review-claude-sonnet-4.6.md) | 調査結果の信頼性を担保するための品質検証。論理的整合性・根拠の裏付け・情報の偏りを第三者視点で検証 |
| [情報源一覧](./data/sources.json) | 全ソースの集約リスト（Source ID・URL・信頼性評価） |
| [関係図（PNG）](./diagram.png) | リサーチ結果の視覚的サマリー |
| [関係図（SVG）](./diagram.svg) | 高解像度ベクター版 |
| [関係図（編集用）](./data/diagram.drawio) | draw.io で開いて編集可能 |
| [プレゼンスライド（PDF）](./slides.pdf) | プレゼンテーション用スライド |
| [プレゼンスライド（HTML）](./slides.html) | ブラウザで閲覧可能なスライド |

## メタデータ

| 項目 | 値 |
|------|-----|
| **生成方法** | planner |
| **実行日時** | 2026-03-17 11:22:46 |
| **ツール** | AI Research Agent v2.5.0 |
| **手法** | Evidence-based Multi-Model Pipeline |

## パイプライン

| # | 役割 | モデル | 出力 |
|---|------|-------|------|
| 1 | 情報収集 | gemini-3-pro-preview | [情報収集の出力を見る](./steps/01-information-gathering-gemini-3-pro-preview.md) (完了) |
| 2 | 深層分析 | claude-sonnet-4.6 | [深層分析の出力を見る](./steps/02-deep-analysis-claude-sonnet-4.6.md) (完了) |
| 3 | 技術戦略 | gpt-5.3-codex | [技術戦略の出力を見る](./steps/03-technical-strategy-gpt-5.3-codex.md) (完了) |
| 4 | 深層分析 | claude-sonnet-4.6 | [深層分析の出力を見る](./steps/04-deep-analysis-claude-sonnet-4.6.md) (完了) |
| 5 | 品質検証レビュー | claude-sonnet-4.6 | [品質検証レビューの出力を見る](./steps/05-critic-review-claude-sonnet-4.6.md) (完了) |
| 6 | 統合レビュー | claude-opus-4.6 | [統合レビューの出力を見る](./steps/06-integration-review-claude-opus-4.6.md) (完了) |

## 各ステップの要約

### Step 1: 情報収集（gemini-3-pro-preview）

# EU CRA Regulatory Scope & SEMI Gap Analysis (EU CRA規制スコープとSEMI規格ギャップ分析)

## 1. CRA Regulatory Scope & Product Classification (規制適用範囲と製品重要度分類)

EUサイバーレジリエンス法（CRA）は、デジタル要素を含む製品（Products with Digital Elements: PDEs）のライフサイクル全体にセキュリティ要件を課す。半導体製造装置およびその組み込みソフトウェアは、EU市場に上市される限り原則として適用の対象となる。

### Key Findings
*   **Claim 1: CRAの適用範囲と「商用活動」の定義**
    *   CRAは、ハードウェアおよびソフトウェアを含む「デジタル要素を備えた製品」に適用される。SaaS（リモート処理のみでデバイス側にコンポーネントがない場合）はNIS2指令の対象となるが、半導体製造装置の制御PCや組み込みOS、ファームウェアはCRAの対象（PDEs）となる。
    *   **OSSの扱い**: オープンソースソフトウェアは、商業活動（commercial activity）の一環として市場に提供される場合、適用除外とならない。半導体装置に組み込まれて販売されるOSSコンポーネントは、製造者が全責任を負う。
    *   **Requirement Level**: **MUST** (Article 2)
    *   **Evidence**: CRA Final Text Article 2 (Scope), Recital 10.
    *   **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 (Cyber Resilience Act)](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024) — primary_source: true
    *   **Confidence**: high

*   **Claim 2: 重要製品（Important Products）とデフォルトカテゴリの分類**
    *   製品のリスクレベルに応じて3つのカテゴリに分類され、適合性評価手順（Conformity Assessment）が異なる。
    *   **Class I (Lower Risk)**: ID管理システム、ブラウザ、スタンドアロンのウイルス対策ソフト、VPN、ネットワーク管理システム等。
    *   **Class II (Higher Risk)**: ハイパーバイザー、ファイアウォール、改ざん防止マイクロプロセッサ、産業用オートメーション制御システム（IACS）の一部等。
    *   **Default Category (Unclassified)**: 上記リストに含まれない製品。

_...（全84行。詳細は[情報収集の全文](./steps/01-information-gathering-gemini-3-pro-preview.md)を参照）_

### Step 2: 深層分析（claude-sonnet-4.6）

# CRA要件 × SEMI E187/E188 詳細マッピング分析

## Overview（分析概要）

本分析は、EU Cyber Resilience Act（CRA）Annex I に規定される必須セキュリティ要件と、SEMI E187（Fab Equipment Cybersecurity）およびE188（Malware Free Equipment Integration）の要件を条項レベルで対照し、既存SEMI準拠資産の再利用可能範囲と、CRA固有のギャップを特定するものである。

---

## Section 1: CRA Annex I 要件の構造的分解（Structural Decomposition of CRA Annex I）

### 1.1 Annex I Part I — 製品セキュリティ要件（Product Security Properties）

- **Claim**: CRA Annex I Part I は製品のライフサイクル全体にわたる13項目のセキュリティ要件を規定しており、「設計・開発・製造」段階における技術的義務を構成する。これらはすべてMUST要件であり、自己宣言（Module A）の対象製品（Default Category）においても省略不可能である。

- **Evidence**: Annex I Part I は以下の主要要件を列挙している：
  1. **no known exploitable vulnerabilities** — 市場投入時点で既知の悪用可能な脆弱性を含まないこと
  2. **secure by default configuration** — デフォルト設定がセキュリティ的に安全であること（不要機能の無効化）
  3. **protection of confidentiality and integrity** — 保存・転送データの保護
  4. **minimal attack surface** — 攻撃面の最小化（不要なインターフェースの排除）
  5. **effect mitigation** — 他のデバイスへの攻撃伝播防止

_...（全321行。詳細は[深層分析の全文](./steps/02-deep-analysis-claude-sonnet-4.6.md)を参照）_

### Step 3: 技術戦略（gpt-5.3-codex）

少し一次情報を再確認して、CRA条文・SBOM仕様・運用義務の根拠を固めた上で、実装可能な技術戦略に落とし込みます。まず既存の調査ファイルと公式情報を同時に確認します。

公式条文の番号・適用時期・SBOM実装要件を一次情報ベースで確定させます。並行して、OSSツール候補の根拠も集めます。

ローカルの既存リサーチ成果も取り込み、重複調査を減らします。次に既存レポート内の根拠を抽出します。

ネットワーク取得制約があるため、公開GitHub一次資料（仕様・ツールREADME）から根拠を確保します。SBOM形式とOSSツール評価の裏付けを固めます。

CRA条文の該当条項（SBOM・24h報告・設計要件・適用開始日）を個別にクロスチェックして、実装に直結するレベルまで確定します。

次に、SBOMの「最低フィールド」を仕様レベルで落とすため、CycloneDX/SPDXのスキーマ必須項目を直接確認します。

SBOMを“作るだけ”で終わらせないため、生成・検証・保管・脆弱性相関までをOSSで回せる実装スタックの一次根拠を集めます。

# Technical Strategy for EU CRA Compliance（EU CRA適合の技術戦略）

## Findings（主要な発見）

**Claim（主張）**: CRA対応の最小コスト化は、`SEMI E188の既存Software Inventoryを機械可読SBOMへ変換`し、`報告ワークフロー（24h/72h）を先行実装`する方針が最も実装効率が高い。  

_...（全266行。詳細は[技術戦略の全文](./steps/03-technical-strategy-gpt-5.3-codex.md)を参照）_

### Step 4: 深層分析（claude-sonnet-4.6）

# EU CRA 段階的導入ロードマップと関連規格重複活用戦略

## Overview（分析概要）

本分析は、前ステップのCRA×SEMI E187/E188マッピング分析および技術戦略調査を基盤として、SEMI規格遵守済みの日本の半導体装置ソフトウェア製造者がCRA準拠を達成するための段階的ロードマップを具体化する。各フェーズの工数概算・優先順位・依存関係を定義し、IEC 62443・ISO 27001との重複活用によるコスト削減パターンを中小企業の現実的リソース制約の下で最適化する。

---

## Section 1: 施行スケジュールと外部期限制約（External Deadline Constraints）

### 1.1 CRA施行タイムラインの確定

- **Claim**: CRA（Regulation (EU) 2024/2847）は2024年12月11日に発効し、段階的施行スケジュールが法令により確定している。ロードマップ設計において最も重要な制約は「インシデント報告義務の2026年9月先行施行」であり、製品設計要件の完全適用（2027年12月）より1年以上早い。

- **Evidence**:
  - **2024年12月11日**: CRA発効（Official Journal掲載）
  - **2026年9月11日**: **Article 14（インシデント・脆弱性報告義務）先行施行** ← 最優先期限
  - **2026年9月11日**: Article 17および関連委任法令の一部施行
  - **2027年12月11日**: CRA完全適用（Annex I製品設計要件、DoC、CEマーキング義務）
  - **移行期間**: 2024年12月〜2027年12月の3年間が実質的な準備期間

_...（全489行。詳細は[深層分析の全文](./steps/04-deep-analysis-claude-sonnet-4.6.md)を参照）_

### Step 5: 品質検証レビュー（claude-sonnet-4.6）

# Critic Review（批判的レビュー）

## Validation Summary（検証サマリー）

- **Claim without Evidence（根拠なしの主張）**: 7件
- **Evidence without Source（出典なしの根拠）**: 4件
- **Conclusion without Confidence（確信度なしの結論）**: 0件（全結論にConfidence付き）
- **全体の Validation 結果**: **PARTIAL**（法令根拠は堅固だが、工数推計・重複活用率・SEMI再利用率の主要数値がすべて著者推論であり、独立した一次情報による検証がない）

---

## 義務レベル分析（Requirement Level Analysis）

- **MUST（必須）**: 18件 — 法令原文に直接根拠あり
- **SHOULD（推奨）**: 6件 — 特定ツール選定・フレームワーク活用等
- **MAY（任意）**: 0件（明示なし）
- **MUST_NOT（禁止）**: 0件（分析対象外）

### ⚠️ 義務レベル解釈リスク（最重要）

_...（全291行。詳細は[品質検証レビューの全文](./steps/05-critic-review-claude-sonnet-4.6.md)を参照）_

### Step 6: 統合レビュー（claude-opus-4.6）

Now let me check for any existing EU CRA research outputs and gather the latest CRA information to produce a comprehensive integration review.

Now I have all the research data needed. Let me compose the comprehensive integration review.

# 統合レビュー

## Executive Summary（総括）

SEMI規格（E187/E188）準拠企業がEU CRA（Regulation (EU) 2024/2847）に準拠するためには、2026年9月の脆弱性報告義務開始までに報告体制を、2027年12月の全面施行までに製品設計・適合宣言・技術文書を整備する必要がある。SEMI準拠資産の再利用は文書レベルで一定の効果があるものの、CRAが要求する「実装の証明」には追加対応が不可避であり、再利用率は条項レベルの精査なしに確定できない。最も重大かつ緊急性の高い課題は、①商流・責任主体の法的確定（EU Authorised Representative設置義務を含む）、②製品のAnnex III分類確定（IACS該当によるClass I判定リスク）、③24時間脆弱性報告の実運用体制構築の3点であり、これらがロードマップ全体の前提条件となる。コスト試算は楽観・基準・悲観の3シナリオで提示し、5年間継続運用コストを含めた総費用で経営判断すべきである。

## Research Question（調査の問い）

SEMI規格を遵守する日本の半導体装置ソフトウェア企業が、EU CRAに低コストかつ確実に準拠するための段階的ロードマップと技術戦略はどうあるべきか。商流・責任主体・製品分類・SEMI資産再利用性・コスト構造を統合的に評価し、経営層への説明と現場への指示にそのまま使える形式で策定する。

---

## Findings（主要な発見）

### Finding 1: CRA適用タイムラインと施行の段階構造

_...（全544行。詳細は[統合レビューの全文](./steps/06-integration-review-claude-opus-4.6.md)を参照）_

---

## Trust Summary（信頼性サマリー）

### Validation Result（検証結果）: **PARTIAL**

| 指標 | 値 |
|------|-----|
| 総 Claim（主張）数 | 67 |
| Evidence（根拠）なし | 3 |
| Source（情報源）なし | 9 |
| Confidence（確信度）なし | 0 |

### Confidence Distribution（確信度分布）

| Level（レベル） | 件数 |
|-------|------|
| High（高） | 40 |
| Medium（中） | 25 |
| Low（低） | 2 |

### Source Reliability（情報源の信頼性分布）

| Tier（階層） | 件数 | 説明 |
|------|------|------|
| Tier 1（公式） | 53 | 公式文書・法令・政府機関・標準化団体 |
| Tier 2（高信頼） | 5 | 企業公式・研究機関・学術論文 |
| Tier 3（参考） | 1 | 技術ブログ・専門メディア・業界記事 |
| Tier 4（コミュニティ） | 8 | フォーラム・コミュニティ・SNS |

一次情報（Primary Source）: 57件 / 二次情報: 10件

### Confidence 判定基準（確信度の基準）

| Level（レベル） | 基準 |
|-------|------|
| **High（高）** | 一次情報または複数独立ソースで裏付けあり |
| **Medium（中）** | 信頼できるソースあり、ただし補強不足 |
| **Low（低）** | 推測を含む、または情報不足 |

### Validation Rules（検証ルール）

1. すべての Claim（主張）に Evidence（根拠）が付いていること
2. すべての Evidence（根拠）に Source（情報源）が付いていること
3. すべての結論に Confidence（確信度）が付いていること
4. Critic Review（批判的レビュー）が未解決事項をリスト化していること

### 注意事項

- AI生成のため、重要な意思決定には人間による検証を推奨
- Evidence JSON (`.evidence.json`) で機械的な監査が可能
- Validation 結果 (`.validation.json`) でレポートの品質を定量評価

---

_Generated by [AI Research Agent](https://github.com/ledboots624/ai-research-agent) v2.5.0_
