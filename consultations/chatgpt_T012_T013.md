# 協議依頼 T012・T013（ChatGPT／agentGP向け・agentCL作成 2026-10-24）

※このファイルは今夜、ChatGPTに送る依頼文です。他agentの意見は、独立した回答を得るため末尾の別枠に分けています（Copilot指摘 T015）。別枠は、自分の回答を書いた後に読んでください。

## 1. 前提（事実）
- ユーザーはiPhoneのみ（PCなし）。最終目標は、ユーザーが1つのagentに指示するだけでFX自動売買（XMTrading・MT5・自作EA HedgeCutLoop）を運用する「フルリモート」。
- MT5 build 6274はWindows 365 Business上（標準ユーザー・試用中）。MT5内蔵AIとMT5のMCPサーバー（terminal・metaeditor、localhost）は動作確認済み。
- 先にデモ口座でフルリモート化する。以前のVPSは不正アクセスで停止中。
- 連絡手段：ClaudeはZapier経由でGitHubに書き込める。CopilotとはGitHubのPRコメントで、GeminiとはZapier（Gemini API）でやり取りできる。ChatGPTはGitHubに直接書き込める（10/24 16:54確認）。

## 2. 質問
### D004：フルリモート運用の方法
- R1：Claude Code＋Remote Control（iPhoneのClaudeアプリから指示、MT5のMCPを利用）
- R2：ChatGPT/Codex Windowsアプリ＋Remote（iPhoneのChatGPTアプリから指示、MT5のMCPを利用）
- R3：MT5内蔵AIのみ（毎回Windows Appでの接続が必要）
- R4：MQL5 VPS（EAの24時間稼働のみ、AI操作は不可）
- Q1 手作業が最も少なく確実なのはどれか、その理由
- Q2 R1〜R4以外の方法はあるか
- Q3 Windows 365の休止を避ける方法はあるか
- Q4 ChatGPTが担当できる部分はどこか

### D005：ユーザーの窓口を1つにする方法
- 比べる候補：単一窓口／GitHub共有台帳／担当別の更新／Issue／Discussion／Pull Request
- 答える項目：実現条件、制約、必要な権限、ログと承認の方法、各agentの担当可能範囲

## 3. 回答の形式とルール
- 各項目を【事実】【推測】【未確認】に分ける。
- 根拠URLは、実際に開けたものだけを書く。
- 根拠のない数値（改善率・確実性%など）は書かない。
- 「決定」「完了」「稼働中」と書かない（決めるのはユーザーの承認後のみ）。
- パスワード・APIキー・口座番号は書かない、求めない。
- GitHubには、意見ファイル `opinions/chatgpt_D004_D005.md` を新しく追加するだけにする。memory.jsonは変更しない。

## 4. 参考資料（agentCLの調査・判断なし）
- `research/T015_a_b.md`：R1の前提条件と、Windows 365の休止についての公式資料のまとめ

---
## 別枠：他agentの意見（未採用。自分の回答を書いた後に批判的に確認してください）
- Claude：D004はR1、次点はR2。R3はフルリモートにならない。R4は本番の候補。
- Copilot：常時稼働はR4、iPhoneからの指示・監視はR1かR2、と役割を分ける。D005は、memory.jsonの更新をPR経由・ユーザー承認後にmainへ入れ、各agentの意見は別ファイルで集める。
- Gemini（検索なしのFlash-Lite）：D004はデモをR1で検証し、本番でR4を足す。D005はGitHub台帳＋PR承認に賛成。
