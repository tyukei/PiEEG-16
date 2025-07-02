Raspberry Pi（Ubuntu環境）でAnthropicのAIコーディングアシスタント「Claude Code」を利用するには、以下の手順でセットアップできます。([zenn.dev][1])

---

## ✅ 前提条件

* OS: Ubuntu 20.04以降（Raspberry Pi OS（Debianベース）でも可）
* メモリ: 最低4GB RAM（8GB以上推奨）
* インターネット接続
* Node.js 18以上
* Anthropicアカウント（APIキーまたは有料プラン）([note.com][2], [claudecode.io][3], [itecsonline.com][4])

---

## 🛠️ インストール手順

### 1. システムの更新

```bash
sudo apt update && sudo apt upgrade -y
```



### 2. Node.jsのインストール（v18以上）

```bash
curl -fsSL https://deb.nodesource.com/setup_18.x | sudo -E bash -
sudo apt install -y nodejs
```



インストール後、バージョンを確認します：

```bash
node -v
```



### 3. npmのグローバルパッケージディレクトリの設定（sudoを避けるため）

```bash
mkdir -p ~/.npm-global
npm config set prefix '~/.npm-global'
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc
```



### 4. Claude Codeのインストール

```bash
npm install -g @anthropic-ai/claude-code
```



> ⚠️ `sudo`は使用しないでください。パーミッションエラーの原因となります。

### 5. プロジェクトディレクトリへ移動し、Claude Codeを起動

```bash
cd ~/your-project
claude
```



初回起動時にOAuth認証が求められます。ブラウザが自動で開き、Anthropicアカウントでログインし、アクセスを許可してください。

---

## 🧪 基本的な使い方

* プロジェクトの要約：

```bash
  claude > summarize this project
```



* プロジェクトガイドの生成：

```bash
  claude > /init
```



* コードのバグ修正：([zenn.dev][1])

```bash
  claude > fix the type errors in auth.py
```



* Git操作の支援：

```bash
  claude > commit all changes with message "Add login feature"
```



---

## 💡 補足情報

* Claude Codeは、自然言語での指示により、コードの生成、修正、テスト、ドキュメント作成などを支援します。
* Vimキーバインディングのサポートや、VSCodeとの連携も可能です。
* 詳細な設定や使い方については、[公式ドキュメント](https://docs.anthropic.com/ja/docs/claude-code/setup)を参照してください。([zenn.dev][1], [docs.anthropic.com][5])

---

これで、Raspberry Pi上のUbuntu環境でClaude Codeを利用する準備が整いました。開発作業の効率化にぜひお役立てください。

[1]: https://zenn.dev/arterect/articles/31b08fba9ff818?utm_source=chatgpt.com "WSLで動かすClaude Codeの世界 - Zenn"
[2]: https://note.com/mega_gorilla/n/n52645704880c?utm_source=chatgpt.com "Claude CodeをUbuntuで試してみたけどどうなん？｜猩々博士"
[3]: https://www.claudecode.io/install?utm_source=chatgpt.com "Claude Code Install Guide - Setup & Getting Started"
[4]: https://itecsonline.com/post/how-to-install-claude-code-on-ubuntu-linux-complete-guide-2025?utm_source=chatgpt.com "How to Install Claude Code on Ubuntu Linux: Complete Guide ..."
[5]: https://docs.anthropic.com/ja/docs/claude-code/setup?utm_source=chatgpt.com "Claude Codeのセットアップ - Anthropic"
