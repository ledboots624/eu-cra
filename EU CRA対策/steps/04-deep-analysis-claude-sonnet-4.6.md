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

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Article 71（発効・施行規定）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **MUST**（期限は法令により固定）

| 期限 | 義務 | 対象ロードマップフェーズ |
|---|---|---|
| **2026年9月** | Article 14 インシデント・脆弱性報告義務 | **Phase 1-2 必達** |
| **2027年12月** | Annex I全要件・DoC・CEマーキング | **Phase 3-4 必達** |

---

## Section 2: フェーズ別導入ロードマップ（Phased Implementation Roadmap）

### 2.1 ロードマップ全体設計の原則

- **Claim**: 本ロードマップは「法的リスクの時系列的除去」を最優先原則とし、①先行施行される報告義務への対応を最初の完了目標とし、②既存SEMI資産の再利用を最大化することで新規投資を最小化し、③フェーズ間の依存関係を明示することで、工数の重複と手戻りを防ぐ構造とする。

- **Evidence**: 前ステップ分析では、ENISAインシデント報告（P1優先度）・EU DoC（P1）・SBOM（P1）の3項目が「法的ペナルティ直結ギャップ」と評価されており、この優先度順がフェーズ設計の根拠となる。

- **Source**: [unknown] 前ステップ deep-analysis（本調査セッション内分析）(2026-03-17) — primary_source: false
- **Confidence**: medium（工数推定は業界標準プロジェクト規模に基づく推論）

---

### Phase 0: 法的基盤確立フェーズ（Legal Foundation Phase）
**期間**: 月1〜2（2ヶ月）  
**目標**: 製品分類の法的確定と、全フェーズの前提となる組織基盤の構築  
**総工数概算**: **15〜25人日**

#### 2.2 Phase 0 タスク詳細

**タスク P0-1: 製品スコープ・分類確定（最優先）**

- **Claim**: CRA適用開始前に製品がDefault Category・Class I・Class IIのいずれに該当するかを確定することが最重要の初期アクションであり、この判定が第三者認証要否（数百万円の費用差）と適合宣言手法（Module A/B/C）を決定する。

