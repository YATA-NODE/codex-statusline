# codex-statusline

WSL2 で使う Codex TUI 向けの、コンパクトなステータスライン設定例です。

モデル、コンテキスト使用量、5時間制限、週間制限、コンテキストウィンドウをフッターにまとめて表示します。

```text
gpt-5.5 default · Context 13% used · 5h 84% left · weekly 71% left · 258K window
```

この表示は横に長いため、README にフル幅のスクリーンショットを貼ると読みにくくなります。基本的には上のようにテキスト例で示すか、スクリーンショットを使う場合はターミナル下部だけを切り抜くのがおすすめです。

## 前提

- TUI のステータスライン設定に対応した Codex CLI
- WSL2
- WSL2 の Linux 環境内にある `~/.codex/config.toml`

WSL2 では、`~/.codex/config.toml` は Windows 側ではなく、利用している Linux ディストリビューション内のパスを指します。

例:

```text
/home/<linux-user>/.codex/config.toml
```

Codex CLI が Windows 側の設定を読んでいる場合を除き、`C:\Users\<windows-user>\.codex\config.toml` のような Windows 側のパスではなく、WSL2 側の設定ファイルを編集してください。

## 導入方法

まず、既存の Codex 設定をバックアップします。

```bash
cp ~/.codex/config.toml ~/.codex/config.toml.bak
```

設定ファイルを開きます。

```bash
nano ~/.codex/config.toml
```

次の設定を追加、または既存の `[tui]` セクションを更新してください。

```toml
[tui]
status_line = [
  "model-with-reasoning",
  "context-used",
  "five-hour-limit",
  "weekly-limit",
  "context-window-size",
]
status_line_use_colors = true
```

保存後、Codex を再起動してください。

## `/statusline` で設定する方法

Codex TUI 内の `/statusline` から同じ内容を設定することもできます。

1. Codex を起動します。
2. `/statusline` を実行します。
3. 次の項目を選び、同じ順番に並べます。
   - `model-with-reasoning`
   - `context-used`
   - `five-hour-limit`
   - `weekly-limit`
   - `context-window-size`
4. 選択内容を保存します。

保存すると、Codex が `~/.codex/config.toml` に設定を反映します。

## 補足

Codex のステータスラインは、Codex に組み込まれている item ID を並べて設定します。このリポジトリは外部レンダラーやシェルスクリプトをインストールするものではありません。

利用中の Codex が上記の item ID を認識しない場合は、Codex を更新するか、`/statusline` のメニューから近い項目を選んでください。

## ライセンス

MIT
