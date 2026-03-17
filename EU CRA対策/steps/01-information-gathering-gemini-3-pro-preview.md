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
    *   **半導体製造装置の扱い**: 一般的な半導体製造装置（リソグラフィ、エッチング等）は、それ自体が「ファイアウォール」や「汎用IACS」として機能しない限り、**Default Category**に分類される可能性が高い。この場合、第三者認証は不要であり、製造者による自己宣言（Module A）が可能となるため、コストへの影響は甚大である。ただし、装置に汎用ルーターやHSM（Hardware Security Module）が組み込まれている場合、そのコンポーネントはClass I/IIとなる。
    *   **Requirement Level**: **MUST** (Annex III)
    *   **Evidence**: CRA Final Text Annex III (List of Important Products), Article 6 (Critical products).
    *   **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Annex III](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024) — primary_source: true
    *   **Confidence**: medium (製品の具体的機能によりIACSへの該当性が議論される可能性があるため)

## 2. Economic Operators & Responsibilities (経済事業者の責任分界)

日本企業（製造者）が直接、あるいは販社を通じてEUへ輸出する場合の責任構造。

### Key Findings
*   **Claim: 製造者（Manufacturer）の包括的責任**
    *   自社の名前・商標で製品を上市する自然人または法人は「製造者」とみなされる。日本の本社が開発し、EU支社（Importer）が輸入する場合でも、技術文書の作成、脆弱性対応、適合宣言（DoC）の署名は日本側の責任となる。
    *   **Importerの責任**: 製造者がCRA要件を満たしていることを確認し、不適合がある場合は製品を市場に出してはならない（ゲートキーパー機能）。
    *   **Requirement Level**: **MUST** (Article 13 - Obligations of manufacturers)
    *   **Evidence**: CRA Final Text Article 13, Article 16 (Importers).
    *   **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Article 13](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024) — primary_source: true
    *   **Confidence**: high

## 3. Timeline & Penalties (施行スケジュールと罰則)

### Key Findings
*   **Claim 1: 施行タイムライン（2024年成立版）**
    *   **発効（Entry into Force）**: 2024年中盤（官報掲載から20日後）。
    *   **報告義務の開始**: 発効から21ヶ月後（概ね2026年）。脆弱性およびインシデントの報告義務が先行して適用される。
    *   **完全適用（Application）**: 発効から36ヶ月後（概ね2027年）。この時点でCEマーキング適合が必須となる。
    *   **Requirement Level**: **MUST**
    *   **Evidence**: CRA Final Text Article 57 (Entry into force and application).
    *   **Source**: [official_document/tier1] [European Council Press Release: Cyber Resilience Act adopted](https://www.consilium.europa.eu/en/press/press-releases/2024/10/10/cyber-resilience-act-council-adopts-new-law-on-security-requirements-for-digital-products/) (2024) — primary_source: false
    *   **Confidence**: high

*   **Claim 2: 罰則規定（Non-compliance penalties）**
    *   **最大罰則**: 必須要件（Annex I）への不適合に対し、最大1,500万ユーロ（約24億円）または全世界売上高の2.5%のいずれか高い方。
    *   **その他の違反**: 適合評価機関への虚偽情報の提供などは、最大500万ユーロまたは売上高の1%。
    *   **Requirement Level**: **MUST** (Article 53)
    *   **Evidence**: CRA Final Text Article 53 (Penalties).
    *   **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Article 53](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024) — primary_source: true
    *   **Confidence**: high

## 4. Preliminary Mapping: SEMI E187/E188 vs CRA (SEMI規格との予備的マッピング)

SEMI E187（Fab Equipment Cybersecurity）およびE188（Malware Free Equipment Integration）準拠企業が活用できる資産とギャップ。

### Key Findings
*   **Claim 1: SEMI E187の再利用可能領域（Overlap）**
    *   **OS Support (E187 §3.2)**: サポート切れOSの使用制限およびパッチ適用機能の維持は、CRA Annex I "Vulnerability Management" に直接対応する。
    *   **Security Hardening (E187 §3.4)**: 不要なポート/サービスの無効化は、CRA Annex I "Secure by Default" 要件の中核をなす。
    *   **Access Control (E187 §3.5)**: 認証・認可の仕組みは、CRAのアクセス制御要件に合致する。
    *   **Mapping Status**: **Partial / Direct**
    *   **Evidence**: SEMI E187 Specification for Cybersecurity of Fab Equipment.
    *   **Source**: [industry_report/tier2] [SEMI E187-0122 Specification](https://store-us.semi.org/products/e18700) (2022) — primary_source: true
    *   **Confidence**: high

*   **Claim 2: 明確なギャップ（Gaps）**
    *   **SBOM形式**: SEMI E187ではSBOMが要求されるものの、フォーマットの厳密性は低い。CRAは機械可読な形式（CycloneDX, SPDX等）と継続的な更新を厳格に要求する。
    *   **Active Reporting**: CRAは「悪用された脆弱性」および「深刻なインシデント」を**24時間以内**にCSIRT/ENISAへ早期警告することを義務付けている（Article 11）。SEMI規格には、当局への報告義務プロセスは含まれていない。
    *   **CE Marking & DoC**: 適合宣言書の作成とCEマーク貼付はCRA固有の法的要件であり、SEMI準拠だけではカバーできない。
    *   **Mapping Status**: **Gap (Significant)**
    *   **Evidence**: CRA Article 11 (Reporting obligations), Annex I.
    *   **Source**: [official_document/tier1] [Regulation (EU) 2024/1183 Article 11](https://eur-lex.europa.eu/eli/reg/2024/1183/oj) (2024) — primary_source: true
    *   **Confidence**: high

### Summary for Strategy
この調査結果から、SEMI E187準拠企業は「製品設計（Secure by Design）」の多くの部分でCRA要件を既に満たしている可能性が高い。一方で、「プロセス（脆弱性開示・報告）」と「ドキュメンテーション（適合宣言・技術文書）」に大きなギャップが存在する。戦略の焦点は、製品の再設計ではなく、**運用プロセスの構築と文書化**に置くべきである。
