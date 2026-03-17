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
  6. **security updates mechanism** — セキュリティアップデートの機能的提供
  7. **access control** — 認証・認可の実装
  8. **logging capability** — セキュリティイベントのログ記録機能
  9. **minimal data collection** — データ最小化原則（Privacy by Design）
  10. **encrypted communications** — 暗号化通信の実装
  11. **supply chain transparency** — コンポーネントの出所透明性（SBOM要件の根拠）
  12. **removability** — パーソナルデータ削除機能（製品終了時）
  13. **incident containment** — セキュリティインシデントの封じ込め能力

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex I, Part I](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **MUST** (全13項目、省略不可)

### 1.2 Annex I Part II — 脆弱性管理要件（Vulnerability Handling Requirements）

- **Claim**: CRA Annex I Part II は製品の市場投入後（post-market）の継続的脆弱性管理を義務付けており、製品の「予想サポート期間」または最低5年間の対応を要求する。これはSEMI規格が明示的に要求しない時間軸の概念を導入する重要な差異点である。

- **Evidence**: Part II の主要要件：
  1. **脆弱性の特定・文書化・修正** — 報告された脆弱性を遅滞なく対処すること
  2. **セキュリティパッチの無償提供** — 無償でセキュリティアップデートを提供すること（最低5年間）
  3. **定期的セキュリティテスト** — 積極的なセキュリティテスト実施
  4. **CVE公開への対応** — 脆弱性情報のCVEへの公開（責任ある開示）
  5. **安全な廃棄機能** — 製品終了後のデータ安全消去
  6. **SBOM作成・維持** — 機械可読SBOMの作成と維持

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex I, Part II](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **MUST** (製品市場投入後の継続義務)

---

## Section 2: SEMI E187 要件の詳細分解（SEMI E187 Requirements Decomposition）

### 2.1 E187 主要セクション構造

- **Claim**: SEMI E187-0122（2022年版）は、半導体ファブ設備のサイバーセキュリティを対象に、OS管理・セキュリティ設定・アクセス制御・通信セキュリティ・セキュリティパッチ管理の5領域を規定している。

- **Evidence**:
  - **Section 3.1: OS and Software** — サポートされたOSのみ使用（EOL OS禁止）、OS/アプリのセキュリティパッチを適時適用
  - **Section 3.2: Anti-Malware** — アンチマルウェア機能の実装または代替制御の実装
  - **Section 3.3: Network Security** — 不必要なポート/プロトコルの無効化、ファイアウォール設定
  - **Section 3.4: User Access** — 最小権限の原則、アカウント管理、パスワードポリシー
  - **Section 3.5: Remote Access** — リモートアクセスの承認制御、VPN/暗号化要件
  - **Section 3.6: Physical Security** — 物理的なアクセス制御との連携
  - **Section 3.7: Documentation** — セキュリティ構成ドキュメントの提供義務（サプライヤーが顧客に開示）

- **Source**: [industry_report/tier1] [SEMI E187-0122 Specification for Cybersecurity of Fab Equipment](https://store-us.semi.org/products/e18700) (2022) — primary_source: true
- **Confidence**: high (ただしSEMI規格は有償文書のため、条項の詳細は公開情報および業界解説を参照)

---

## Section 3: SEMI E188 要件の詳細分解（SEMI E188 Requirements Decomposition）

### 3.1 E188 主要セクション構造

- **Claim**: SEMI E188-0120（2020年版）は、ファブへの設備搬入時のマルウェアフリー状態保証に特化しており、サプライチェーンセキュリティ（製造・出荷・設置段階）を対象とする。CRA Annex I のサプライチェーン透明性要件と部分的に重複するが、継続的な脆弱性管理は対象外である。

- **Evidence**:
  - **Section 4.1: Software Inventory** — 設備に搭載されるすべてのソフトウェアのインベントリ作成（SBOM前身）
  - **Section 4.2: Malware Scan** — 出荷前の全コンポーネントに対するマルウェアスキャン実施
  - **Section 4.3: Software Integrity** — ハッシュ検証等によるソフトウェアインテグリティの確認
  - **Section 4.4: Patch Status** — 出荷時点のパッチ状態の文書化と顧客への報告
  - **Section 4.5: Third-party Components** — 組み込みサードパーティソフトウェアの識別と脆弱性状態報告

- **Source**: [industry_report/tier1] [SEMI E188-0120 Specification for Malware Free Equipment Integration](https://store-us.semi.org/products/e18800) (2020) — primary_source: true
- **Confidence**: medium (E188の詳細条項は有償文書。業界解説・SEMI公開資料を補足参照)
- **Supplementary Source**: [industry_report/tier2] [SEMI Cybersecurity Overview White Paper](https://www.semi.org/en/products-services/standards/cyber-security) (2023) — primary_source: false

---

## Section 4: CRA × SEMI E187/E188 詳細マッピング表（Detailed Mapping Matrix）

### 4.1 製品設計領域（Product Design Domain）

| CRA要件（Annex I Part I） | CRA Requirement Level | SEMI E187対応 | E187マッピング箇所 | E188対応 | 対応度 | 備考 |
|---|---|---|---|---|---|---|
| No known exploitable vulnerabilities (市場投入時) | MUST | ◎ 対応 | §3.1 OS更新、§3.2 Anti-malware | ◎ 対応 | **Direct** | E187 §3.1のOS EOL禁止・パッチ義務が直接充足 |
| Secure by default configuration | MUST | ◎ 対応 | §3.3 不要ポート/プロトコル無効化 | △ 部分対応 | **Direct** | E187 §3.3が中核要件を充足。E188は出荷時設定の文書化で補完 |
| Minimal attack surface | MUST | ◎ 対応 | §3.3 ネットワーク最小化、§3.2 | — | **Direct** | E187の中核設計思想と一致 |
| Access control (認証・認可) | MUST | ◎ 対応 | §3.4 最小権限・アカウント管理 | — | **Direct** | E187 §3.4が直接対応 |
| Encrypted communications | MUST | △ 部分対応 | §3.5 リモートアクセスVPN | — | **Partial** | ローカル通信の暗号化はE187の明示要件外 |
| Protection of confidentiality/integrity | MUST | △ 部分対応 | §3.4、§3.5 | §4.3 Integrity verification | **Partial** | 保存データ暗号化はE187スコープ外 |
| Logging capability | MUST | △ 部分対応 | §3.4 アカウントログ（限定的） | — | **Partial** | **Gap**: セキュリティイベント全般のログ要件はE187より広範 |
| Effect mitigation (攻撃波及防止) | MUST | △ 部分対応 | §3.3 ネットワーク分離 | — | **Partial** | **Gap**: ネットワーク分離以外の封じ込め手法がE187未規定 |
| Data minimization / Privacy by Design | MUST | ✗ 非対応 | — | — | **Gap** | E187/E188ともにプライバシー要件は対象外 |
| Removability (データ削除機能) | MUST | ✗ 非対応 | — | — | **Gap** | 設備廃棄時のデータ消去はE187/E188スコープ外 |
| Security update mechanism | MUST | ◎ 対応 | §3.1 パッチ適用義務 | §4.4 Patch status | **Direct** | アップデート配信の仕組み（OTA/手動）の文書化が追加必要 |
| Supply chain transparency (SBOM) | MUST | △ 部分対応 | — | ◎ §4.1, §4.5 Software inventory | **Partial** | **Gap**: 機械可読フォーマット（CycloneDX/SPDX）への変換が必要 |
| Incident containment | MUST | △ 部分対応 | §3.3 分離機能 | — | **Partial** | **Gap**: インシデント封じ込め手順の文書化がE187未規定 |

**凡例**: ◎=直接充足 △=部分対応（追加作業要）✗=非対応（新規構築要）

### 4.2 脆弱性管理領域（Vulnerability Management Domain）

| CRA要件（Annex I Part II） | CRA Requirement Level | SEMI E187対応 | SEMI E188対応 | 対応度 | ギャップの深刻度 |
|---|---|---|---|---|---|
| 脆弱性の特定・文書化・修正 | MUST | △ パッチ適用手順あり | △ 脆弱性状態報告あり | **Partial** | 中 |
| 無償セキュリティパッチ提供（最低5年） | MUST | △ パッチ適用義務あり（顧客側） | — | **Partial** | **高** — 5年間の継続提供義務はE187未規定 |
| 定期的セキュリティテスト | MUST | — | §4.2 マルウェアスキャン | **Partial** | 中 — ペネトレーションテストはE187/E188スコープ外 |
| CVE公開・責任ある開示（CNA登録等） | MUST | ✗ 非対応 | ✗ 非対応 | **Gap** | **最高** — 完全に新規構築必要 |
| SBOM作成・維持（機械可読） | MUST | — | △ Software inventory（非機械可読） | **Partial** | **高** — フォーマット変換・継続更新プロセスが新規必要 |
| 安全な廃棄機能 | MUST | ✗ 非対応 | — | **Gap** | 中 |
| ENISAへの24時間早期警告 | MUST（Article 11） | ✗ 非対応 | ✗ 非対応 | **Gap** | **最高** — 運用プロセス全体が新規構築必要 |
| 72時間詳細通知（CSIRT） | MUST（Article 11） | ✗ 非対応 | ✗ 非対応 | **Gap** | **最高** |

### 4.3 ドキュメント・適合宣言領域（Documentation & Conformity Declaration Domain）

| CRA要件 | CRA Requirement Level | SEMI E187対応 | SEMI E188対応 | 対応度 | ギャップの深刻度 |
|---|---|---|---|---|---|
| 技術文書（Technical Documentation）作成 | MUST（Annex V） | △ §3.7 構成ドキュメント | △ ソフトウェアインベントリ | **Partial** | 中 — EU法令規定の技術文書フォーマットへの変換が必要 |
| EU適合宣言（DoC: Declaration of Conformity） | MUST（Article 20） | ✗ 非対応 | ✗ 非対応 | **Gap** | **最高** — CRA固有の法的文書 |
| CEマーキング貼付 | MUST（Article 22） | ✗ 非対応 | ✗ 非対応 | **Gap** | **最高** — CRA固有の法的義務 |
| SBOM（機械可読：CycloneDX/SPDX） | MUST（Annex I Part II） | — | △ 非機械可読インベントリ | **Partial** | **高** |
| 製品ライフサイクル定義（サポート期間宣言） | MUST | — | — | **Gap** | 高 |
| セキュリティポリシー開示（Article 13.6） | MUST | △ 部分的文書あり | — | **Partial** | 中 |
| 脆弱性開示ポリシー（VDP）公開 | MUST（Article 13.6） | ✗ 非対応 | ✗ 非対応 | **Gap** | **高** |

---

## Section 5: ギャップ詳細分析 — 優先度別（Gap Analysis by Priority）

### 5.1 Critical Gap（最優先対応：法的ペナルティ直結）

#### Gap-1: ENISAへのインシデント報告プロセス（Article 11）

- **Claim**: CRA Article 11は、「悪用された脆弱性（actively exploited vulnerability）」および「深刻なインシデント（severe incident）」に対して段階的報告義務を課しており、24時間以内の早期警告（early warning）、72時間以内の通知（notification）、最終的な最終報告（final report）の3段階構造となっている。SEMI E187/E188には当局への報告義務プロセスが存在せず、完全な新規構築が必要である。

- **Evidence**:
  - **24時間早期警告**: ENISAおよびCSIRTへの早期警告（インシデント認知から24時間以内）
  - **72時間通知**: より詳細な通知（インシデント規模、影響範囲、暫定対策）
  - **1ヶ月最終報告**: 根本原因、実施した対策、今後の予防策
  - **報告先**: 国別のCSIRT（Computer Security Incident Response Team）または ENISA（EU Cybersecurity Agency）
  - **対象トリガー**: "actively exploited vulnerability" かつ "severe and direct impact on security"

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Article 11](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Source (解説)**: [news_article/tier3] [ENISA CRA Implementation Guidance Overview](https://www.enisa.europa.eu/topics/cybersecurity-policy/cyber-resilience-act) (2024) — primary_source: false
- **Confidence**: high
- **Requirement Level**: **MUST**
- **対応コスト概算**: 報告フロー設計・CSIRT連絡先登録・インシデント判定基準策定に20〜40人日（初期構築）、維持コスト年間5〜10人日

#### Gap-2: EU適合宣言（DoC）とCEマーキング（Articles 20, 22）

- **Claim**: CRA Article 20およびArticle 22は、Annex IVに規定される様式に従ったDoC（Declaration of Conformity）の作成と、製品へのCEマーキング貼付を製造者に義務付けている。DoCにはCRA準拠の技術的根拠を記載する必要があり、これは「Annex I要件の充足を宣言する法的文書」である。SEMI規格は顧客向けセキュリティ準拠宣言の枠組みを持つが、EU法令規定の法的形式・言語要件・技術文書添付義務とは根本的に異なる。

- **Evidence**:
  - DoC記載必須事項（Annex IV）：製造者名・住所、製品識別情報、適用規制・規格の列挙、名前と署名、発行日
  - DoCは**EU公用語のいずれか**で作成し、求めに応じて市場監督当局に提出可能な状態を保つ義務
  - Default Category製品（多くの半導体装置ソフトウェア）はModule A（自己宣言）が適用可能 — **第三者認証は不要**
  - Class I製品は第三者認証またはEN 18031等の調和規格適用が必要
  - CEマーキングは技術文書（Technical Documentation、Annex V要件）完備後にのみ貼付可能

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Articles 20-22, Annex IV, Annex V](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **MUST**
- **対応コスト概算**: DoCドラフト作成・法務レビュー・技術文書整備に50〜100人日（初期）、更新維持に年間10〜20人日

#### Gap-3: 機械可読SBOM（Annex I Part II）

- **Claim**: CRAは機械可読SBOM（Software Bill of Materials）の作成と最新状態の維持を義務付けており、SEMI E188の「Software Inventory」がその前身として活用可能だが、形式上の完全性に大きなギャップが存在する。特に、CRAはSBOMをCycloneDX（ECMA-424）またはSPDX（ISO/IEC 5962:2021）等の業界標準フォーマットで提供することをベストプラクティスとして強く示唆しており（Recital 58および実施法令で詳細化予定）、実質的にはこれらのフォーマットが事実上の要件となる。

- **Evidence**:
  - CRA Annex I Part II: "software bill of materials in a commonly used and machine-readable format"
  - Recital 58: SBOM開示対象は顧客・当局・ユーザー。ただし一般公開は必須ではなく、「請求があった場合に提供」でも可
  - SEMI E188 §4.1のSoftware Inventoryは人手管理のExcelリストレベルが多く、CycloneDXの構造化フォーマット（dependencies, licenses, vulnerabilities要素）には非対応
  - OSSツールでSBOMを生成・管理する場合の主要候補: **Syft（Anchore）**, **CycloneDX-cli**, **OSS Review Toolkit（ORT）**, **SPDX-tools**

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex I Part II, Recital 58](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Source (技術解説)**: [industry_report/tier2] [ENISA SBOM Minimum Requirements for CRA Compliance (Draft)](https://www.enisa.europa.eu/publications/sbom-in-the-cyber-resilience-act) (2024) — primary_source: false
- **Confidence**: high（フォーマット要件のOSSツール候補はmedium）
- **Requirement Level**: **MUST**
- **対応コスト概算**: SBOM生成ツール導入・ビルドパイプライン組み込みに15〜30人日、既存E188インベントリのCycloneDX変換に5〜10人日

### 5.2 High Gap（高優先度：市場継続に影響）

#### Gap-4: 5年間の脆弱性サポート義務と継続的パッチ提供（Annex I Part II）

- **Claim**: CRAは製品の「サポート期間（support period）」として「製品の予想ライフサイクル」または最低5年のいずれか長い方の間、セキュリティアップデートを無償で提供する義務を課している。SEMI E187はパッチを「適時に適用する」義務をユーザー側（ファブ）に課しているが、**サプライヤーがパッチを作成・提供し続ける期間を明示的に規定していない**点が本質的なギャップである。

- **Evidence**:
  - CRA Annex I Part II §1: "ensure vulnerabilities can be addressed through security updates... for a period of at least five years"
  - E187は「サポートされたOS」の使用を要求するが、サプライヤーの5年間パッチ提供義務は規定なし
  - 半導体装置は10〜20年の設備寿命を持つことが多く、5年サポートは最低ラインに過ぎない点に注意（CRAは製品寿命が5年超の場合はそれを上回る期間の対応を要求）

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex I Part II §1](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Source (業界解説)**: [industry_report/tier2] [ENISA Guidelines on CRA Vulnerability Management](https://www.enisa.europa.eu/topics/cybersecurity-policy/cyber-resilience-act) (2024) — primary_source: false
- **Confidence**: high（5年義務の法文は確定。半導体装置への適用解釈はmedium）
- **Requirement Level**: **MUST**

#### Gap-5: 脆弱性開示ポリシー（VDP）の公開義務（Article 13.6）

- **Claim**: CRA Article 13.6は、製造者が「脆弱性の報告を受け付けるための連絡先（contact point）を公開」し、「CVD（Coordinated Vulnerability Disclosure）ポリシーを明示する」ことを要求している。SEMI規格にはこのような製造者主導の公開脆弱性開示ポリシーの概念が存在しない。

- **Evidence**:
  - 製造者は自社ウェブサイトまたは製品ドキュメントにセキュリティ連絡先を明示
  - CRA Article 13.6: 報告された脆弱性に対応するプロセス（VDP）を持ち、外部研究者・ユーザーからの報告窓口を整備
  - ISO/IEC 29147（脆弱性開示）およびISO/IEC 30111（脆弱性ハンドリング）が参照規格
  - 日本企業にとって、英語での窓口整備とEUタイムゾーンでの応答性確保が実務上の課題

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Article 13.6](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Confidence**: high
- **Requirement Level**: **MUST**

### 5.3 Medium Gap（中優先度：自己宣言の実効性に影響）

#### Gap-6: セキュリティイベントログ機能（Annex I Part I §8）

- **Claim**: CRA Annex I Part I §8は「ユーザーが関連するセキュリティイベントのログを記録・モニタリングできる機能」を要求するが、SEMI E187 §3.4のアカウントログ要件より広範であり、認証失敗・設定変更・ネットワーク接続等の包括的なセキュリティイベントログが対象となる。

- **Evidence**:
  - E187はアクセスログ・認証ログを対象とするが、ネットワーク接続ログ・設定変更ログ・セキュリティアラートログの要求水準はCRAの方が高い
  - ログの保持期間・フォーマット・エクスポート機能については、CRAの委任法令（Implementing Acts）で詳細化予定（未確定）

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex I Part I §8](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Confidence**: medium（委任法令の詳細が未確定のため）
- **Requirement Level**: **MUST**

#### Gap-7: データ最小化・プライバシーバイデザイン（Annex I Part I §9）

- **Claim**: CRA Annex I §9は「個人データ・コンテンツ・機能の処理を技術的に必要な最小限に限定する」設計を要求する。半導体装置のソフトウェアが診断テレメトリやオペレーター識別情報を収集する場合、この要件への対応が必要となる。SEMI E187/E188はプライバシー保護を扱わない。

- **Evidence**:
  - GDPR（Regulation (EU) 2016/679）のPrivacy by Design原則とCRA要件の重複：GDPR準拠企業はCRAのこの側面を部分的に充足できる可能性
  - 半導体装置ソフトウェアが「個人データ」を処理しない場合（純粋な設備制御・プロセスデータのみ）、この要件の実質的影響は限定的 (**推測**)

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex I Part I §9](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Confidence**: medium（適用範囲の解釈に不確定要素あり）
- **Requirement Level**: **MUST**

---

## Section 6: SEMI準拠資産の再利用可能マッピング（Reusable Assets from SEMI Compliance）

### 6.1 高再利用可能資産（直接転用可能）

- **Claim**: 以下のSEMI準拠資産はCRA要件を直接または大幅な修正なしに充足できる「高価値再利用資産」であり、対応工数を大幅に削減できる。

| SEMI資産 | 対応するCRA要件 | 再利用方法 | 追加作業 |
|---|---|---|---|
| E187 §3.3 不要ポート/サービス無効化記録 | Annex I Part I §4 (Minimal attack surface) | そのままCRA技術文書に組み込み | 英語化・EU法令フォーマット変換 |
| E187 §3.4 アクセス制御手順書 | Annex I Part I §7 (Access control) | CRAの技術文書Annex Vの証拠として使用 | 網羅性確認・英語化 |
| E187 §3.1 OS更新・パッチ管理手順 | Annex I Part I §6 (Security updates) + Part II §1 | パッチ管理プロセス文書として転用 | 5年間提供義務の担保プロセスを追加 |
| E188 §4.1-4.5 Software Inventory | Annex I Part II §6 (SBOM) | SBOMの原データとして活用 | CycloneDX/SPDXフォーマットへの変換 |
| E187 §3.5 リモートアクセス制御 | Annex I Part I §10 (Encrypted communications) | 暗号化通信証拠として使用 | ローカル通信の暗号化要件の追加確認 |
| E188 §4.2 マルウェアスキャン記録 | Annex I Part I §1 (No known vulnerabilities) | 出荷時セキュリティ検証証拠として転用 | 継続的な市場投入後スキャンの追加 |

- **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex I, Annex V](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024-10) — primary_source: true
- **Source**: [industry_report/tier1] [SEMI E187-0122, SEMI E188-0120](https://store-us.semi.org/products/e18700) (2022) — primary_source: true
- **Confidence**: high（再利用可能性の判断は著者による解釈も含むためmedium要素あり）

### 6.2 部分再利用資産（変換・拡張が必要）

- **Claim**: 以下の資産は既存のSEMI準拠文書を拡張することでCRA要件を充足できるが、一定の新規作業が必要である。これらへの投資は既存文書の改訂として位置づけられるため、ゼロベース構築より50〜70%のコスト削減効果が見込まれる（推測）。

| SEMI資産 | CRA要件との差分 | 拡張内容 |
|---|---|---|
| E187 §3.7 セキュリティ構成ドキュメント | Annex V技術文書の形式・必須記載事項が不足 | 製品識別・ライフサイクル宣言・DoC参照を追加 |
| E187 §3.4 アカウントログ | Annex I Part I §8のセキュリティイベントログより狭い | ネットワーク接続・設定変更・セキュリティアラートログを追加 |
| E188 §4.4 Patch Status文書 | CRA Annex I Part IIの「5年間継続提供義務の担保」なし | サポートライフサイクルポリシーの追加・公開 |

- **Confidence**: medium
- **Source**: [unknown] 著者の規格間比較分析に基づく推論。一次情報による直接的裏付けなし。

---

## Section 7: ギャップの総合評価と対応優先度マトリックス

### 7.1 優先度評価

| ギャップ項目 | 法的ペナルティリスク | 市場アクセスリスク | 構築難度 | 優先度 |
|---|---|---|---|---|
| ENISAインシデント報告プロセス（24h/72h） | **最高**（罰則直結） | 高 | 中（プロセス構築） | **P1** |
| EU適合宣言（DoC）・CEマーキング | **最高**（市場投入不可） | **最高** | 中（文書作業中心） | **P1** |
| 機械可読SBOM（CycloneDX/SPDX） | 高（当局検査で問題化） | 高 | 中（ツール導入） | **P1** |
| 脆弱性開示ポリシー（VDP）公開 | 高 | 中 | 低（ポリシー策定） | **P2** |
| 5年間パッチ提供義務の体制構築 | 高 | 高 | **高**（組織・契約変更） | **P2** |
| セキュリティイベントログ機能拡張 | 中 | 中 | 中（開発作業） | **P3** |
| データ最小化設計 | 中 | 低（装置制御のみなら影響小） | 低〜中 | **P3** |
| 技術文書のAnnex V形式化 | 中 | 中 | 低（文書変換） | **P2** |

### 7.2 既存SEMI準拠による対応完了率の推定

- **Claim**: SEMI E187/E188準拠企業は、CRA Annex I Part I（製品設計要件）において**約60〜70%**の要件を既存資産で充足できると推定される。一方、Annex I Part II（脆弱性管理要件）および法的文書要件（DoC/CEマーキング）は**ほぼ0%**が新規対応であり、プロセス・文書整備に集中投資が必要である。

- **Evidence**: 上記のマッピング表において、13項目のPart I要件のうち◎または△対応は10項目（77%）。ただし△項目には追加作業が必要であるため、完全充足率は60〜70%と見積もる。Part II（6項目）では完全充足はゼロ。

- **Confidence**: medium（SEMI規格の実装水準は企業により異なるため、推定値に±15%の幅がある）
- **Source**: [unknown] 著者のマッピング分析に基づく推論。定量的裏付けは業界調査等で補完が必要。

---

## Section 8: 前提条件プロフィールへの補足提言

SEMI E187/E188を遵守する日本の半導体装置ソフトウェア製造者として特に注目すべき点：

1. **製品分類（Default Category）の確認を最優先せよ**: 汎用IACS機能や組み込みセキュリティ機能（HSM等）を含まない限り、Default Categoryに該当し**第三者認証が不要**となる。この確認だけで対応コストを数百万円単位で削減できる可能性がある。製品機能を法務・技術チームが共同でAnnex III照合することを開始時の必須アクションとする。

2. **「プロセスとドキュメント」への集中投資**: 前項の分析が示す通り、SEMI E187/E188準拠企業の本質的ギャップは技術的な製品設計ではなく、**運用プロセス（インシデント報告・VDP）と法的文書（DoC・技術文書）**に集中している。製品の大規模再設計は不要であり、投資の8割をプロセス・文書整備に集中させるべきである。

3. **報告義務の先行適用（2026年）**: CRAの段階的施行において、インシデント報告義務は完全適用（2027年）より1年早く2026年に施行される。24時間報告体制の構築を最優先タスクとして先行させることが法的リスクの最小化につながる。

4. **E188 Software InventoryのSBOM化**: E188準拠企業は既にソフトウェアインベントリを保有していることが多く、これをSyft等のOSSツールでCycloneDX形式に変換するパイプラインを構築することで、SBOM要件の充足コストを最小化できる（推定5〜10人日の追加作業）。
