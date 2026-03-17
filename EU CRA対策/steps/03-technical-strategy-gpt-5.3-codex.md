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

**Evidence（根拠）**: CRAは機械可読SBOM（少なくともトップレベル依存関係）と脆弱性報告を義務化し、SEMI側にはインベントリ・装置セキュリティ基盤が既に存在する。  

**Requirement Level（義務レベル）**: MUST（CRA）  

**Standard Reference（規格対応）**: CRA Annex I（SBOM/脆弱性対応）↔ SEMI E188（Software Inventory）= **partial**  

**Source（情報源）**:  
[official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary: true  
[official_document/tier1] [SEMI E188 product page](https://store-us.semi.org/products/e18800-semi-e188-specification-for-malware-free-equipment-integration) (2026-03-17) — primary: false  

**Confidence（確信度）**: high
**Claim（主張）**: CRA報告運用は、`ENISA SRP前提のテンプレート駆動運用`にすると、日本企業でも24時間通知義務を現実的に運用可能。  

**Evidence（根拠）**: ENISAのSingle Reporting Platform（SRP）運用と、EU公式のCRA報告期限（24h/72h/最終報告）が示されている。  

**Requirement Level（義務レベル）**: MUST（CRA報告義務）  

**Standard Reference（規格対応）**: CRA Article 14/16（報告）↔ SEMI E187/E188 = **gap**  

**Source（情報源）**:  
[official_document/tier1] [ENISA Single Reporting Platform (SRP)](https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp) (2026-03-17) — primary: true  
[official_document/tier1] [European Commission CRA reporting page](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting) (2026-03-17) — primary: true  

**Confidence（確信度）**: high
**Claim（主張）**: 製品設計は「新規再設計」よりも、`CRA Annex I要求をSEMI既存制御へマッピングし不足分だけ実装`する方式が低コスト。  

**Evidence（根拠）**: E187はアクセス制御・ネットワーク最小化・パッチ管理で重複領域がある一方、ログ網羅性・VDP・当局報告は不足。  

**Requirement Level（義務レベル）**: MUST（不足領域）/ SHOULD（高度化）  

**Standard Reference（規格対応）**: CRA Annex I ↔ SEMI E187/E188 = direct/partial/gap混在  

**Source（情報源）**:  
[official_document/tier1] [SEMI E187 product page](https://store-us.semi.org/products/e18700-semi-e187-specification-for-cybersecurity-of-fab-equipment) (2026-03-17) — primary: false  
[official_document/tier1] [SEMI cybersecurity standards overview](https://www.semi.org/en/industry-groups/semiconductor-cybersecurity/standards) (2026-03-17) — primary: false  
[official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary: true  

**Confidence（確信度）**: medium（SEMI条文本文が有償で公開限定）

---

## 1) SBOM Minimum Requirements & OSS Tools（SBOM最低要件とOSSツール）

### 1.1 CRA準拠の最低要件（法令MUST）と実装最低ライン

| 項目 | Requirement Level | 実装最低ライン（日本製造業向け） | Standard Reference | 対応度 |
|---|---|---|---|---|
| 機械可読SBOM | MUST | `CycloneDX JSON`を標準出力、`SPDX JSON`を変換出力 | CRA（SBOM機械可読） | direct |
| トップレベル依存関係の記載 | MUST | 直接依存のみでも初期適合可（後で再帰依存へ拡張） | CRA（top-level dependencies） | direct |
| SBOM最新化（更新運用） | MUST | リリースごとに自動再生成、版管理 | CRA（keep up to date） | direct |
| 既存E188インベントリ再利用 | SHOULD（コスト最適） | Excel/CSV在庫を初期投入し段階的自動化 | SEMI E188 ↔ CRA | partial |
| 依存関係グラフ（ref/dependsOn） | SHOULD | CycloneDX dependenciesを必須化 | CycloneDX schema | partial |

**Source（情報源）**:  
[official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary: true  
[industry_report/tier2] [CycloneDX BOM 1.6 schema](https://github.com/CycloneDX/specification/blob/master/schema/bom-1.6.schema.json) (2026-03-17) — primary: true  
[official_document/tier1] [SEMI E188 product page](https://store-us.semi.org/products/e18800-semi-e188-specification-for-malware-free-equipment-integration) (2026-03-17) — primary: false  

**Confidence（確信度）**: high（CRA法令）、medium（SEMI実運用解釈）
### 1.2 CRA-Minフィールドセット（実務最低）

**Claim（主張）**: CRA最小準拠を狙うなら、法令必須に加え、監査・顧客説明で破綻しない最小フィールドセットを最初から固定すべき。  

**Evidence（根拠）**: CycloneDX/SPDXの必須属性と依存記述要素が明示されている。  

**Requirement Level（義務レベル）**: MUST（法令必須） + SHOULD（運用監査耐性）  

**Standard Reference（規格対応）**: CRA ↔ CycloneDX/SPDX = partial（法令は形式を固定していない）  

**推奨フィールド（CRA-Min）**:  
`doc_format`, `spec_version`, `document_id`, `timestamp`, `product_name`, `product_version`, `component_type`, `component_name`, `component_version`, `supplier`, `download_location`, `hash/checksum`, `license`, `bom_ref`, `dependency_ref`, `depends_on`  

**Source（情報源）**:  
[industry_report/tier2] [CycloneDX BOM 1.6 schema](https://github.com/CycloneDX/specification/blob/master/schema/bom-1.6.schema.json) (2026-03-17) — primary: true  
[industry_report/tier2] [SPDX 2.3 JSON schema](https://github.com/spdx/spdx-spec/blob/v2.3/schemas/spdx-schema.json) (2026-03-17) — primary: true  
[industry_report/tier2] [SPDX 2.3 document creation](https://github.com/spdx/spdx-spec/blob/v2.3/chapters/document-creation-information.md) (2026-03-17) — primary: true  
[industry_report/tier2] [SPDX 2.3 package information](https://github.com/spdx/spdx-spec/blob/v2.3/chapters/package-information.md) (2026-03-17) — primary: true  

**Confidence（確信度）**: high
### 1.3 OSSツール選定（低コスト優先）

| 役割 | 推奨OSS | 理由 | Requirement Level |
|---|---|---|---|
| SBOM生成 | Syft | CycloneDX/SPDX両出力、CI組込み容易 | MUST |
| SBOM変換・検証 | cyclonedx-cli | validate/convert/merge/signが一体 | SHOULD |
| 脆弱性照合 | Grype または OSV-Scanner | SBOM/イメージ/FSスキャン対応 | MUST |
| 継続監視・証跡管理 | Dependency-Track | CycloneDX中心で継続リスク監視 | SHOULD |
| ライセンス/ポリシー統合 | ORT | SPDX/CycloneDX生成＋ポリシー評価 | MAY |

**Source（情報源）**:  
[industry_report/tier2] [Syft README](https://github.com/anchore/syft/blob/main/README.md) (2026-03-17) — primary: true  
[industry_report/tier2] [cyclonedx-cli README](https://github.com/CycloneDX/cyclonedx-cli/blob/main/README.md) (2026-03-17) — primary: true  
[industry_report/tier2] [Grype README](https://github.com/anchore/grype/blob/main/README.md) (2026-03-17) — primary: true  
[industry_report/tier2] [OSV-Scanner README](https://github.com/google/osv-scanner/blob/main/README.md) (2026-03-17) — primary: true  
[industry_report/tier2] [Dependency-Track README](https://github.com/DependencyTrack/dependency-track/blob/master/README.md) (2026-03-17) — primary: true  
[industry_report/tier2] [ORT README](https://github.com/oss-review-toolkit/ort/blob/main/README.md) (2026-03-17) — primary: true  

**Confidence（確信度）**: high

---

## 2) Vulnerability Management & Incident Reporting Workflow（脆弱性管理・インシデント報告設計）

### 2.1 CRA報告期限を前提にした運用SLA

| タイミング | 対応 | Requirement Level | Standard Reference | 対応度 |
|---|---|---|---|---|
| T0〜24h | Early Warning提出（ENISA/CSIRT経路） | MUST | CRA reporting obligations | direct |
| T0〜72h | 詳細通知（影響範囲・暫定対策） | MUST | CRA reporting obligations | direct |
| 修正策準備後14日 | 脆弱性最終報告 | MUST | CRA reporting obligations（実務ガイダンス） | direct |
| 72h通知後1か月 | 深刻インシデント最終報告 | MUST | CRA reporting obligations（実務ガイダンス） | direct |

**Source（情報源）**:  
[official_document/tier1] [European Commission CRA reporting page](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting) (2026-03-17) — primary: true  
[official_document/tier1] [ENISA SRP](https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp) (2026-03-17) — primary: true  
[official_document/tier1] [CRA summary](https://digital-strategy.ec.europa.eu/en/policies/cra-summary) (2026-03-17) — primary: true  

**Confidence（確信度）**: medium（実装細部は委任法令・運用更新で変動可能）
### 2.2 実装ワークフロー（運用負荷最小化）

**Claim（主張）**: 日本企業での実装は、英日テンプレート＋PSIRT当番＋自動証跡収集の3点セットで運用負荷を最小化できる。  

**Evidence（根拠）**: SRPへの期限付き報告には、事前定義テンプレートと迅速なトリアージ体制が必要。PSIRT標準フレームワークでも同様の工程が推奨。  

**Requirement Level（義務レベル）**: MUST（報告期限遵守）/ SHOULD（運用効率化）  

**Standard Reference（規格対応）**: CRA報告義務 = direct、FIRST PSIRT = partial（実装指針）  

**実装手順（最小）**:  
1. 検知トリガー統一（SOC/顧客報告/脆弱性DB）。  
2. 4時間以内トリアージ（影響製品・悪用有無・重大度）。  
3. 24時間以内の初報テンプレート自動生成。  
4. 72時間報告にSBOM差分・暫定回避策・顧客通知案を添付。  
5. 最終報告提出後に是正処置をCAPA化。  

**Source（情報源）**:  
[official_document/tier1] [European Commission CRA reporting page](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting) (2026-03-17) — primary: true  
[industry_report/tier2] [FIRST PSIRT Services Framework v1.1](https://www.first.org/standards/frameworks/psirts/FIRST_PSIRT_Services_Framework_v1.1.pdf) (2026-03-17) — primary: true  

**Confidence（確信度）**: high
### 2.3 VDP/CVD実装（Article 13(6)相当）

**Claim（主張）**: 連絡窓口公開は `security.txt + 専用メール + 公開VDP` の3点で最短実装できる。  

**Evidence（根拠）**: CRAは脆弱性受付連絡先の明示を求め、RFC 9116は標準化された公開方法を提供。  

**Requirement Level（義務レベル）**: MUST（連絡窓口）/ SHOULD（security.txt）  

**Standard Reference（規格対応）**: CRA Article 13(6) = direct、RFC 9116 = partial  

**Source（情報源）**:  
[official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary: true  
[official_document/tier1] [RFC 9116](https://www.rfc-editor.org/rfc/rfc9116) (2026-03-17) — primary: true  
[official_document/tier1] [CISA: security.txt](https://www.cisa.gov/news-events/news/securitytxt-simple-file-big-value) (2026-03-17) — primary: true  

**Confidence（確信度）**: high
### 2.4 CVE公開の現実解（中堅企業向け）

**Claim（主張）**: 脆弱性件数が少ない段階では、自社CNA化よりRoot CNA連携の方が低コスト。  

**Evidence（根拠）**: CNAは運用ルール遵守・人的継続リソースが必要。  

**Requirement Level（義務レベル）**: MAY（CNA化手段）/ MUST（脆弱性ハンドリング）  

**Standard Reference（規格対応）**: CRA脆弱性運用 = direct、CVE運用 = partial  

**Source（情報源）**:  
[official_document/tier1] [CVE CNA Rules v4.1](https://www.cve.org/Resources/Roles/Cnas/CNA_Rules_v4.1.0.pdf) (2026-03-17) — primary: true  
[official_document/tier1] [CVE Program CNAs](https://www.cve.org/ProgramOrganization/CNAs) (2026-03-17) — primary: true  

**Confidence（確信度）**: high

---

## 3) Secure-by-Design Mandatory Implementation Items（セキュアバイデザイン必須実装項目）

| 実装項目 | Requirement Level | 最低実装（実務） | CRA-SEMIマッピング | 対応度 |
|---|---|---|---|---|
| セキュアデフォルト設定 | MUST | 不要サービス無効・初期パスワード禁止・MFA可能化 | CRA Annex I ↔ E187 | partial |
| 攻撃面最小化 | MUST | ポート/プロトコル縮退、USB/保守口制御 | CRA Annex I ↔ E187 | direct |
| 認証・認可 | MUST | RBAC、最小権限、管理者操作の二重承認 | CRA Annex I ↔ E187 | direct |
| ログ・監査証跡 | MUST | 認証失敗/設定変更/更新イベントを改ざん耐性付き記録 | CRA Annex I ↔ E187 | partial |
| 通信・保存データ保護 | MUST | TLS1.2+、鍵管理、機微設定の暗号化保存 | CRA Annex I ↔ E187/E188 | partial |
| セキュリティ更新機構 | MUST | 署名付き更新、ロールバック保護、LTS分岐運用 | CRA Annex I ↔ E187 | partial |
| 脆弱性ハンドリング | MUST | VDP受付、SLA、顧客通知テンプレート、修正追跡 | CRA Article 13/14 ↔ E187/E188 | gap |
| 開発ライフサイクル統制 | SHOULD | SSDFベースで要件→設計→検証→脆弱性対応を定義 | CRA Annex I ↔ NIST SSDF/IEC62443-4-1 | partial |

**Source（情報源）**:  
[official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary: true  
[official_document/tier1] [NIST SP 800-218 (SSDF)](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-218.pdf) (2026-03-17) — primary: true  
[official_document/tier1] [IEC 62443-4-1 publication page](https://webstore.iec.ch/en/publication/33615) (2026-03-17) — primary: true  
[official_document/tier1] [SEMI cybersecurity standards overview](https://www.semi.org/en/industry-groups/semiconductor-cybersecurity/standards) (2026-03-17) — primary: false  

**Confidence（確信度）**: medium（IEC/SEMI詳細条文が有償領域）

---

## 4) 180-Day Practical Rollout（180日実装ロードマップ：日本製造業向け）

| 期間 | 主要成果物 | 概算工数 |
|---|---|---|
| Day 0-30 | SBOM方針、CRA報告テンプレート、VDP公開（security.txt含む） | 20-35人日 |
| Day 31-90 | Syft+cyclonedx-cli自動化、Grype/OSVスキャン、初回ドリル | 35-60人日 |
| Day 91-180 | Dependency-Track運用、24h/72h演習、設計ギャップ改修 | 45-80人日 |

**Claim（主張）**: 「報告運用先行→SBOM自動化→設計改修」の順が、罰則回避と現場負荷のバランスが最も良い。  

**Evidence（根拠）**: 報告義務は先行適用され、SBOMはツール導入で短期に可視化可能、設計改修は最も時間を要する。  

**Requirement Level（義務レベル）**: MUST（報告・SBOM）/ SHOULD（段階導入順）  

**Standard Reference（規格対応）**: CRA reporting/SBOM = direct、設計改修 = partial  

**Source（情報源）**:  
[official_document/tier1] [European Commission CRA reporting page](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting) (2026-03-17) — primary: true  
[industry_report/tier2] [Syft README](https://github.com/anchore/syft/blob/main/README.md) (2026-03-17) — primary: true  
[industry_report/tier2] [Dependency-Track README](https://github.com/DependencyTrack/dependency-track/blob/master/README.md) (2026-03-17) — primary: true  
[unknown/tier4] 推定工数モデル（既存SEMI準拠・中堅規模を仮定）(unknown) (2026-03-17) — primary: false  

**Confidence（確信度）**: medium（工数は推定）

---

## Recommendations（結論・提言）

**Claim（主張）**: 本件の最適解は「CRA必須のMUSTを先に閉じる」戦略。具体的には `SBOM機械可読化` と `24h/72h報告運用` を最優先し、製品設計はSEMI資産を再利用して差分実装する。  

**Evidence（根拠）**: 法令リスク直結領域（報告・脆弱性運用・SBOM）は期限拘束が強く、SEMI既存資産で再利用余地が大きい。  

**Requirement Level（義務レベル）**: MUST  

**Standard Reference（規格対応）**: CRA direct、SEMI partial/gap  

**Source（情報源）**:  
[official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary: true  
[official_document/tier1] [European Commission CRA reporting page](https://digital-strategy.ec.europa.eu/en/policies/cra-reporting) (2026-03-17) — primary: true  
[official_document/tier1] [SEMI standards overview](https://www.semi.org/en/industry-groups/semiconductor-cybersecurity/standards) (2026-03-17) — primary: false  

**Confidence（確信度）**: high
**未確定事項（要ウォッチ）**: SBOM要素の実装細目や報告手順の一部は、実施法・ガイダンス更新で変動余地があるため、四半期ごとに法令ウォッチを組み込むのが安全。  

**Source（情報源）**:  
[official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary: true  
[official_document/tier1] [European Commission CRA summary](https://digital-strategy.ec.europa.eu/en/policies/cra-summary) (2026-03-17) — primary: true  

**Confidence（確信度）**: medium
