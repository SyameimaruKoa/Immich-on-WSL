# 実装履歴

## 2026-03-02

### 変更概要（追記）
- One-Shot 起動方式を取り下げ、安定性重視の Managed Keep-Alive 方式に再変更。

### 変更詳細（追記）
- [deployment.html](deployment.html)
  - Step 5 を `Managed Keep-Alive` 表記へ更新。
  - `Start-Immich.bat` サンプルを更新し、`systemd-run` で `immich-wsl-keepalive` を生成する方式に変更。
  - `stop-keepalive` サブコマンドを追加。
  - タスクスケジューラ登録手順を追記（GUI 手順 + `schtasks` CLI 例）。
- [README.md](README.md)
  - `Operation Notes` を安定性優先方針へ更新。

### 変更概要
- `deployment.html` の Step 5 を、`sleep infinity` による Keep-Alive 方式から One-Shot 起動方式へ変更。
- `README.md` に運用方針と `wsl --exec dbus-launch true` の調査結果を追記。

### 変更詳細
- [deployment.html](deployment.html)
  - 手順名を `Windows側 自動起動設定 (One-Shot Start)` に変更。
  - `Start-Immich.bat` サンプルを刷新し、以下を実装。
    - `-h` / `--help` ヘルプ表示
    - 未引数時ヘルプ表示 + `pause`
    - `start` / `status` サブコマンド
    - `sleep infinity` 廃止
- [README.md](README.md)
  - `Operation Notes` 追加。
  - `wsl --exec dbus-launch true` 調査セクションを追加。
  - 実装履歴ファイルへのリンクを追加。

### 調査メモ
- `dbus-launch` man page の `NOTES` に「`dbus-launch myapp` 実行時、`myapp` 終了後も `dbus-daemon` は自動終了しない」旨の記載あり。
- そのため、WSL で `dbus-launch true` を使うと、子プロセスが残ってディストリビューションが継続動作する状況は妥当。
