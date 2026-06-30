# Farcaster Mini App 対応メモ（Wise World 2）

GitHub Pages 公開のWebアプリを **Farcaster Mini App** としても動くように改修済み。

## 追加・変更したもの
- `index.html` `<head>`：`fc:miniapp` メタタグ（＋旧互換 `fc:frame`）。タイムラインで画像＋ボタンのカードになりタップで起動。
- `index.html` `</body>` 直前：`@farcaster/miniapp-sdk` を esm.sh から動的importし `sdk.actions.ready()`。Farcaster外/オフラインは try/catch で無害スキップ。
- `icons/farcaster-embed.png`：3:2 埋め込みカード画像（青グラデ＋アイコン）。
- `.well-known/farcaster.json`：Mini App身分証（**未署名**）。
- `sw.js`：CACHE を v9→v10 に更新。

## 残作業（ユーザー操作）
1. **manifest署名**：`https://farcaster.xyz/~/developers/mini-apps/manifest` で署名し `accountAssociation` を追記（FID必要）。
2. **ドメイン注意**：farcaster.json はドメイン直下でないと「追加・通知・発見」が無効。現状サブパス配下のためカード表示＆起動は可・完全独立公開には独自ドメイン要。
3. **検証**：`https://farcaster.xyz/~/developers/mini-apps/embed` に公開URLを貼って確認。
