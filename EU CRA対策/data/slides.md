---
marp: true
theme: default
paginate: true
style: |
  @import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@400;700&display=swap');
  section {
    font-family: 'Noto Sans JP', 'Helvetica Neue', sans-serif;
    background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    color: #ffffff;
    padding: 40px 60px;
  }
  section.title {
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
    text-align: center;
    display: flex;
    flex-direction: column;
    justify-content: center;
  }
  section.title h1 { font-size: 2.4em; color: #e2e8f0; margin-bottom: 0.2em; }
  section.title p { color: #a0aec0; font-size: 1.1em; }
  section.light {
    background: #ffffff;
    color: #2d3748;
  }
  section.light h2 { color: #2b6cb0; border-bottom: 3px solid #4299e1; padding-bottom: 8px; }
  section.alert {
    background: linear-gradient(135deg, #742a2a 0%, #9b2c2c 100%);
    color: #ffffff;
  }
  section.alert h2 { color: #fed7d7; border-bottom: 3px solid #fc8181; }
  section.success {
    background: linear-gradient(135deg, #22543d 0%, #276749 100%);
    color: #ffffff;
  }
  section.success h2 { color: #c6f6d5; border-bottom: 3px solid #68d391; }
  section.dark {
    background: linear-gradient(135deg, #1a202c 0%, #2d3748 100%);
    color: #e2e8f0;
  }
  h2 { font-size: 1.6em; margin-bottom: 0.6em; }
  strong { color: #ffd700; }
  table { font-size: 0.85em; width: 100%; border-collapse: collapse; }
  th { background: rgba(255,255,255,0.2); padding: 8px 12px; text-align: left; }
  td { padding: 8px 12px; border-bottom: 1px solid rgba(255,255,255,0.1); }
  ul { line-height: 1.7; }
  li { margin-bottom: 0.3em; }
  code { background: rgba(0,0,0,0.3); padding: 2px 8px; border-radius: 4px; font-size: 0.9em; }
  .badge { display: inline-block; padding: 2px 10px; border-radius: 12px; font-size: 0.8em; font-weight: bold; }
  .high { background: #c6f6d5; color: #22543d; }
  .medium { background: #fefcbf; color: #744210; }
  .low { background: #fed7d7; color: #742a2a; }
---
<!-- _class: title -->
# EU CRA対策戦略
## SEMI規格準拠企業向け技術ロードマップ

2026-03-17
AI Research Agent

---
<!-- _class: light -->
# エグゼクティブサマリー

SEMI E187/E188準拠をベースに、EUサイバーレジリエンス法（CRA）への効率的な対応を目指します。開発チームは以下の重要マイルストーンを認識する必要があります。

- **最優先期限**: **2026年9月**（脆弱性・インシデント報告義務の先行施行）
- **完全施行**: **2027年12月**（セキュアバイデザイン、SBOM、CEマーキング）
- **基本戦略**: SEMI準拠資産の最大活用＋報告プロセスの新規構築
- **コスト影響**: 脆弱性管理プロセスの維持コスト（5年間サポート義務）

<br>
<span class="badge high">Confidence: High</span> 法的施行スケジュールは確定済みです。

---
<!-- _class: light -->
# 1. CRA適用範囲と対象製品

半導体製造装置の制御PC、組み込みOS、ファームウェアは「デジタル要素を含む製品（PDEs）」として**CRA規制の対象**となります。

- **ハードウェア・ソフトウェア**: EU市場に上市される全てのPDEsが対象
- **OSSの扱い**: 商用製品に組み込まれたOSSコンポーネントは製造者責任
- **SaaS**: リモート処理のみならNIS2対象だが、デバイス側コンポーネントがあればCRA対象

**開発チームへの影響**:
既存の出荷済み製品に対するサポート期間とパッチ提供義務の範囲特定が急務です。

<span class="badge high">High</span> Article 2 (Scope)

---
<!-- _class: light -->
# 2. 重要製品分類（Class I/II）の判定

多くの半導体製造装置は「デフォルトカテゴリ」ですが、産業用オートメーション制御システム（IACS）等の機能を持つ場合は**Class I/II**に分類される可能性があります。

- **Default Category**: 自己適合宣言（Module A）が可能。第三者認証不要。
- **Class I/II**: 第三者機関による関与が必要になる可能性あり。
- **判断基準**: ネットワーク機能、特権アクセス管理機能の有無。

**開発チームへの影響**:
Annex IIIリストに基づき、自社製品機能が「重要製品」に該当しないか精査が必要です。

<span class="badge medium">Medium</span> Annex III / Recital 10

---
<!-- _class: light -->
# 3. SEMI E187/E188とのギャップ分析

既存のSEMI規格対応は有用ですが、CRA準拠には**不足領域（Gap）**があります。ここを埋めることが技術対応の焦点です。

| 領域 | SEMI E187/E188 | EU CRA (Annex I) | ギャップ |
| :--- | :--- | :--- | :--- |
| **OS強化** | 対応済 (Hardening) | 必須 | **小** (再利用可) |
| **SBOM** | Software Inventory | 機械可読SBOM | **大** (形式変換必須) |
| **脆弱性管理** | パッチ適用プロセス | **24時間以内**の報告 | **特大** (運用体制) |
| **設計** | マルウェアフリー | セキュアバイデフォルト | **中** (証明が必要) |

<span class="badge high">High</span> SEMI E187/E188 vs CRA Annex I Mapping

---
<!-- _class: light -->
# 4. 技術戦略：SBOMの実装

SEMI E188で要求される「Software Inventory」を、CRAが求める機械可読な**SBOM（CycloneDX/SPDX）**へ変換・高度化する必要があります。

- **必須要件**: 脆弱性データベースとの自動照合が可能な形式であること
- **推奨ツール**: Syft, Grype, Dependency-Track等のOSS活用
- **運用**: ビルドパイプラインへのSBOM生成組み込みと、出荷後の構成管理

**開発チームへの影響**:
手動管理のインベントリから、CI/CD統合型のSBOM自動生成フローへの移行が必要です。

<span class="badge medium">Medium</span> CRA Annex II / E188 Specification

---
<!-- _class: light -->
# 5. 技術戦略：脆弱性報告（Article 14）

**2026年9月**より、悪用された脆弱性や深刻なインシデントについて、**認知から24時間以内の「早期警告」**が義務化されます。

- **Early Warning**: 24時間以内にENISA/CSIRTへ第一報
- **Full Notification**: 72時間以内に詳細報告
- **Final Report**: 修正完了後または1ヶ月以内

**開発チームへの影響**:
技術的な検知から法務・広報へのエスカレーションを含む、緊急対応フローの確立と演習が不可欠です。

<span class="badge high">High</span> Article 14 (Reporting Obligations)

---
<!-- _class: alert -->
# 未対応時のリスク（Alert）

CRAに違反した場合、ビジネス存続に関わる重大なペナルティが課されます。

- **制裁金**: 最大 **1,500万ユーロ** または 全世界売上高の **2.5%**（高い方）
- **市場アクセス**: EU市場での**販売停止・回収命令**（リコール）
- **サプライチェーン**: SEMI準拠を求める顧客からの取引停止（適合宣言書が出せないため）

単なる努力目標ではなく、**「EUへの輸出許可証」**と捉える必要があります。

<span class="badge high">High</span> Article 53 (Penalties)

---
<!-- _class: success -->
# 段階的導入ロードマップ（Action Items）

開発チームが着手すべきアクションと期限です。

1.  **Phase 1: 調査・定義 (〜2024 Q4)**
    - 製品分類（Default vs Class I/II）の確定
    - EU代理人（Authorised Representative）の指名準備
2.  **Phase 2: 体制構築 (〜2026 Q2)** 🔴 **最優先**
    - **24時間脆弱性報告フロー**の策定とPSIRT体制強化
    - 既存SEMI資産のCRAマッピングドキュメント作成
3.  **Phase 3: 技術実装 (〜2027 Q3)**
    - CI/CDパイプラインへのSBOM生成・脆弱性スキャン統合
    - 技術文書（Technical Documentation）の整備と適合宣言（DoC）準備

<span class="badge medium">Medium</span> Implementation Roadmap based on CRA Timeline

---
<!-- _class: dark -->
# 結論：法令対応を競争力へ

CRA対応はコストですが、回避不能な市場参入要件です。

- **SEMI規格の貯金**を活かし、ゼロベースの競合より有利な位置にいます。
- まずは**「2026年9月の報告義務」**をターゲットに、PSIRT体制を整備しましょう。
- 自動化（SBOM/VEX）への投資は、長期的にはソフトウェア品質向上に寄与します。

**Next Step**:
対象製品リストの棚卸しと、SEMI E187/E188対応状況の精査を開始してください。

---

<!-- _class: light -->
<!-- _backgroundColor: white -->

![bg contain](../diagram.png)

---

<!-- _class: light -->
<!-- _backgroundColor: white -->

![bg contain](../visuals/matrix.png)

---

<!-- _class: light -->
<!-- _backgroundColor: white -->

![bg contain](../visuals/mindmap.png)

---

<!-- _class: light -->
<!-- _backgroundColor: white -->

![bg contain](../visuals/timeline.png)

---

<!-- _class: dark -->

## Thank You

AI Research Agent によるリサーチ結果をご覧いただきありがとうございました。

本資料に関するご質問・フィードバックをお待ちしています。