- **Evidence**:
  - **Default Category（自己宣言Module A適用可）**: Annex IIIに列挙されないすべての製品。多くの半導体装置制御ソフトウェアはここに該当すると推定（**推測**）。
  - **Class I（第三者関与推奨）**: Annex III, Part I列挙品目。ID管理ソフトウェア、VPN製品、産業用オートメーション・制御システム（IACS）向け製品が含まれる可能性がある。
  - **Class II（第三者認証必須）**: Annex III, Part II列挙品目。産業用制御システムやHSM等の限定的なカテゴリ。
  - **判定作業**: Annex III照合は法務・技術の共同作業で3〜5人日、外部法律顧問による確認に別途10〜20人日を推奨。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Annex III](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Source（解説）**: [industry_report/tier2] [ENISA Product Classification Guidance under CRA](https://www.enisa.europa.eu/topics/cybersecurity-policy/cyber-resilience-act) (2026-03-17) — primary_source: false
- **Confidence**: high（法令根拠）、medium（実製品の分類判断）
- **Requirement Level**: **MUST**（DoC前提条件）

**タスク P0-2: CRA対応プロジェクト体制構築**

- **Claim**: CRA対応を横断的に推進する「CRA対応オーナー（PSIRT兼任可）」を任命し、責任主体・意思決定経路・外部連携（EU法務顧問・認定機関）を明確化することが、フェーズ全体の実行速度を決定する。

- **Evidence**: PSIRT（Product Security Incident Response Team）は後のPhase 2でインシデント報告義務対応に必須であり、Phase 0から並行して立ち上げることで工数の重複を防げる。FIRST PSIRT Services Framework v1.1が実装指針として参照可能。

- **Source**: [industry_report/tier2] [FIRST PSIRT Services Framework v1.1](https://www.first.org/standards/frameworks/psirts/FIRST_PSIRT_Services_Framework_v1.1.pdf) (2026-03-17) — primary_source: true
- **Confidence**: high
- **工数概算**: 体制設計・役割定義・対外窓口設定に5〜10人日

| P0タスク | 工数（人日） | 依存関係 | 優先度 |
|---|---|---|---|
| P0-1: 製品分類確定（Annex III照合） | 15〜25 | なし（最初期） | **P1** |
| P0-2: CRA対応体制・PSIRT設立 | 5〜10 | なし（並行可） | **P1** |
| P0-3: ギャップ分析（前分析結果の内部確認） | 5〜10 | P0-1完了後 | **P2** |
| **Phase 0 合計** | **25〜45** | | |

---

### Phase 1: 報告義務先行対応フェーズ（Incident Reporting Priority Phase）
**期間**: 月3〜6（4ヶ月）  
**目標**: 2026年9月施行の報告義務（Article 14）への確実な対応完了  
**総工数概算**: **40〜70人日**  
**⚠️ 期限クリティカル**: 2026年9月11日までに完了必須

#### 2.3 Phase 1 タスク詳細

**タスク P1-1: ENISAインシデント報告プロセス設計・実装**

- **Claim**: Article 14に基づく24時間早期警告・72時間通知・最終報告の3段階プロセスを、ENISAのSingle Reporting Platform（SRP）経由で実行できる運用手順書・テンプレートセットを整備することが本フェーズの核心タスクである。

- **Evidence**:
  - **報告対象トリガー**: 「悪用が確認された脆弱性（actively exploited vulnerability）」かつ「重大なインシデント（severe incident）」の両条件を満たすケース
  - **報告先経路**: ENISAのSingle Reporting Platform（SRP）を通じた国別CSIRT（Computer Security Incident Response Team）への報告
  - **24時間早期警告内容**: インシデントの性質・影響製品・暫定情報（完全な情報でなくてよい）
  - **72時間通知内容**: インシデント影響範囲・暫定緩和策・製品バージョン特定
  - **最終報告（72h通知後1ヶ月）**: 根本原因・修正策・再発防止策

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Article 14](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Source**: [official_document/tier1] [ENISA Single Reporting Platform (SRP)](https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp) (2026-03-17) — primary_source: true
- **Confidence**: high（法令根拠）、medium（SRP運用細部は委任法令で詳細化予定）
- **Requirement Level**: **MUST**（2026年9月施行）

```
報告フロー（最小実装）:
[検知T0] → 4h: 内部トリアージ → 24h: SRP/CSIRT早期警告 
                                  → 72h: 詳細通知 → 1ヶ月: 最終報告
```

**タスク P1-2: VDP（脆弱性開示ポリシー）公開**

- **Claim**: Article 13(6)が要求する脆弱性報告受付窓口の公開は、`security.txt（RFC 9116準拠）+ 専用メールアドレス + 公開VDPページ` の3点セットで最短実装できる。これは工数最小（5〜10人日）で法令要件を充足できる高コスト効率の施策である。

- **Evidence**:
  - **RFC 9116 security.txt**: ウェブサイトの `/.well-known/security.txt` に連絡先・ポリシーURL・PGP公開鍵を記載する業界標準。CISAも推奨する実装方法。
  - **VDPページ最小内容**: 報告受付メール、応答SLA（例：5営業日以内に受領確認）、修正・開示のタイムライン方針
  - **言語**: 英語での窓口整備必須（EU市場向け）。日本語併記は任意。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Article 13(6)](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Source**: [official_document/tier1] [RFC 9116 – A File Format to Aid in Security Vulnerability Disclosure](https://www.rfc-editor.org/rfc/rfc9116) (2026-03-17) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **MUST**（Article 13(6)）

| P1タスク | 工数（人日） | 依存関係 | 優先度 |
|---|---|---|---|
| P1-1: インシデント報告フロー設計・テンプレート作成 | 15〜25 | P0-2（PSIRT体制） | **P1** |
| P1-2: CSIRT登録・SRP接続テスト | 5〜10 | P1-1 | **P1** |
| P1-3: インシデント対応ドリル（模擬訓練） | 5〜10 | P1-2 | **P1** |
| P1-4: VDP公開（security.txt + VDPページ） | 5〜10 | なし（並行可） | **P1** |
| P1-5: CVE運用方針確定（Root CNA連携vs自社CNA） | 5〜10 | P0-2 | **P2** |
| **Phase 1 合計** | **35〜65** | | |

---

### Phase 2: SBOM基盤構築フェーズ（SBOM Infrastructure Phase）
**期間**: 月4〜8（5ヶ月）  
**目標**: 機械可読SBOMの継続的生成・管理基盤の確立  
**総工数概算**: **35〜60人日**

#### 2.4 Phase 2 タスク詳細

**タスク P2-1: SBOM生成パイプライン構築**

- **Claim**: CRAが要求する「機械可読SBOM（commonly used and machine-readable format）」の最小コスト実装は、Syftによる自動生成をCIパイプラインに組み込み、CycloneDX JSON形式を標準出力とすることで達成できる。SEMI E188の既存Software Inventoryは初期投入データとして活用し、段階的に自動化する。

- **Evidence**:
  - **SBOM最低フィールドセット（CRA-Min）**: `doc_format, spec_version, document_id, timestamp, product_name, product_version, component_name, component_version, supplier, hash/checksum, license, dependency_ref, depends_on`（前ステップ技術戦略分析より）
  - **Syft**: CycloneDX/SPDX両フォーマット出力対応、CI/CDパイプライン組込み実績が豊富なOSSツール
  - **E188 Software Inventory活用**: 既存Excel/CSV形式のインベントリをCycloneDX変換する初期移行作業は5〜10人日で実施可能（前ステップ推計）

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Annex I Part II](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Source**: [industry_report/tier2] [Syft README（Anchore）](https://github.com/anchore/syft/blob/main/README.md) (2026-03-17) — primary_source: true
- **Confidence**: high（法令）、medium（工数推計）
- **Requirement Level**: **MUST**

**タスク P2-2: 脆弱性継続照合基盤**

- **Claim**: SBOMを生成するだけでなく、CRA Annex I Part IIが要求する「継続的な脆弱性管理」を実現するには、SBOM+脆弱性DBの継続照合（Grype/OSV-Scanner）とDependency-Trackによる長期管理基盤が必要である。

- **Evidence**: Dependency-Trackは生成されたSBOMを継続的に取り込み、NVD・OSVデータベースと照合して新規CVEの発生を自動検出する。これにより「出荷後に発覚した脆弱性への対応」という5年間の継続義務を、人的コストを最小化しながら実現できる。

- **Source**: [industry_report/tier2] [Dependency-Track README（OWASP）](https://github.com/DependencyTrack/dependency-track/blob/master/README.md) (2026-03-17) — primary_source: true
- **Source**: [industry_report/tier2] [Grype README（Anchore）](https://github.com/anchore/grype/blob/main/README.md) (2026-03-17) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **MUST**（継続管理）、**SHOULD**（特定ツール選定）

| P2タスク | 工数（人日） | 依存関係 | 優先度 |
|---|---|---|---|
| P2-1: E188インベントリのCycloneDX変換 | 5〜10 | P0-1（製品スコープ確定） | **P1** |
| P2-2: Syft自動生成パイプライン構築 | 15〜20 | P2-1 | **P1** |
| P2-3: Grype/OSV-Scanner脆弱性スキャン統合 | 10〜15 | P2-2 | **P1** |
| P2-4: Dependency-Track環境構築・SBOM取込み | 10〜15 | P2-3 | **P2** |
| P2-5: SBOM版管理・提供プロセス策定 | 5〜10 | P2-2 | **P2** |
| **Phase 2 合計** | **45〜70** | | |

---

### Phase 3: 製品設計適合フェーズ（Product Design Conformity Phase）
**期間**: 月6〜14（9ヶ月）  
**目標**: CRA Annex I Part I（製品設計要件）の不足ギャップを修正し、技術文書（Annex V）を整備  
**総工数概算**: **60〜120人日**

#### 2.5 Phase 3 タスク詳細

**タスク P3-1: SEMI再利用資産の技術文書化（Annex V変換）**

- **Claim**: CRA Annex V（技術文書）の要求事項に対し、既存のSEMI E187/E188準拠文書を再利用・変換することで、技術文書整備の約60〜70%を既存資産でカバーできる。この変換作業に集中投資することが、製品設計対応における最大のコスト削減効果をもたらす。

- **Evidence**: 前ステップ分析の「高再利用可能資産」テーブルが根拠：E187 §3.3/§3.4/§3.5/§3.1、E188 §4.1-4.5が直接転用可能。追加作業は英語化・EU法令フォーマット変換・製品識別情報の追記が主体。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Annex V（技術文書要件）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: medium（SEMI実装水準は企業による差異あり）
- **Requirement Level**: **MUST**

**タスク P3-2: ギャップ項目の技術実装**

- **Claim**: CRA要件のうちSEMI資産で充足できない「ギャップ項目」（セキュリティイベントログの拡充・データ最小化設計・インシデント封じ込め機能・暗号化通信の完全化）については、製品ロードマップへの組み込みによる段階的修正が現実的であり、一括対応より優先順位付きの分割実装が中小企業には適している。

- **Evidence**: ギャップ分析（前ステップ）では、製品設計ギャップのうちData Minimization（個人データ不処理の場合は影響限定）とRemovabilityは半導体装置制御ソフトウェアにおいて実質影響が小さい可能性があり、製品特性に応じたスコープ調整が可能。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Annex I Part I §8, §9](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: medium
- **Requirement Level**: **MUST**（ログ拡充）、medium（データ最小化：製品特性依存）

| P3タスク | 工数（人日） | 依存関係 | 優先度 |
|---|---|---|---|
| P3-1: 技術文書Annex V骨格作成 | 10〜20 | P0-1（製品分類確定） | **P1** |
| P3-2: SEMI資産の英語化・Annex V形式変換 | 15〜25 | P3-1 | **P1** |
| P3-3: セキュリティイベントログ機能拡張（開発） | 20〜40 | P3-1 | **P2** |
| P3-4: 暗号化通信・保存データ保護の完全化 | 15〜30 | P3-1 | **P2** |
| P3-5: サポートライフサイクルポリシー策定・公開 | 5〜10 | P0-2 | **P2** |
| P3-6: 技術文書の内部レビュー・承認 | 5〜10 | P3-2完了後 | **P2** |
| **Phase 3 合計** | **70〜135** | | |

---

### Phase 4: 適合宣言・審査準備フェーズ（Conformity Declaration Phase）
**期間**: 月13〜18（6ヶ月）  
**目標**: EU DoC（Declaration of Conformity）の発行とCEマーキングによる市場適合完了  
**総工数概算**: **40〜80人日**  
**⚠️ 期限**: 2027年12月11日完全適用前までに完了

#### 2.6 Phase 4 タスク詳細

**タスク P4-1: DoC（適合宣言書）作成・法務審査**

- **Claim**: Default Category製品（Module A：自己宣言）の場合、DoC作成は第三者認証なしに実施可能であり、Annex IV規定フォームへの記載と法務確認を経て発行できる。DoC発行コストの大部分は「技術文書の完全性確認」であり、Phase 3が完了していれば追加工数は限定的である。

- **Evidence**:
  - **Annex IV必須記載事項**: 製造者名・住所・連絡先、製品の説明（型式・バッチ番号等）、適用CRA規定のリスト、適用調和規格のリスト（EN 18031等）、EU公用語での発行、権限者署名・日付
  - **Module A（自己宣言）**: Default Categoryに適用。第三者の適合性評価機関関与不要。
  - **Class I製品（追加注意）**: 調和規格（EN 18031）を適用するか、第三者機関によるレビューが選択肢となる。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Article 20, Annex IV, Annex VIII（適合評価手順）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: high（Module A適用がDefault Categoryに限定される点に注意）
- **Requirement Level**: **MUST**

| P4タスク | 工数（人日） | 依存関係 | 優先度 |
|---|---|---|---|
| P4-1: DoCドラフト作成（Annex IV形式） | 10〜20 | Phase 3完了 | **P1** |
| P4-2: DoC外部法務レビュー（EU法律顧問） | 10〜20 | P4-1 | **P1** |
| P4-3: CEマーキング貼付手順整備 | 3〜5 | P4-2 | **P1** |
| P4-4: 技術文書の最終完全性チェック | 5〜10 | P3完了 | **P1** |
| P4-5: 市場監督当局対応手順整備 | 5〜10 | P4-2 | **P2** |
| P4-6: 定期レビュープロセス確立（年次更新） | 5〜10 | P4-2 | **P2** |
| **Phase 4 合計** | **38〜75** | | |

---

### 2.7 ロードマップ全体サマリー（18ヶ月・総工数概算）

```
タイムライン（月単位）:
月 1  2  3  4  5  6  7  8  9  10 11 12 13 14 15 16 17 18
|━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━|
Phase 0: 法的基盤         [━━━━━━━━]
Phase 1: 報告義務     [━━━━━━━━━━━━━━━]  ← 2026年9月施行期限
Phase 2: SBOM基盤        [━━━━━━━━━━━━━━━━━━━━]
Phase 3: 製品設計             [━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━]
Phase 4: 適合宣言                                  [━━━━━━━━━━━━━━]
                                                              ↑2027年12月期限
```

| フェーズ | 工数概算（人日） | 外部費用概算（参考） |
|---|---|---|
| Phase 0: 法的基盤確立 | 25〜45 | 法務顧問費用：50〜200万円 |
| Phase 1: 報告義務対応 | 35〜65 | CSIRT接続・ツール費用：最小50万円 |
| Phase 2: SBOM基盤構築 | 45〜70 | OSSツール中心：10〜30万円 |
| Phase 3: 製品設計適合 | 70〜135 | 開発費：内部工数中心 |
| Phase 4: 適合宣言 | 38〜75 | EU法務レビュー：100〜300万円 |
| **合計** | **213〜390人日** | **約210〜580万円（外部費用）** |

- **Confidence**: low〜medium（工数は中堅規模・既存SEMI準拠企業を仮定した参考値。実際の規模・製品複雑度・内部体制により大幅に変動する）
- **Source**: [unknown] 著者のロードマップ設計に基づく工数モデル（業界参考値）(2026-03-17) — primary_source: false

---

## Section 3: 関連規格重複活用によるコスト削減（Standards Overlap Cost Reduction Analysis）

### 3.1 IEC 62443との重複活用

- **Claim**: IEC 62443（産業用オートメーション・制御システムのセキュリティ）は、CRA Annex I要件と最も重複度が高い関連規格であり、特にIEC 62443-4-1（製品セキュリティ開発ライフサイクル）とIEC 62443-4-2（コンポーネントセキュリティ要件）は、CRAの製品設計・開発プロセス要件に直接対応するため、既存IEC 62443準拠資産がある場合は大幅なコスト削減が可能である。

- **Evidence**:

| IEC 62443条項 | 対応するCRA要件 | 重複活用の具体内容 | コスト削減推定 |
|---|---|---|---|
| **62443-4-1** SR-1〜SR-8（セキュア開発プロセス） | CRA Annex I Part I（設計要件全般） | SSDLエビデンスをAnnex V技術文書に転用 | **30〜50%削減**（技術文書作成工数） |
| **62443-4-2** SAR 3.1〜3.14（アクセス制御・ログ等） | CRA Annex I Part I §7,§8（アクセス制御・ログ） | 既存テスト結果・設計文書を再利用 | 20〜40%削減 |
| **62443-2-1**（セキュリティ管理システム） | CRA脆弱性管理プロセス（Annex I Part II） | 脆弱性管理プロセスの相互認証可能性 | 10〜20%削減 |
| **62443-3-3**（システムセキュリティ要件） | CRA Annex I Part I（effect mitigation等） | SRおよびセキュリティレベル評価の再利用 | 20〜30%削減 |

- **Source**: [official_document/tier1] [IEC 62443 Series（産業用セキュリティ標準）](https://webstore.iec.ch/en/publication/33615) (2026-03-17) — primary_source: true
- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Recital 35（調和規格・標準の活用）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: medium（IEC 62443の詳細条項は有償文書。重複度の数値は業界解説参照）

**CRA適合評価でのIEC 62443の位置づけ（重要注意点）**

- **Claim**: IEC 62443は現時点ではCRAの「調和規格（Harmonised Standards）」として正式指定されていないが、CRA Recital 35は「既存のセキュリティ規格・標準が技術文書の根拠として活用可能」と認めており、準拠証跡の補強材料として使用できる。調和規格指定後は「準拠推定（Presumption of Conformity）」の効果が生じ、適合評価コストが大幅に低減される可能性がある。

- **Evidence**: ENISAの調和規格候補リストにIEC 62443-4-1が検討対象として含まれている旨の業界報告あり（**推測・要確認**）。EN 18031（ヨーロッパ規格）はすでにCRA適合評価の参照規格として位置づけられている。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Recital 35, Article 19（調和規格）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Source（参考）**: [industry_report/tier3] [ENISA Standards and Certification under CRA](https://www.enisa.europa.eu/topics/cybersecurity-policy/cyber-resilience-act) (2026-03-17) — primary_source: false
- **Confidence**: medium（調和規格指定の進捗は2026年3月時点で未確定）

---

### 3.2 ISO/IEC 27001との重複活用

- **Claim**: ISO/IEC 27001（情報セキュリティマネジメントシステム）は、CRAの脆弱性管理プロセス・インシデント対応・サプライチェーン管理要件と組織的側面で重複しており、既存ISO 27001認証保有企業は組織プロセスの構築工数を**30〜50%削減**できると推定される。

- **Evidence**:

| ISO 27001条項 | 対応するCRA要件 | 重複活用の具体内容 |
|---|---|---|
| **A.12.6**（技術的脆弱性の管理） | CRA Annex I Part II（脆弱性管理） | 脆弱性管理プロセスがほぼ直接対応 |
| **A.16**（情報セキュリティインシデント管理） | CRA Article 14（インシデント報告） | インシデント対応手順書を拡張してSRP報告を追加 |
| **A.15**（サプライヤー関係） | CRA Annex I Part I §11（サプライチェーン透明性） | サプライヤー評価プロセスにSBOM収集を追加 |
| **A.8.29**（開発フェーズのセキュリティテスト） | CRA Annex I Part II §3（定期セキュリティテスト） | セキュリティテスト計画の再利用 |
| **A.5.24**（情報セキュリティインシデント対応計画） | CRA Article 14（対応プロセス） | インシデント対応計画に当局報告ステップを追加 |

- **Source**: [official_document/tier1] [ISO/IEC 27001:2022（情報セキュリティマネジメント要件）](https://www.iso.org/standard/27001) (2026-03-17) — primary_source: true
- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Annex I Part II](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: medium（重複度の定量値は業界参考値）
- **Requirement Level**: **SHOULD**（重複活用はコスト削減手段として推奨）

**ISO 27001未保有企業への推奨**

- **Claim**: ISO 27001を未取得の場合でも、ISO 27001の統制フレームワーク（Annex A統制リスト）をCRA対応のチェックリスト設計の参照モデルとして活用することで、ゼロベース設計より効率的な組織プロセス構築が可能である。認証取得自体はCRA法令では要求されない。

- **Source**: [unknown] 著者の規格活用分析に基づく推論 (2026-03-17) — primary_source: false
- **Confidence**: medium

---

### 3.3 NIST SP 800-218（SSDF）との重複活用

- **Claim**: NIST SP 800-218（Secure Software Development Framework：SSDF）は、CRAが求めるセキュア開発ライフサイクルの実装指針として最も直接的に参照可能な無償フレームワークであり、中小企業がIEC 62443等の高コスト有償規格に依存せずにCRA対応を進める際の代替基盤として活用できる。

- **Evidence**:
  - SSDFの4プラクティスグループ（PO：組織準備、PS：ソフトウェア保護、PW：セキュア開発、RV：脆弱性対応）はCRA Annex I要件に広く対応
  - 無償で公開されており、中小企業のコスト制約に対して最もアクセシブルな標準
  - CRA技術文書においてSSDFへの準拠を記載することで、開発プロセスの証拠補強が可能（**SHOULD**レベルの活用）

- **Source**: [official_document/tier1] [NIST SP 800-218 Secure Software Development Framework（SSDF）v1.1](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-218.pdf) (2026-03-17) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **SHOULD**（SSDF自体はMUST要件ではないが、CRA技術文書補強として有効）

---

### 3.4 規格重複活用の総合コスト削減マトリックス

| 保有規格・基盤 | 削減効果（工数比） | 主な削減対象フェーズ | 条件・注意点 |
|---|---|---|---|
| **SEMI E187/E188準拠済み** | **30〜40%削減**（製品設計技術文書） | Phase 3 | 本稿分析の出発点。既存文書の質・英語化状況依存 |
| **IEC 62443-4-1準拠済み** | **30〜50%削減**（開発プロセス文書） | Phase 3, Phase 4 | 調和規格指定前は証拠補強止まり |
| **ISO/IEC 27001認証保有** | **30〜50%削減**（組織プロセス構築） | Phase 1, Phase 2 | A.12.6/A.16等の統制が既に整備されている場合 |
| **NIST SSDF実践中** | **20〜30%削減**（開発ライフサイクル文書） | Phase 3 | 無償活用可能。中小企業に最適 |
| **複数規格複合保有** | **最大60〜70%削減**（推定） | 全フェーズ | ただし規格間のギャップ調整工数が別途発生 |

- **Confidence**: low〜medium（複合削減率は著者推論。一次情報による検証なし）
- **Source**: [unknown] 著者の規格間重複分析に基づく推論 (2026-03-17) — primary_source: false

---

## Section 4: 中小企業向け最適化戦略（SME Optimization Strategy）

### 4.1 リソース制約下での4原則

**原則1: 「Process-First, Product-Second（プロセス先行）」**

- **Claim**: SEMI E187/E188遵守企業のCRA対応コストの70〜80%は製品の技術的再設計ではなく、プロセス構築と文書整備に集中するべきであり、これが中小企業にとって最もROIが高い投資方針である。

- **Evidence**: 前ステップ分析が示す通り、製品設計領域ではSEMI準拠資産で60〜70%を充足可能だが、報告義務・VDP・DoCはゼロから構築が必要。中小企業は開発リソースより管理・文書リソースが希少なため、外部専門家との分業が有効。

- **Source**: [unknown] 前ステップ分析・著者推論 (2026-03-17) — primary_source: false
- **Confidence**: medium

**原則2: 「OSS-First（OSSツール優先）」**

- **Claim**: SBOM生成・管理・脆弱性照合のツールスタックはすべてOSSで構成可能であり、ライセンスコストゼロで必要な技術基盤を構築できる。商用ツールへの投資はOSS基盤が安定してから段階的に検討するべきである。

- **Evidence**: Syft（SBOM生成）・cyclonedx-cli（変換・検証）・Grype/OSV-Scanner（脆弱性照合）・Dependency-Track（継続管理）のすべてが無償OSSで利用可能。

- **Source**: [industry_report/tier2] [各OSSツールGitHub README参照（前ステップ技術戦略分析）](https://github.com/anchore/syft) (2026-03-17) — primary_source: true
- **Confidence**: high

**原則3: 「Milestone-Driven Priority（期限駆動型優先順位）」**

- **Claim**: 2026年9月（報告義務先行施行）を唯一の硬直的期限として扱い、Phase 1（報告義務対応）とPhase 2の一部（SBOM初期生成）を2026年9月までの必達目標として集中投資する。残りのPhase 3・4は2027年12月に向けて段階的に実施する余裕を確保する。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Article 71](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: high

**原則4: 「Scalable Documentation（スケーラブル文書化）」**

- **Claim**: 技術文書（Annex V）の初版は最小限の必須記載事項のみで作成し、四半期ごとに更新・充実化する「生きた文書」として管理することで、初期構築コストと継続維持コストの両方を最適化できる。

- **Source**: [unknown] 著者の文書管理最適化推論 (2026-03-17) — primary_source: false
- **Confidence**: medium

---

### 4.2 外部専門家活用の費用対効果

- **Claim**: 中小企業においては、EU法務顧問（DoC発行・製品分類確認）と認定コンサルタント（技術文書レビュー）への限定的な外部委託が、全内製よりも総コストを削減できる可能性が高い。自社には「プロセスオーナー」を置き、文書作成の実作業を内製化することで外部費用を最小化する構造が最適である。

- **Evidence**: EU CRAの製品分類誤認（Default CategoryをClass Iと誤判定、またはその逆）は数百万円規模のコスト差を生む。初期の法務確認投資（50〜200万円）は保険コストとして見なすべきである。

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Annex III（製品分類）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: medium（外部費用推定は著者の参考値）

---

### 4.3 リスクシナリオ別対応優先マトリックス

| リスクシナリオ | 罰則規定 | 最大ペナルティ | 対応フェーズ | 軽減策 |
|---|---|---|---|---|
| インシデント報告義務違反 | Article 14 + Article 64 | **最大1,500万ユーロまたは売上高2.5%（高い方）** | **Phase 1**（最優先） | 24h/72h報告フロー整備 |
| CEマーキング未取得でEU市場継続販売 | Article 22 + Article 64 | 最大1,500万ユーロまたは売上高2.5% | Phase 4 | 2027年12月期限前にDoC発行 |
| 技術文書・SBOM未整備 | Annex I Part II + Article 64 | 最大1,000万ユーロまたは売上高1.5% | Phase 2, Phase 3 | SBOM自動生成パイプライン構築 |
| 製品分類誤認による手続き不備 | Article 20 | 上記に準ずる | Phase 0（最重要） | 外部法務による分類確認 |
| 市場監督当局による市場アクセス停止 | Article 54 | EU市場からの排除（金銭罰を超える損害） | 全フェーズ | 計画的なフェーズ実施 |

- **Source**: [official_document/tier1] [Regulation (EU) 2024/2847 Article 64（罰則規定）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence**: high（罰則額は法令により確定）

---

## Section 5: 批評的検証（Critical Assessment）

### 5.1 ロードマップの実現可能性評価

- **Claim**: 本ロードマップの「18ヶ月・213〜390人日」という推計は、SEMI準拠済み・中堅規模（50〜200名）・既存セキュリティ担当者保有を前提とした参考値であり、実際の難易度は以下の要因により大幅に変動しうる。

| 変動要因 | 工数増加方向 | 工数削減方向 |
|---|---|---|
| 製品がClass Iに該当する場合 | +50〜100人日（第三者関与） | — |
| SEMI E187/E188準拠が書面のみの場合 | +30〜60人日（実装ギャップ対応） | — |
| ISO 27001・IEC 62443の既存認証あり | — | ▲30〜70人日 |
| 複数製品ラインへの横展開 | +30〜100人日/製品 | — |
| 専任CRA担当者の不在 | +20〜40人日（学習コスト） | — |
| 委任法令の追加規制（2025〜2027年） | +未定 | — |

- **Source**: [unknown] 著者の工数変動分析（参考値） (2026-03-17) — primary_source: false
- **Confidence**: low（変動係数が高く、個社ごとの実態調査が必要）

### 5.2 日本企業固有の実施障壁

- **Claim**: 日本の半導体装置ソフトウェア製造者がCRA対応を実施する際、技術的課題よりも「組織・言語・欧州規制体制への不慣れ」が最大の実施障壁となりうる（**推測**）。

- **Evidence（間接根拠）**:
  1. **言語障壁**: DoC・技術文書のEU公用語での作成義務。DG CONNECT（EU）はCRA実施に際して英語を含む複数言語での文書提供を要求する。
  2. **EU CSIRT体制の不熟知**: 各EU加盟国のCSIRT連絡先・SRP報告経路の把握には事前準備が必要。ENISA公開の「EU CSIRT Network」一覧の事前確認が必須。
  3. **調和規格の流動性**: 2026〜2027年の委任法令・調和規格指定の変動により、準拠対象仕様が変化しうる。四半期ごとの法令ウォッチが不可欠。
  4. **先行事例の乏しさ**: CRAは2027年12月完全適用前の過渡期にあり、日本企業による完全対応事例は現時点でほぼ存在しない（**未確定・要情報収集**）。

- **Source**: [official_document/tier1] [ENISA CSIRT Network](https://www.enisa.europa.eu/topics/csirts-in-europe/csirt-network) (2026-03-17) — primary_source: true
- **Source**: [official_document/tier1] [European Commission CRA reporting page](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting) (2026-03-17) — primary_source: true
- **Confidence**: medium（言語・組織障壁の実態は調査対象企業の文書化状況により異なる）

---

## Conclusions & Recommendations（結論と提言）

### 優先アクション（前提条件プロフィールへの特化提言）

SEMI E187/E188遵守済みの日本の半導体装置ソフトウェア製造者として、以下の順序でアクションを実施することを推奨する:

1. **【即時実施】製品分類確定（Phase 0-P0-1）**: Annex III照合で製品がDefault Categoryに該当することを確認する。これ一つで適合評価コストが数百万円単位で変わる。外部EU法務顧問への初期投資（50〜200万円）は必須保険として位置づける。

2. **【2026年9月厳守】報告義務インフラ整備（Phase 1）**: 24h/72h報告フロー・VDP公開・PSIRT体制の3点を先行完成させる。これは技術的実装よりプロセス・テンプレート整備が中心であり、35〜65人日で達成可能。

3. **【並行実施】E188インベントリのSBOM化（Phase 2-P2-1）**: 既存Software InventoryをSyftでCycloneDX形式に変換する。5〜10人日の追加作業で機械可読SBOM要件の大部分を充足でき、コストパフォーマンスが最高の施策。

4. **【継続投資】技術文書のAnnex V形式化（Phase 3）**: SEMI資産の英語化・EU法令フォーマット変換は段階的に実施し、2027年12月期限に向けて着実に完成度を高める。

5. **【規格重複活用】IEC 62443-4-1 / ISO 27001 / NIST SSDFの証拠補強活用**: これらへの準拠資産がある場合は積極的にAnnex V技術文書に組み込み、追加開発工数を削減する。現時点では調和規格正式指定を待つ必要はなく、「参照規格」として記載可能。

- **Confidence（全体）**: medium（委任法令詳細・調和規格指定・個社実態により変動余地が高い）
- **法令ウォッチ推奨**: ENISA/European Commissionの公式チャンネルで四半期ごとに委任法令・調和規格指定の最新情報を確認すること。
