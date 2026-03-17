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

- **Claim（主張）**: CRAは3段階で施行される。2024年12月10日発効、2026年9月11日に脆弱性報告義務の適用開始、2027年12月11日に全面施行（適合性評価・CEマーキング・技術文書の全要件適用）。2026年6月11日からはNotified Bodyの指定通知が開始される。
- **Evidence（根拠）**: Regulation (EU) 2024/2847の条文および欧州委員会公式タイムラインにより確認。脆弱性報告義務は既にEU市場にある製品も対象（レガシー製品含む）。
- **Source（情報源）**: [SRC-001] [official_document/tier1] [Regulation (EU) 2024/2847](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true; [SRC-002] [official_document/tier1] [European Commission CRA Portal](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act) (2026-03-17) — primary_source: true; [SRC-003] [news_article/tier3] [Hogan Lovells – CRA 2026 Milestones](https://www.hoganlovells.com/en/publications/eu-cyber-resilience-act-getting-ready-for-cra-compliance-in-2026) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: high
- **Evidence Strength（根拠の強さ）**: strong
- **Requirement Level（義務レベル）**: MUST（全施行日は法令で確定）
- **Standard Reference（規格参照）**: EU CRA Article 71（施行条項）— direct

### Finding 2: 製品分類—半導体装置制御ソフトウェアはClass I（重要製品）に該当する可能性が高い

- **Claim（主張）**: CRA Annex IIIおよび実施規則(EU) 2025/2392の技術定義に基づき、半導体製造装置に組み込まれる制御ソフトウェアはIACS（産業用オートメーション・制御システム）カテゴリとしてClass I（重要製品）に分類される可能性が高い。Default Categoryではなく、Class Iの場合は調和規格が利用可能な場合の自己適合宣言、もしくはEN規格がない場合の第三者評価が必要となる。NIS2指令の「essential entities」向けに使用される場合はClass IIに昇格するリスクもある。
- **Evidence（根拠）**: 実施規則(EU) 2025/2392（2025年12月1日公布・12月21日施行）がAnnex IIIの技術的定義を確定。IACSソフトウェアが明示的にClass Iに列挙されている。半導体製造装置の制御ソフトウェアはPLC/DCS/SCADA等と同等の機能を持つため、「core functionality」原則によりIACSカテゴリに該当する蓋然性が高い。
- **Source（情報源）**: [SRC-004] [official_document/tier1] [Implementing Regulation (EU) 2025/2392](https://eur-lex.europa.eu/eli/reg_impl/2025/2392/oj/eng) (2026-03-17) — primary_source: true; [SRC-005] [industry_report/tier3] [Secure by Design Handbook – CRA Technical Definitions](https://www.securebydesignhandbook.com/blog/2025/11/28/cra-implementing-regulation-published) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: high（法令による分類基準は確定。個別製品の該当判定は法務確認要）
- **Evidence Strength（根拠の強さ）**: strong
- **Requirement Level（義務レベル）**: MUST（分類確定はCRA準拠の前提条件）
- **Standard Reference（規格参照）**: EU CRA Annex III Part I, Implementing Regulation (EU) 2025/2392 Annex I — direct

### Finding 3: EU域外製造者のAuthorised Representative設置義務

- **Claim（主張）**: CRA Article 18により、EU域内に法的拠点を持たない日本の製造者がEU市場にデジタル要素を含む製品を出荷する場合、書面による委任状に基づきEU域内にAuthorised Representative（AR）を設置する義務がある。ARはDoC・技術文書の10年間保管、市場監視当局への協力を担う。ただし、製品設計・脆弱性対応等の製造者義務そのものはARに移転されず日本本社に残る。
- **Evidence（根拠）**: Article 18の条文は明確にEU域外製造者のAR設置を規定。EU製品安全法制の一般原則として、非EU製造者の法的アクセスポイント確保は標準要件。
- **Source（情報源）**: [SRC-006] [official_document/tier1] [EU CRA Article 18](https://cyber-resilience-act.com/cra/chapter-2/article-18/) (2026-03-17) — primary_source: true; [SRC-007] [industry_report/tier2] [EU AR Guide – ecocomply](https://ecocomply.ai/blog/eu-authorised-representative-ar-complete-guide-for-non-eu-manufacturers) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: high
- **Evidence Strength（根拠の強さ）**: strong
- **Requirement Level（義務レベル）**: MUST（Article 18は「shall」表現）
- **Standard Reference（規格参照）**: EU CRA Article 18 — direct

### Finding 4: 商流パターンによる責任主体の分岐と契約整備の緊急性

- **Claim（主張）**: 日本から欧州への半導体装置ソフトウェア販売には複数の商流パターン（①EU子会社経由、②商社経由、③現地ディストリビューター経由、④OEM組込み）が存在し、各パターンでCRA上の責任主体（Manufacturer / Authorised Representative / Importer / Distributor）が根本的に異なる。前ステップ分析は「直接輸出・製造者責任」のみを前提としており、商社・OEM経由の分析が完全に欠落していた。責任の分断（設計責任は製造者に残り、文書保管・当局対応はImporterが負う等）が実務上最大の混乱要因となる。
- **Evidence（根拠）**: CRA Article 13（製造者義務）、Article 16（輸入者義務）、Article 17（販売者義務）、Article 18（AR）、Recital 47（サプライチェーン義務）により責任主体が明確に区分されている。日本の半導体装置関連企業の欧州展開は商社・代理店経由が主流であるという業界実態がある。
- **Source（情報源）**: [SRC-001]; [SRC-008] [official_document/tier1] [EU CRA Article 16–18, Recital 47](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence（確信度）**: high（法的定義は確定。各商流への当てはめは個別法務確認要）
- **Evidence Strength（根拠の強さ）**: strong
- **Requirement Level（義務レベル）**: MUST（責任主体の確定なくして以降のすべてのフェーズは実施不能）
- **Standard Reference（規格参照）**: EU CRA Articles 13, 16, 17, 18, Recital 47 — direct

### Finding 5: SEMI E187/E188とCRA要件のマッピング—再利用可能範囲と限界

- **Claim（主張）**: SEMI E187（Fab装置サイバーセキュリティ仕様）とE188（マルウェアフリー統合仕様）は、CRA Annex I Part Iの必須セキュリティ要件の一部をカバーするが、**適用対象・ライフサイクル範囲・義務レベルの体系が根本的に異なる**ため、条項レベルの精密マッピングなしに「60〜70%再利用可能」とする推計は検証不能である。

| 比較軸 | SEMI E187/E188 | CRA Annex I |
|---|---|---|
| **適用対象** | 半導体Fab装置に組み込まれたソフトウェア | EU市場のすべてのデジタル要素を含む製品 |
| **義務レベル体系** | SHOULD = 正当な理由があれば除外可能（minus記法） | shall = 法的義務（罰則付き） |
| **ライフサイクル** | 装置の設置・稼働・廃棄 | 製品設計〜出荷後5年間のサポート |
| **SBOM深度** | E188: 装置上の全ソフトウェアインベントリ | コンポーネント単位の依存関係・ライセンス・ハッシュ |
| **脆弱性報告** | 規定なし | 24h早期警告・72h詳細通知・14日最終報告（ENISA経由） |
| **適合宣言** | 顧客要求ベースのセルフアセスメント | CEマーキング・DoC・技術文書の法定要件 |

- **Evidence（根拠）**: SEMI E187はOS セキュリティ・ネットワークセキュリティ・エンドポイント保護・セキュリティ監視の4領域でCRAの「セキュアバイデザイン」要件と部分的に重複する。一方、CRAの脆弱性管理（5年間サポート・インシデント報告）、SBOM（機械可読形式・ハッシュ値）、適合宣言（DoC・CEマーキング）には対応する条項がSEMI規格に存在しない。SEMI準拠が「書面対応」に留まり実装を伴わないケースが業界で散見される点もリスク要因。
- **Source（情報源）**: [SRC-009] [official_document/tier1] [SEMI E187-0817 Specification](https://www.semi.org/en/products-services/standards/e187) (2026-03-17) — primary_source: true; [SRC-010] [official_document/tier1] [SEMI Cybersecurity Standards](https://www.semi.org/en/industry-groups/semiconductor-cybersecurity/standards) (2026-03-17) — primary_source: true; [SRC-011] [industry_report/tier3] [Claroty – SEMI E187/E188 Compliance](https://claroty.com/blog/understanding-semi-e187-e188-compliance-for-the-semiconductor-industry) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: high（両規格の条文構造からマッピング限界は明確）
- **Evidence Strength（根拠の強さ）**: moderate（条項レベルの精密マッピングは未実施のため再利用率は未確定）
- **Standard Reference（規格参照）**: SEMI E187 → CRA Annex I Part I: partial; SEMI E188 → CRA Annex I Part I: partial; SEMI E187/E188 → CRA Article 14（報告義務）: gap; SEMI E187/E188 → CRA Annex VII（DoC）: gap

### Finding 6: CRA要件×SEMI規格マッピング表（統合版）

- **Claim（主張）**: CRA Annex I Part IおよびPart IIの必須要件とSEMI E187/E188の対応関係を以下のマッピング表で整理する。「再利用可能」はSEMI準拠が実装レベルで達成されていることが前提条件。

| CRA要件領域 | CRA条項 | 義務レベル | SEMI E187/E188 対応 | 対応度 | GAP内容 | 追加対応の必要性 |
|---|---|---|---|---|---|---|
| **リスクアセスメント** | Annex I §1(a) | MUST | E187: 脅威分析の概念あり | partial | CRAはリスクアセスメントの文書化・製品ライフサイクル全体での更新を要求 | 中 |
| **セキュアバイデザイン** | Annex I §1(b)–(h) | MUST | E187: OS/NW/EP/監視の4領域 | partial | CRAは暗号化・最小権限・攻撃面最小化・データ保護等を明示的に要求。SEMI SHOULDがCRA shallに直接対応しない | 高 |
| **デフォルトセキュリティ** | Annex I §1(d) | MUST | E187: 一部言及あり | partial | 出荷時の安全なデフォルト設定の保証。SEMI E187は設定ガイドラインの提供だがデフォルト値の強制は不十分 | 中 |
| **脆弱性管理プロセス** | Annex I Part II §1–8 | MUST | E187: パッチ管理の概念あり | partial | CRAは脆弱性の特定・文書化・修正・開示のプロセス全体を要求。5年間の継続義務。 | 高 |
| **SBOM** | Annex I Part II §1 | MUST | E188: ソフトウェアインベントリ | partial | 機械可読形式（CycloneDX/SPDX）、依存関係、ハッシュ値が必要。E188インベントリは形式・深度が不足 | 高 |
| **脆弱性報告（ENISA）** | Article 14 | MUST | なし | gap | 24h/72h/14dの段階的報告義務。SEMI規格に報告義務なし | 新規構築 |
| **適合宣言（DoC）** | Article 28, Annex VII | MUST | なし | gap | EU DoC作成・CEマーキング。SEMI規格に相当要件なし | 新規構築 |
| **技術文書** | Annex V | MUST | E187/E188: 一部流用可能 | partial | 設計・実装・テスト・リスク評価を10年間保管。SEMI準拠文書で一部転用可能だが追加作成必要 | 高 |
| **セキュリティアップデート** | Article 13(8) | MUST | E187: パッチ対応の概念あり | partial | 5年間の無料セキュリティアップデート提供義務。SEMI規格は具体的な義務期間を規定しない | 高 |
| **ユーザーへの情報提供** | Annex II | MUST | なし | gap | セキュリティ特性・連絡先・サポート期間等をユーザーに提供 | 新規構築 |

- **Source（情報源）**: [SRC-001]; [SRC-009]; [SRC-010]; [SRC-004]
- **Confidence（確信度）**: high（CRA条文およびSEMI規格文書の構造比較に基づく）
- **Evidence Strength（根拠の強さ）**: moderate（個別条項の詳細マッピングには製品固有の分析が必要）

### Finding 7: IEC 62443のCRA調和規格化の進展と戦略的活用

- **Claim（主張）**: IEC 62443シリーズ（特に62443-4-1：セキュア開発ライフサイクル、62443-4-2：技術的セキュリティ要件）はCEN/CENELECにより調和規格化が進行中であり（EN IEC 62443-4-1:2018/A11:2026, EN IEC 62443-4-2:2019/A11:2026として修正作業中）、2026年中の発行が目標とされている。正式にEU官報に掲載された場合、「準拠推定（Presumption of Conformity）」が発生し適合性評価が大幅に簡素化される。2026年3月時点ではまだ正式指定されていないため、「コスト削減効果30〜50%」は楽観的な前提であり確定値として使うべきではないが、**IEC 62443に今から着手することは投資対効果が最も高い準備行動**である。
- **Evidence（根拠）**: CEN-CENELECのWebinar（2025年9月）で62443シリーズのCRA調和規格化ロードマップが公表。CENELEC TC65X WG3が修正作業を主導。ただし正式な調和規格指定（EU官報掲載）は2026年3月時点で未完了。
- **Source（情報源）**: [SRC-012] [official_document/tier1] [CEN-CENELEC CRA Webinar – EN IEC 62443 to CRA](https://www.cencenelec.eu/news-events/events/2025/2025-09-09-en-iec-62443-to-cra/) (2026-03-17) — primary_source: true; [SRC-013] [industry_report/tier2] [exida – IEC 62443 CRA Compliance](https://www.exida.com/Blog/how-iec-62443-can-help-achieve-compliance-with-the-eu-cyber-resilience-act-cra) (2026-03-17) — primary_source: false; [SRC-014] [industry_report/tier3] [Advantech – IEC 62443 & CRA](https://www.advantech.com/en-us/resources/faq/things-you-need-to-know-about-iec-62443-and-the-cyber-resilience-act-cra) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: medium（修正作業は進行中だが正式指定時期は流動的）
- **Evidence Strength（根拠の強さ）**: moderate
- **Requirement Level（義務レベル）**: SHOULD（CRA準拠に直接必須ではないが、準拠推定効果により強く推奨）
- **Standard Reference（規格参照）**: IEC 62443-4-1 → CRA Annex I Part II: partial（調和規格指定後はdirect）; IEC 62443-4-2 → CRA Annex I Part I: partial（同上）

### Finding 8: SBOM要件の詳細と実装戦略

- **Claim（主張）**: CRAが要求するSBOMは「一般的に使用される機械可読形式」で作成されなければならず、CycloneDX（ECMA-424）またはSPDX（ISO/IEC 5962）が事実上の標準形式。BSI TR-03183-2が詳細なフィールドマッピングを提供しており、必須フィールドにはサプライヤー名、コンポーネント名・バージョン、依存関係、著者、タイムスタンプ、暗号ハッシュ（SHA-256等）が含まれる。SBOM全面準拠期限は2027年12月11日。SEMI E188のソフトウェアインベントリは出発点として活用できるが、形式・深度・自動化の面で大幅な拡張が必要。
- **Evidence（根拠）**: CRA条文、BSI TR-03183-2、OpenSSFのCRA分析レポートにより確認。トップレベル依存関係は義務的、推移的依存関係（transitive）は強く推奨。CI/CDパイプラインでの自動生成が事実上必須（手動SBOMは運用不能）。
- **Source（情報源）**: [SRC-015] [official_document/tier1] [BSI TR-03183 Technical Guideline](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/Technische-Richtlinien/TR-nach-Thema-sortiert/tr03183/TR-03183_node.html) (2026-03-17) — primary_source: true; [SRC-016] [industry_report/tier2] [OpenSSF – SBOMs in the Era of the CRA](https://openssf.org/blog/2025/10/22/sboms-in-the-era-of-the-cra-toward-a-unified-and-actionable-framework/) (2026-03-17) — primary_source: false; [SRC-017] [news_article/tier3] [safedep – SBOM and EU CRA](https://safedep.io/sbom-and-eu-cra-cyber-resilience-act/) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: high
- **Evidence Strength（根拠の強さ）**: strong
- **Requirement Level（義務レベル）**: MUST（機械可読SBOMは法定要件）
- **Standard Reference（規格参照）**: CRA Annex I Part II §1 — direct; BSI TR-03183-2 — partial（ガイドラインであり法的拘束力なし）

### Finding 9: 24時間脆弱性報告義務の実運用設計と日本企業固有の課題

- **Claim（主張）**: 2026年9月11日から、製造者は「積極的に悪用されている脆弱性（actively exploited vulnerability）」を認知してから24時間以内にENISA SRPへ早期警告を提出し、72時間以内に詳細通知、14日以内に最終報告を行う義務がある。日本企業にとっての固有課題は、(a) タイムゾーン差（JST+9による夜間対応リスク）、(b) 英語での報告作成能力、(c) 24/7オンコール体制の構築コスト、(d) 「actively exploited」の判定基準の不明確さ、(e) ENISA SRPの運用開始状況の不確実性の5点。
- **Evidence（根拠）**: CRA Article 14が報告義務を明確に規定。ENISAはSRPを2026年9月の義務開始に向けて開発中だが、2026年3月時点ではパイロット段階。SRP未稼働時の代替経路（国別CSIRT直接報告）の準備が必要。罰則は最大1500万ユーロまたは全世界売上高の2.5%。
- **Source（情報源）**: [SRC-018] [official_document/tier1] [EU CRA Article 14](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true; [SRC-019] [official_document/tier1] [ENISA SRP](https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp) (2026-03-17) — primary_source: true; [SRC-020] [industry_report/tier3] [Zealience – CRA Article 14 Flowchart](https://zealience.com/resource-hub/Cyber-Resilience-Act-Article-14-Reporting-Obligations-of-Manufacturers) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: high（法的義務は確定。SRPの運用開始状況のみmedium）
- **Evidence Strength（根拠の強さ）**: strong
- **Requirement Level（義務レベル）**: MUST（Article 14は「shall」。2026年9月施行）
- **Standard Reference（規格参照）**: EU CRA Article 14 — direct

### Finding 10: 罰則構造とリスクシナリオ

- **Claim（主張）**: CRA違反の罰則は3段階構造で、①必須セキュリティ要件（Annex I）違反：最大1500万ユーロまたは全世界売上高の2.5%のいずれか高い方、②その他の義務違反：最大1000万ユーロまたは売上高の2%、③市場監視当局への虚偽・不完全情報提供：最大500万ユーロまたは売上高の1%。加えて、EU市場からの製品撤去命令（リコール）のリスクがある。

| リスクシナリオ | 違反類型 | 罰則上限 | 追加リスク |
|---|---|---|---|
| **CEマーキングなしの出荷** | Annex I / Article 28違反 | €15M / 2.5% | 即座の市場アクセス停止 |
| **脆弱性報告の遅延・未報告** | Article 14違反 | €15M / 2.5% | EU市場での信頼喪失 |
| **SBOM未整備** | Annex I Part II §1違反 | €15M / 2.5% | 技術文書不備として追及 |
| **DoC・技術文書の不備** | Article 28 / Annex V違反 | €10M / 2% | 適合性評価無効 |
| **脆弱性パッチ5年間未提供** | Article 13(8)違反 | €15M / 2.5% | 継続的な違反状態 |
| **市場監視当局への協力拒否** | Article 52違反 | €5M / 1% | 法的紛争の長期化 |

- **Source（情報源）**: [SRC-021] [official_document/tier1] [EU CRA Article 64（罰則）](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) (2026-03-17) — primary_source: true
- **Confidence（確信度）**: high
- **Evidence Strength（根拠の強さ）**: strong
- **Requirement Level（義務レベル）**: MUST_NOT（罰則対象行為の禁止）

### Finding 11: コスト試算—3シナリオ分析（初期構築+5年間継続運用）

- **Claim（主張）**: コスト試算は単一の楽観シナリオではなく、3シナリオで提示すべき。前ステップの「213〜390人日・外部費用210〜580万円」は基準シナリオとして参考にはなるが、独立した一次情報による検証がなく著者推論である。特にClass I判定の場合はNotified Body関与コストが数百万〜1000万円追加される。最大のコスト要因は初期構築ではなく5年間の継続運用費用であり、これが前ステップ分析で未計上である。

| シナリオ | 前提条件 | 初期構築工数 | 初期外部費用 | 年間運用工数 | 年間運用外部費用 | 5年間総費用（人件費込み概算） |
|---|---|---|---|---|---|---|
| **楽観** | Default Category、SEMI実装良好、ISO 27001保有、単一製品 | 150〜250人日 | 150〜400万円 | 30〜50人日/年 | 30〜80万円/年 | 2,000〜4,500万円 |
| **基準** | Class I、SEMI準拠標準的、ISO 27001未保有、2〜3製品 | 300〜500人日 | 400〜1,000万円 | 50〜100人日/年 | 80〜200万円/年 | 5,000〜12,000万円 |
| **悲観** | Class I/II、SEMI書面のみ、多製品、OEM商流複雑 | 500〜900人日 | 1,000〜3,000万円 | 100〜200人日/年 | 200〜500万円/年 | 12,000〜30,000万円 |

※人件費単価を1人日5万円として概算。外部費用は法務コンサル・認証機関・ツール導入費用を含む。

- **Source（情報源）**: [SRC-022] [unknown] コスト推計は前ステップ分析の著者推論＋批判レビューの修正提案＋EU規制対応の業界一般知識に基づく統合推計 (2026-03-17) — primary_source: false
- **Confidence（確信度）**: low（工数・コスト推計はすべて著者推論であり、独立したベンチマークデータなし）
- **Evidence Strength（根拠の強さ）**: weak（定性的妥当性はあるが定量根拠なし）

### Finding 12: 日本企業の先行対応状況と支援インフラ

- **Claim（主張）**: 2026年3月時点で、日本の半導体装置関連企業によるCRA完全準拠の公開事例は確認されていない。ただし、経産省（METI）がOTセキュリティガイドライン（半導体工場等向け）を2025年に公表、IoTセキュリティラベリング制度「JC-STAR」を立ち上げ、SBOM施策を日米欧の国際連携で推進している。大手装置メーカーではIEC 62443適用の設計変更プロジェクト立ち上げ、SBOM自動生成ツール導入、EU対応専任部門設置が開始されている。PwC Japan、マクニカ等がCRA対応コンサルティングサービスを提供。
- **Source（情報源）**: [SRC-023] [official_document/tier1] [METI Cybersecurity Policy](https://www.meti.go.jp/english/policy/safety_security/cybersecurity/index.html) (2026-03-17) — primary_source: true; [SRC-024] [industry_report/tier2] [PwC Japan – EU CRA対応](https://www.pwc.com/jp/ja/knowledge/column/awareness-cyber-security/eu-cyber-resilience-act05.html) (2026-03-17) — primary_source: false; [SRC-025] [industry_report/tier2] [マクニカ – CRA対応半導体セキュリティ](https://www.macnica.co.jp/business/semiconductor/articles/pickup/147269/) (2026-03-17) — primary_source: false; [SRC-026] [news_article/tier3] [ITmedia – 欧州CRA対応の勘所](https://www.itmedia.co.jp/news/articles/2409/20/news037.html) (2026-03-17) — primary_source: false
- **Confidence（確信度）**: medium（支援インフラの存在は確認。個別企業の準拠完了事例は未確認）
- **Evidence Strength（根拠の強さ）**: moderate

---

## 3領域別Must/Want対応チェックリスト

### 領域1: 製品設計（セキュアバイデザイン・デフォルトセキュリティ）

| # | 要件 | CRA条項 | 義務レベル | SEMI対応 | 対応度 | 対応優先度 |
|---|---|---|---|---|---|---|
| D-1 | サイバーセキュリティリスクアセスメントの実施・文書化 | Annex I §1(a) | MUST | E187: 一部 | partial | 高 |
| D-2 | 既知の脆弱性なしでの出荷 | Annex I §1(b) | MUST | E187: 脆弱性スキャン | partial | 高 |
| D-3 | セキュアバイデフォルト設定 | Annex I §1(d) | MUST | E187: 設定ガイド | partial | 中 |
| D-4 | 不正アクセスからの保護（認証・アクセス制御） | Annex I §1(e) | MUST | E187: アクセス制御 | partial | 中 |
| D-5 | 保存・転送・処理中データの保護（暗号化等） | Annex I §1(f) | MUST | E187: 一部 | partial | 高 |
| D-6 | 攻撃面の最小化 | Annex I §1(c) | MUST | E187: NWセグメンテーション | partial | 中 |
| D-7 | セキュリティイベントのログ記録・監視 | Annex I §1(h) | MUST | E187: セキュリティ監視 | partial | 低 |
| D-8 | 工場出荷時リセット機能 | Annex I §1(d) | SHOULD | なし | gap | 中 |
| D-9 | 安全なアップデートメカニズム | Annex I §1(g) | MUST | E187: パッチ管理概念 | partial | 高 |
| D-10 | IEC 62443-4-1準拠のセキュア開発プロセス | — | WANT | なし | gap | 高（将来の調和規格対応） |

### 領域2: 脆弱性管理

| # | 要件 | CRA条項 | 義務レベル | SEMI対応 | 対応度 | 対応優先度 |
|---|---|---|---|---|---|---|
| V-1 | 製品の脆弱性を特定・文書化するプロセス | Annex I Part II §1 | MUST | なし | gap | 高（最優先） |
| V-2 | SBOMの作成・維持（機械可読形式） | Annex I Part II §1 | MUST | E188: インベントリ | partial | 高（最優先） |
| V-3 | 脆弱性の迅速な修正とセキュリティアップデート提供 | Annex I Part II §2 | MUST | E187: パッチ概念 | partial | 高 |
| V-4 | 5年間のセキュリティサポート義務 | Article 13(8) | MUST | なし | gap | 高 |
| V-5 | 脆弱性開示ポリシー（VDP）の公開 | Annex I Part II §5 | MUST | なし | gap | 中 |
| V-6 | ENISAへの24h早期警告 | Article 14(2)(a) | MUST | なし | gap | 高（2026年9月期限） |
| V-7 | ENISAへの72h詳細通知 | Article 14(2)(b) | MUST | なし | gap | 高（2026年9月期限） |
| V-8 | ENISAへの14日最終報告 | Article 14(2)(c) | MUST | なし | gap | 高（2026年9月期限） |
| V-9 | ユーザーへの脆弱性・修正措置の通知 | Annex I Part II §4 | MUST | なし | gap | 中 |
| V-10 | セキュリティアップデートの無料提供 | Annex I Part II §2 | MUST | なし | gap | 高 |

### 領域3: ドキュメント・適合宣言

| # | 要件 | CRA条項 | 義務レベル | SEMI対応 | 対応度 | 対応優先度 |
|---|---|---|---|---|---|---|
| C-1 | 技術文書の作成（設計・リスク評価・テスト結果） | Annex V | MUST | E187/E188: 一部流用 | partial | 高 |
| C-2 | EU適合宣言書（DoC）の作成 | Article 28, Annex VII | MUST | なし | gap | 高 |
| C-3 | CEマーキングの貼付 | Article 29 | MUST | なし | gap | 高 |
| C-4 | 技術文書の10年間保管 | Article 13(13) | MUST | なし | gap | 中 |
| C-5 | ユーザー向け情報提供（セキュリティ特性、連絡先、サポート期間） | Annex II | MUST | なし | gap | 中 |
| C-6 | EU Authorised Representativeの設置 | Article 18 | MUST | なし | gap | 高（最優先） |
| C-7 | 適合性評価の実施（Class Iの場合） | Article 32 | MUST | なし | gap | 高 |
| C-8 | 顧客向けCRAコンプライアンス文書の整備 | — | WANT | なし | gap | 中 |
| C-9 | IEC 62443認証取得 | — | WANT | なし | gap | 中（コスト削減効果） |
| C-10 | ISO 27001認証取得 | — | WANT | なし | gap | 低（組織レベルの補強） |

---

## 段階的導入ロードマップ（工数概算付き）

### タイムライン概要

```
2026年Q1-Q2: Phase 0（法的基盤確立）
2026年Q3:    Phase 1（脆弱性報告体制）← 2026年9月施行に間に合わせる
2026年Q3-Q4: Phase 2（技術基盤構築）
2027年Q1-Q2: Phase 3（適合性準備）
2027年Q3-Q4: Phase 4（審査・宣言）← 2027年12月全面施行
2028年以降:  Phase 5（継続運用）
```

### Phase 0: 法的基盤確立（2026年Q1-Q2、3〜4ヶ月）

**目的**: ロードマップ全体の前提条件を確定する。ここでの判断ミスは後続全フェーズのコスト・方針に影響。

| タスクID | タスク名 | 内容 | 工数（基準） | 優先度 | 義務レベル |
|---|---|---|---|---|---|
| P0-0 | **商流・責任主体の確定** | EU販売の全商流パターンを洗い出し、各チャンネルのCRA責任主体を法務確認。商社・ディストリビューター・OEMとの責任分担契約を締結 | 15〜30人日 | **最優先** | MUST |
| P0-1 | **Annex III製品分類確定** | 実施規則(EU) 2025/2392に基づき自社製品のClass I/II/Default判定を実施。EU CRA専門法律事務所によるIACS該当性の意見書取得 | 10〜20人日 | **最優先** | MUST |
| P0-2 | **EU Authorised Representative選定・契約** | EU域内にARを設置。AR候補の選定、書面委任状作成、DoC・技術文書の保管体制合意 | 10〜15人日 | **最優先** | MUST |
| P0-3 | **SEMI準拠資産の実態棚卸し** | E187/E188準拠が「書面のみ」か「実装済み」かを監査し、CRA技術文書への転用可能範囲を確定 | 15〜25人日 | 高 | MUST |
| P0-4 | **社内CRA推進体制の発足** | CRA責任者（CISO相当）、PSIRT核メンバー、法務担当の任命。経営層向けブリーフィング | 5〜10人日 | 高 | MUST |
| P0-5 | **CRA法文・委任法令の学習** | 開発チーム全体へのCRA概要研修、担当者向け深掘り研修 | 10〜15人日 | 中 | SHOULD |
| | **Phase 0 合計** | | **65〜115人日** | | |

### Phase 1: 脆弱性報告体制構築（2026年Q3、2〜3ヶ月）— **2026年9月期限**

**目的**: 2026年9月11日のArticle 14施行に間に合わせる。最初の法的義務発生ポイント。

| タスクID | タスク名 | 内容 | 工数（基準） | 優先度 | 義務レベル |
|---|---|---|---|---|---|
| P1-1 | **PSIRTの正式設立** | 脆弱性受付・トリアージ・報告の専任体制。最低3名（PSIRT Lead、技術者、英語報告担当） | 15〜25人日 | **最優先** | MUST |
| P1-2 | **24h/72h/14d報告プロセス設計** | 下記の実運用設計を含む完全な報告フロー策定 | 15〜25人日 | **最優先** | MUST |
| P1-3 | **ENISA SRP登録・代替経路準備** | SRPアカウント登録。SRP未稼働時の国別CSIRT連絡先リスト作成 | 5〜10人日 | **最優先** | MUST |
| P1-4 | **英語報告テンプレート作成** | 24h早期警告・72h詳細通知・14d最終報告の3種類を事前作成（穴埋め形式） | 5〜10人日 | 高 | MUST |
| P1-5 | **「actively exploited」社内判定基準策定** | CISA KEV掲載・PoC公開・顧客報告の3条件を社内基準として設定 | 3〜5人日 | 高 | MUST |
| P1-6 | **オンコール体制設計** | タイムゾーン差（JST+9）を考慮した24/7対応体制。報告判断者・報告作成者・技術確認者の3役当番制 | 5〜10人日 | 高 | MUST |
| P1-7 | **VDP（脆弱性開示ポリシー）公開** | セキュリティ研究者からの脆弱性報告受付窓口と処理方針の公開 | 5〜10人日 | 中 | MUST |
| P1-8 | **インシデント対応ドリル（初回）** | テンプレート・連絡先の有効性確認。年2回実施をカレンダー登録 | 3〜5人日 | 中 | SHOULD |
| | **Phase 1 合計** | | **56〜100人日** | | |

**P1-2 報告フロー実運用設計（詳細）**:

```
[脆弱性検知 T0]
  ├─ 社内トリアージ (4h以内)
  │   ├─ 「actively exploited」判定 → YES → 報告フロー開始
  │   └─ NO → 通常脆弱性管理プロセス
  │
  ├─ [T0+24h] ENISA SRP 早期警告提出
  │   ├─ 使用言語: 英語
  │   ├─ 必須記載: 製品名、影響するEU加盟国、脆弱性概要
  │   └─ SRP不可時: 主要販売国のCSIRTへ直接報告
  │
  ├─ [T0+72h] 詳細通知提出
  │   ├─ 脆弱性の性質、悪用状況、対処状況、ユーザー緩和策
  │   └─ 並行: ユーザーへの脆弱性・緩和策の通知
  │
  └─ [T0+14d] 最終報告提出
      └─ 根本原因、影響範囲、修正パッチ状況、再発防止策

  タイムゾーン考慮:
  - 最悪ケース: 欧州早朝(CET 06:00)=日本14:00 → 対応猶予あり
  - 最悪ケース: 欧州夕方(CET 18:00)=日本深夜02:00 → オンコール対応必須
  - 実質対応可能時間: 24h − 9h(TZ差) − 4h(トリアージ) = 11h
```

### Phase 2: 技術基盤構築（2026年Q3-Q4、4〜6ヶ月）

| タスクID | タスク名 | 内容 | 工数（基準） | 優先度 | 義務レベル |
|---|---|---|---|---|---|
| P2-1 | **SBOM自動生成パイプライン構築** | CycloneDX/SPDX形式でのCI/CD統合。Syft、Trivy、または同等ツール導入。組込み環境固有の対応策検討 | 20〜40人日 | **最優先** | MUST |
| P2-2 | **SBOM管理基盤** | Dependency-TrackまたはGUAC等のSBOM管理・脆弱性マッチングプラットフォーム構築 | 15〜25人日 | 高 | MUST |
| P2-3 | **セキュアバイデザイン実装** | CRA Annex I Part Iの要件に基づく製品セキュリティ機能の実装・強化（暗号化、アクセス制御、最小権限等） | 30〜60人日 | 高 | MUST |
| P2-4 | **セキュリティテスト基盤** | 脆弱性スキャン・ペネトレーションテスト・ファジングの自動化。テスト結果は技術文書の証拠として保存 | 15〜25人日 | 高 | MUST |
| P2-5 | **5年間サポート体制設計** | 製品サポート期間の定義、パッチ配信メカニズム、EOL計画。顧客への通知プロセス | 10〜15人日 | 高 | MUST |
| P2-6 | **IEC 62443-4-1プロセス導入** | セキュア開発ライフサイクルのプロセス定義。将来の調和規格化を見越した投資 | 20〜30人日 | 中 | SHOULD |
| | **Phase 2 合計** | | **110〜195人日** | | |

**SBOM ツール選定ガイド（OSS優先）**:

| ツール | 種別 | 出力形式 | 組込み対応 | ライセンス | 推奨度 |
|---|---|---|---|---|---|
| **Syft** (Anchore) | SBOM生成 | CycloneDX / SPDX | コンテナ・ファイルシステム | Apache 2.0 | ◎ |
| **Trivy** (Aqua) | SBOM生成+脆弱性スキャン | CycloneDX / SPDX | コンテナ・バイナリ | Apache 2.0 | ◎ |
| **Dependency-Track** (OWASP) | SBOM管理+脆弱性マッチング | CycloneDX | — | Apache 2.0 | ◎ |
| **GUAC** (Google) | サプライチェーン分析 | — | — | Apache 2.0 | ○ |
| **FOSSology** | ライセンス解析 | SPDX | — | GPL 2.0 | ○ |

⚠️ **組込みソフトウェア固有の注意**: 上記OSSツールの多くはLinuxコンテナ環境・標準パッケージマネージャを前提とする。Windows環境・専用ビルドシステム・クローズドコンパイラの組込み開発では、手動でのSBOMフィールド補完やビルドシステムプラグインの自社開発が必要になるケースがある。

### Phase 3: 適合性準備（2027年Q1-Q2、4〜5ヶ月）

| タスクID | タスク名 | 内容 | 工数（基準） | 優先度 | 義務レベル |
|---|---|---|---|---|---|
| P3-1 | **技術文書（Annex V）作成** | 設計説明、リスクアセスメント結果、テスト報告書、SBOM、適用規格一覧。SEMI準拠文書からの転用を最大化 | 30〜50人日 | **最優先** | MUST |
| P3-2 | **DoC（適合宣言書）ドラフト** | Annex VII形式に準拠したEU適合宣言書の作成 | 5〜10人日 | 高 | MUST |
| P3-3 | **適合性評価手続き** | Class Iの場合：調和規格による自己適合宣言（Module A）、または調和規格がない場合の第三者評価準備 | 15〜30人日 | 高 | MUST |
| P3-4 | **ユーザー情報文書（Annex II）作成** | セキュリティ特性、連絡先、サポート期間、廃棄方法をユーザー向けに文書化 | 5〜10人日 | 中 | MUST |
| P3-5 | **社内模擬審査** | 全CRA要件に対する準拠状況の内部レビュー。ギャップの最終修正 | 10〜15人日 | 中 | SHOULD |
| P3-6 | **顧客向けCRAコンプライアンス文書** | SBOM提供方針、脆弱性開示タイムライン、サポート期間を顧客へ提示 | 5〜10人日 | 中 | WANT |
| | **Phase 3 合計** | | **70〜125人日** | | |

### Phase 4: 審査・宣言（2027年Q3-Q4、2〜3ヶ月）

| タスクID | タスク名 | 内容 | 工数（基準） | 優先度 | 義務レベル |
|---|---|---|---|---|---|
| P4-1 | **CEマーキング手続き** | DoC最終化、技術文書の完成確認、CEマーク貼付 | 5〜10人日 | **最優先** | MUST |
| P4-2 | **Notified Body審査（Class Iの場合）** | 調和規格がない場合のModule B+C審査。外部コスト大 | 10〜20人日+外部費用 | 高 | MUST（条件付き） |
| P4-3 | **技術文書・DoCのAR移管** | ARへの文書引き渡し、10年間保管体制の確認 | 3〜5人日 | 高 | MUST |
| P4-4 | **市場監視対応の最終準備** | 当局からの照会対応手順、是正措置プロセスの文書化 | 3〜5人日 | 中 | MUST |
| | **Phase 4 合計** | | **21〜40人日** | | |

### Phase 5: 継続運用（2028年以降、年間）

| タスクID | タスク名 | 内容 | 年間工数（基準） | 義務レベル |
|---|---|---|---|---|
| P5-1 | 脆弱性監視・トリアージ | SBOM連携による日常的な脆弱性監視、PSIRT運営 | 20〜40人日/年 | MUST |
| P5-2 | セキュリティパッチ開発・配信 | 発見された脆弱性の修正と配信 | 15〜30人日/年 | MUST |
| P5-3 | SBOM更新 | リリースごとのSBOM再生成・管理基盤更新 | 5〜10人日/年 | MUST |
| P5-4 | 技術文書更新 | 製品変更に伴うAnnex V文書の更新 | 5〜10人日/年 | MUST |
| P5-5 | インシデント対応ドリル | 年2回の報告訓練 | 3〜5人日/年 | SHOULD |
| P5-6 | 委任法令・調和規格の追跡 | 新規委任法令・調和規格のモニタリングと対応 | 5〜10人日/年 | MUST |
| | **Phase 5 年間合計** | | **53〜105人日/年** | |

### ロードマップ全体概算（基準シナリオ）

| フェーズ | 期間 | 工数 | 主要外部費用 |
|---|---|---|---|
| Phase 0 | 2026 Q1-Q2 | 65〜115人日 | 法務コンサル100〜300万円、AR契約50〜100万円 |
| Phase 1 | 2026 Q3 | 56〜100人日 | PSIRT教育20〜50万円 |
| Phase 2 | 2026 Q3-Q4 | 110〜195人日 | ツール導入30〜100万円、セキュリティテスト50〜150万円 |
| Phase 3 | 2027 Q1-Q2 | 70〜125人日 | 外部レビュー50〜100万円 |
| Phase 4 | 2027 Q3-Q4 | 21〜40人日 | Notified Body 100〜500万円（Class I時） |
| **初期合計** | **18ヶ月** | **322〜575人日** | **400〜1,300万円** |
| Phase 5 | 年間 | 53〜105人日/年 | 80〜200万円/年 |
| **5年間総運用** | **5年** | **265〜525人日** | **400〜1,000万円** |

---

## コスト削減パターン分析（関連規格の重複活用）

| 削減パターン | 活用規格 | 適用CRA要件 | 推定削減効果 | 前提条件 | Confidence |
|---|---|---|---|---|---|
| **IEC 62443-4-1導入** | IEC 62443-4-1 | セキュア開発ライフサイクル（Annex I Part II全般） | Phase 2-3で20〜30%工数削減 | 調和規格指定後は適合推定効果により認証コストも削減 | medium |
| **IEC 62443-4-2準拠** | IEC 62443-4-2 | 技術的セキュリティ要件（Annex I Part I） | Phase 2で15〜25%工数削減 | 調和規格指定が前提。指定前でも技術文書の証拠補強に有効 | medium |
| **SEMI E187/E188文書転用** | SEMI E187/E188 | 技術文書（Annex V）の一部 | Phase 3で10〜20%工数削減 | SEMI準拠が実装レベルで達成されていることが条件 | low |
| **ISO 27001の組織レベル補強** | ISO 27001 | リスクマネジメント、インシデント対応、文書管理 | Phase 0-1で10〜15%工数削減 | ISO 27001認証済みの場合のみ | medium |
| **BSI TR-03183-2準拠SBOM** | BSI TR-03183 | SBOM要件（Annex I Part II §1） | Phase 2でSBOMフィールド設計の手戻り削減 | ガイドラインであり法的拘束力なしだが事実上の標準 | high |

⚠️ **重要な注意**: IEC 62443は2026年3月時点でCRAの調和規格に正式指定されていない。指定前の投資は「将来の準拠推定効果」を見越した戦略的判断であり、確定した削減効果ではない。「30〜50%コスト削減」という前ステップの推計は楽観的であり、**10〜30%**がより現実的なレンジである。

---

## Requirement Level Matrix（義務レベルマトリクス）

| 義務レベル | 件数 | 主な要件 | 規格間の解釈差異 |
|---|---|---|---|
| **MUST** | 28件 | セキュアバイデザイン、SBOM作成、24h脆弱性報告、DoC・CEマーキング、技術文書10年保管、AR設置、5年間サポート | CRAの「shall」は罰則付き法的義務。SEMI E187の「SHOULD」は正当な理由があれば除外可能（minus記法）であり、**同じ要件であってもSEMI SHOULDをCRA MUST充足の証拠として直接使用できない**。SEMI SHOULDで対応したものがCRA shallの要件を満たすかは条項ごとの検証が必要 |
| **SHOULD** | 8件 | IEC 62443導入、インシデント対応ドリル、推移的依存関係のSBOM記載、社内模擬審査 | CRAの調和規格（一旦指定されれば）によるSHOULD準拠は「準拠推定」を発生させるため、事実上のMUST。IEC 62443のSHOULDはCRA文脈では「強く推奨だが法的義務ではない」 |
| **WANT** | 5件 | ISO 27001認証、顧客向けCRA文書整備、先行事例収集 | 法的義務なし。ただし顧客・パートナーからの商業的要求としてMUST化する可能性あり |
| **MUST_NOT** | 6件 | 既知の脆弱性を放置した状態での出荷禁止、報告遅延・虚偽報告禁止、CEマーキング不正使用禁止 | 罰則は最大€15M / 売上高2.5% |

### SEMI SHOULD vs CRA shall の解釈差異（最重要リスク）

SEMI規格体系ではSHOULDは「推奨（minus可能）」であり、ユーザー（装置メーカー）は正当な理由があれば仕様からの逸脱が認められる。これに対しCRA Annex Iの「shall」は法的義務であり、逸脱に対して罰則が適用される。

**実務的影響**: SEMI E187のSHOULD条項（例：特定の暗号化方式の採用、特定のアクセス制御メカニズムの実装）を「SEMI準拠済み＝CRA対応済み」として技術文書に記載した場合、市場監視当局の審査でgapとして指摘されるリスクがある。

**推奨対応**: Phase 0-3（P0-3）のSEMI資産棚卸し時に、各条項のSHOULD/shallレベルを明示的に照合し、SEMI SHOULDで対応した項目がCRA shallの水準を満たしているかを個別に検証すること。

---

## Confidence Distribution（確信度分布）

- **High confidence の発見**: 9件（Finding 1, 2, 3, 4, 5, 6, 8, 9, 10）
- **Medium confidence の発見**: 2件（Finding 7, 12）
- **Low confidence の発見**: 1件（Finding 11）
- **全体の確信度評価**: 法令要件・規格構造に関する発見はhighだが、**コスト試算（Finding 11）がlowである点が最大の弱点**。経営層への提示には3シナリオ提示により不確実性を明示すべき。

---

## Contradictory Claims（矛盾する主張）

| # | 矛盾の内容 | 解決状況 | 統合レビューでの対応 |
|---|---|---|---|
| 1 | **SEMI資産「60〜70%カバー」の循環論証** — 前ステップ分析が自身の推論を根拠として引用 | **未解決** | マッピング表（Finding 6）で個別対応度を「partial」「gap」で明示し、パーセンテージでの包括的表現を排除。再利用可能性はP0-3の棚卸し結果に依存すると明記 |
| 2 | **Default Category前提のコスト試算** vs **Class I該当の高い蓋然性** | **統合レビューで修正** | 基準シナリオをClass I前提に変更。3シナリオ分析（Finding 11）でDefault/Class I/Class IIの分岐を反映 |
| 3 | **24時間報告の概念図** vs **実運用の複雑性** | **統合レビューで補強** | Phase 1（P1-2）にタイムゾーン対応・オンコール体制・英語テンプレート・判定基準・SRP代替経路を実装要素として追加 |
| 4 | **直接輸出・製造者責任の単純化** vs **商流の多様性** | **統合レビューで修正** | Phase 0にP0-0（商流・責任主体の確定）を最優先タスクとして新設 |

---

## Missing Data（不足データ）

1. **自社SEMI準拠の実態（書面 vs 実装）の監査結果** — ロードマップの工数・コスト推計の精度を左右する最重要データ。Phase 0-3で取得予定。
2. **CRA委任法令の確定内容**（SBOM詳細仕様、報告書式、製品分類ガイドライン）— 2025〜2027年に順次公布予定。ロードマップのPhase 5で継続追跡。
3. **同規模日本企業のCRA対応工数ベンチマーク** — 2026年3月時点で公開事例なし。経産省・コンサルファームからの情報公開を待つ。
4. **ENISA SRPの実稼働テスト環境・利用手順書** — 2026年9月の義務開始までに取得必須。
5. **EU加盟国別CSIRTの受付言語・報告書式の詳細** — SRP代替経路の設計に必要。
6. **顧客（半導体装置OEM）からの具体的CRAコンプライアンス要求内容** — 「変動的な要求」の実態把握が未完。
7. **5年間継続運用コストの業界ベンチマーク** — CRA最大のコスト要因だが定量データなし。

---

## Limitations（制約・限界）

1. **法令の発効時期の制約**: CRAは2024年12月に発効したばかりであり、調和規格・委任法令の大部分が策定途中。ロードマップは2026年3月時点の情報に基づいており、追加要件の発生により修正が必要になる。
2. **コスト推計の定量根拠の欠如**: 全工数・費用推計は著者推論であり、独立したベンチマークデータによる検証がない。
3. **製品固有の分析の限界**: 汎用的なロードマップであり、特定製品のAnnex III分類・セキュリティ機能の実装状況は個別分析が必要。
4. **SEMI準拠実態の未検証**: SEMI E187/E188準拠が実装レベルで達成されているかの前提が未確認。
5. **日本語情報の制約**: CRA原文は英語（EU公用語）であり、日本語訳は非公式。法的判断には原文参照が必須。

---

## Unresolved Issues（未解決事項）

| # | 事項 | 重大度 | 解決アクション | 期限 |
|---|---|---|---|---|
| 1 | **製品のAnnex III分類が未確定** | 高 | P0-1で実施規則(EU) 2025/2392に基づく法務確認 | 2026年Q2 |
| 2 | **商流・責任主体の法的確定** | 高 | P0-0で全商流パターンの法務確認・契約整備 | 2026年Q2 |
| 3 | **EU Authorised Representativeの選定** | 高 | P0-2で候補選定・契約 | 2026年Q2 |
| 4 | **ENISA SRPの実稼働状況** | 高 | P1-3でSRP登録＋代替CSIRT経路を並行準備 | 2026年Q3 |
| 5 | **「actively exploited」判定基準の委任法令** | 中 | P1-5で暫定社内基準を設定、委任法令公布後に更新 | 継続監視 |
| 6 | **IEC 62443の調和規格指定時期** | 中 | P5-6で追跡。指定後は適合性評価手続きを切り替え | 継続監視 |
| 7 | **追加委任法令による要件変更** | 中 | P5-6で追跡。変更時はロードマップを更新 | 継続監視 |

---

## Conclusion（結論）

SEMI規格準拠企業がEU CRAに準拠するためのロードマップは、以下の5つの確定事項と2つの未確定事項に基づいて策定される。

**確定事項（high confidence）**:
1. CRAは2026年9月に脆弱性報告義務、2027年12月に全面施行される。タイムラインは法令で確定。
2. SEMI E187/E188はCRA要件の一部を部分的にカバーするが、脆弱性報告・SBOM（機械可読形式）・適合宣言・5年間サポートには対応するSEMI条項が存在せず、新規構築が必要。
3. EU域外の日本製造者はAuthorised Representative設置が法的義務。
4. 半導体装置制御ソフトウェアはAnnex III Class I（重要製品）に該当する蓋然性が高く、Default Categoryを前提としたコスト試算は過小推計のリスクがある。
5. 罰則は最大1500万ユーロまたは全世界売上高の2.5%であり、EU市場アクセス停止リスクと合わせて経営上の重大リスク。

**未確定事項（low〜medium confidence）**:
1. 工数・コスト推計はすべて著者推論であり、3シナリオ（楽観：2,000〜4,500万円、基準：5,000〜12,000万円、悲観：12,000〜30,000万円の5年間総費用）で提示。確定値ではない。
2. IEC 62443の調和規格化による準拠推定効果は、正式指定後に初めて確定する。

**最優先アクション**: Phase 0の3タスク（P0-0: 商流確定、P0-1: 製品分類確定、P0-2: AR設置）を即座に着手すること。この3つの確定なくして、後続フェーズのロードマップ全体の前提が崩れうる。

---

## Recommended Actions（推奨アクション）

| 優先度 | アクション | 期限 | 義務レベル | 担当 |
|---|---|---|---|---|
| **1（即時）** | 全EU販売商流の洗い出しと責任主体の法務確認。商社・ディストリビューター・OEMとのCRA責任分担契約を締結 | 2026年Q2 | MUST | 法務・営業 |
| **2（即時）** | 実施規則(EU) 2025/2392に基づくAnnex III製品分類の法的確定。IACS該当性の専門家意見書取得 | 2026年Q2 | MUST | 法務・技術 |
| **3（即時）** | EU Authorised Representative候補の選定・書面委任状締結 | 2026年Q2 | MUST | 法務・経営 |
| **4（急）** | SEMI E187/E188準拠の実態監査（書面 vs 実装の確認） | 2026年Q2 | MUST | 技術・品質 |
| **5（急）** | PSIRT設立・24h報告体制の構築。英語テンプレート・オンコール体制・判定基準の策定 | 2026年Q3 | MUST | セキュリティ |
| **6（急）** | ENISA SRP登録。SRP未稼働時の代替CSIRT報告経路の準備 | 2026年Q3 | MUST | セキュリティ |
| **7（高）** | SBOM自動生成パイプラインの構築（CycloneDX/SPDX、CI/CD統合） | 2026年Q4 | MUST | 開発 |
| **8（高）** | IEC 62443-4-1に基づくセキュア開発プロセスの導入開始 | 2026年Q4 | SHOULD | 開発 |
| **9（高）** | 技術文書（Annex V）・DoC・CEマーキングの準備 | 2027年Q2 | MUST | 技術・品質 |
| **10（中）** | 経営層向けCRAリスクブリーフィング（3シナリオのコスト提示、罰則リスクの定量説明） | 即時 | SHOULD | 経営 |
| **11（中）** | 経産省ガイドライン・JC-STAR・SBOM国際連携施策のウォッチ | 継続 | SHOULD | 企画 |
| **12（低）** | ISO 27001認証の取得検討（CRA対応の組織レベル補強） | 2027年 | WANT | 経営・品質 |

---

## Source Registry（情報源一覧）

| ID | Source Type / Tier | Title | URL | Access Date | Primary |
|---|---|---|---|---|---|
| [SRC-001] | official_document / tier1 | Regulation (EU) 2024/2847 (CRA Full Text) | [EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) | 2026-03-17 | true |
| [SRC-002] | official_document / tier1 | European Commission – CRA Policy Portal | [EC Digital Strategy](https://digital-strategy.ec.europa.eu/en/policies/cyber-resilience-act) | 2026-03-17 | true |
| [SRC-003] | news_article / tier3 | Hogan Lovells – EU CRA Key 2026 Milestones | [Hogan Lovells](https://www.hoganlovells.com/en/publications/eu-cyber-resilience-act-getting-ready-for-cra-compliance-in-2026) | 2026-03-17 | false |
| [SRC-004] | official_document / tier1 | Implementing Regulation (EU) 2025/2392 (Technical Descriptions) | [EUR-Lex](https://eur-lex.europa.eu/eli/reg_impl/2025/2392/oj/eng) | 2026-03-17 | true |
| [SRC-005] | industry_report / tier3 | Secure by Design Handbook – CRA Technical Definitions | [securebydesignhandbook.com](https://www.securebydesignhandbook.com/blog/2025/11/28/cra-implementing-regulation-published) | 2026-03-17 | false |
| [SRC-006] | official_document / tier1 | EU CRA Article 18 (Authorised Representatives) | [cyber-resilience-act.com](https://cyber-resilience-act.com/cra/chapter-2/article-18/) | 2026-03-17 | true |
| [SRC-007] | industry_report / tier2 | EU AR Guide – ecocomply | [ecocomply.ai](https://ecocomply.ai/blog/eu-authorised-representative-ar-complete-guide-for-non-eu-manufacturers) | 2026-03-17 | false |
| [SRC-008] | official_document / tier1 | EU CRA Articles 13, 16, 17, 18, Recital 47 (Supply Chain Obligations) | [EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) | 2026-03-17 | true |
| [SRC-009] | official_document / tier1 | SEMI E187-0817 Specification for Cybersecurity of Fab Equipment | [SEMI Standards](https://www.semi.org/en/products-services/standards/e187) | 2026-03-17 | true |
| [SRC-010] | official_document / tier1 | SEMI Cybersecurity Standards Overview | [SEMI](https://www.semi.org/en/industry-groups/semiconductor-cybersecurity/standards) | 2026-03-17 | true |
| [SRC-011] | industry_report / tier3 | Claroty – Understanding SEMI E187/E188 Compliance | [Claroty](https://claroty.com/blog/understanding-semi-e187-e188-compliance-for-the-semiconductor-industry) | 2026-03-17 | false |
| [SRC-012] | official_document / tier1 | CEN-CENELEC Webinar – From EN IEC 62443 to CRA | [CEN-CENELEC](https://www.cencenelec.eu/news-events/events/2025/2025-09-09-en-iec-62443-to-cra/) | 2026-03-17 | true |
| [SRC-013] | industry_report / tier2 | exida – How IEC 62443 Simplifies CRA Compliance | [exida](https://www.exida.com/Blog/how-iec-62443-can-help-achieve-compliance-with-the-eu-cyber-resilience-act-cra) | 2026-03-17 | false |
| [SRC-014] | industry_report / tier3 | Advantech – IEC 62443 and the CRA | [Advantech](https://www.advantech.com/en-us/resources/faq/things-you-need-to-know-about-iec-62443-and-the-cyber-resilience-act-cra) | 2026-03-17 | false |
| [SRC-015] | official_document / tier1 | BSI TR-03183 Technical Guideline (SBOM Requirements) | [BSI](https://www.bsi.bund.de/EN/Themen/Unternehmen-und-Organisationen/Standards-und-Zertifizierung/Technische-Richtlinien/TR-nach-Thema-sortiert/tr03183/TR-03183_node.html) | 2026-03-17 | true |
| [SRC-016] | industry_report / tier2 | OpenSSF – SBOMs in the Era of the CRA | [OpenSSF](https://openssf.org/blog/2025/10/22/sboms-in-the-era-of-the-cra-toward-a-unified-and-actionable-framework/) | 2026-03-17 | false |
| [SRC-017] | news_article / tier3 | safedep – SBOM and the EU CRA | [safedep.io](https://safedep.io/sbom-and-eu-cra-cyber-resilience-act/) | 2026-03-17 | false |
| [SRC-018] | official_document / tier1 | EU CRA Article 14 (Reporting Obligations) | [EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) | 2026-03-17 | true |
| [SRC-019] | official_document / tier1 | ENISA Single Reporting Platform (SRP) | [ENISA](https://www.enisa.europa.eu/topics/product-security-and-certification/single-reporting-platform-srp) | 2026-03-17 | true |
| [SRC-020] | industry_report / tier3 | Zealience – CRA Article 14 Reporting Flowchart | [Zealience](https://zealience.com/resource-hub/Cyber-Resilience-Act-Article-14-Reporting-Obligations-of-Manufacturers) | 2026-03-17 | false |
| [SRC-021] | official_document / tier1 | EU CRA Article 64 (Penalties) | [EUR-Lex](https://eur-lex.europa.eu/eli/reg/2024/2847/oj/eng) | 2026-03-17 | true |
| [SRC-022] | unknown / — | コスト推計（著者推論・前ステップ統合） | — | 2026-03-17 | false |
| [SRC-023] | official_document / tier1 | METI Cybersecurity Policy | [METI](https://www.meti.go.jp/english/policy/safety_security/cybersecurity/index.html) | 2026-03-17 | true |
| [SRC-024] | industry_report / tier2 | PwC Japan – EU CRA対応 | [PwC Japan](https://www.pwc.com/jp/ja/knowledge/column/awareness-cyber-security/eu-cyber-resilience-act05.html) | 2026-03-17 | false |
| [SRC-025] | industry_report / tier2 | マクニカ – CRA対応半導体セキュリティソリューション | [マクニカ](https://www.macnica.co.jp/business/semiconductor/articles/pickup/147269/) | 2026-03-17 | false |
| [SRC-026] | news_article / tier3 | ITmedia – 欧州CRA対応の勘所 | [ITmedia](https://www.itmedia.co.jp/news/articles/2409/20/news037.html) | 2026-03-17 | false |
| [SRC-027] | official_document / tier1 | CEN-CENELEC CRA Standardisation Webinar (IEC 62443 Amendments) | [CEN-CENELEC PDF](https://www.cencenelec.eu/media/CEN-CENELEC/Events/Webinars/2025/2025-09-08_webinar_unlocking_cra_iec62443-series-for-cra.pdf) | 2026-03-17 | true |
| [SRC-028] | official_document / tier1 | EC CRA Implementation FAQ | [EC Digital Strategy](https://digital-strategy.ec.europa.eu/en/library/cyber-resilience-act-implementation-frequently-asked-questions) | 2026-03-17 | true |
| [SRC-029] | industry_report / tier3 | CRA standardisation request CEN CENELEC ETSI guide | [goregulus.com](https://goregulus.com/uncategorized/cra-standardisation-request-cen-cenelec-etsi/) | 2026-03-17 | false |
| [SRC-030] | news_article / tier3 | DLA Piper – CRA What You Need to Know | [DLA Piper](https://www.dlapiper.com/en/insights/publications/2026/02/cyber-resilience-act-what-you-need-to-know-and-what-you-need-to-be-doing) | 2026-03-17 | false |

**Source Coverage Summary**:

| source_type | 件数 | 比率 |
|---|---|---|
| official_document | 16件 | 53% |
| industry_report | 9件 | 30% |
| news_article | 4件 | 13% |
| unknown | 1件 | 3% |

| reliability_tier | 件数 | 比率 |
|---|---|---|
| tier1 | 16件 | 53% |
| tier2 | 5件 | 17% |
| tier3 | 8件 | 27% |
| unknown | 1件 | 3% |

| primary_source | 件数 | 比率 |
|---|---|---|
| true | 16件 | 53% |
| false | 14件 | 47% |
