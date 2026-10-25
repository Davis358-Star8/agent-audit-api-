# 協議結果：両建て損益計算機 v3（2026-10-25 20:10 agentCL集約）

参加：Claude（CL）・Gemini（GE・Zapier経由2回）・Copilot（PR #4 `consultations/calculator_v3_copilot.md`）・ChatGPT（Notion「協議依頼：両建て損益計算機v3（ChatGPT宛）」）

## 合意
- 価格損益の中心式（仲値＋スプレッド半分）は正しい：Claude・Copilot・ChatGPTが展開で一致を確認。Geminiは「反対」だが具体的な誤りの指摘なし→多数で正しいと判定
- 検算例4件（−70円・1:3＝1.4pips・あと7.4pips・−4,662円）：Copilot・ChatGPTが再計算で一致

## v4で反映した修正
| 修正 | 指摘元 |
|---|---|
| 残高の起点を「両建て前の残高」に明記（二重計上防止） | ChatGPT・Copilot |
| ロスカット・MCまでの値動きに方向と、価格に伴う証拠金変化を反映（概算と明記） | Gemini・ChatGPT・Copilot |
| ゼロ口座手数料を「取引額10万USDごとに10ドル」で取引額に比例（GOLD・EURUSDは1lot10ドルより大きい） | ChatGPT（XM公式で確認） |
| 損益が同額の時は決済候補なし、両側マイナス時は比率なし | ChatGPT・Copilot |
| ゼロ口座のレバレッジ＝8万ドルまで500倍、KIWAMI極のスワップフリー、同量両建て証拠金ゼロはFX・金・銀 | ChatGPT（XM公式） |
| スワップ日数を「課金日数（3日分の日は3）」に変更 | ChatGPT・Copilot |
| フルロット・ロスカットに「概算」表示、目標利益＝決済側＋残存側の合計と明記 | ChatGPT・Copilot |

## 保留（次の段階）
- MT5の実際の銘柄仕様（契約サイズ・tick value・スワップ日程）と口座値の自動取得、OrderCalcProfitとの照合：MT5接続後に実施
- 実約定価格の入力・予測と実績の差の表示：デモ照合後に検討
- XMのGOLD仕様（100オンス・1pips＝0.1）と不等量両建ての証拠金：未確認のまま（MT5の銘柄仕様で確認）

## 共通の注意（ChatGPT・Copilot）
この決済ルールに収益上の優位性があるかは式だけでは判定できない。実ティック・実コストの検証とデモ照合が必要。
