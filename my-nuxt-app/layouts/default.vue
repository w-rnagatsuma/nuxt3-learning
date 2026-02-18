<template>
  <div>
    <NuxtRouteAnnouncer />
    <main class="app-shell">
      <slot />
    </main>
  </div>
</template>

<style scoped>
/**
 * scopedの書き方ルール
 * - コンポーネントの見た目は各ファイルで完結させる
 *   - グローバルに書くのはtokensとbaseだけ
 * - セレクタは浅く
 * - 親から子のスタイルを上書きするのは避ける
 *   - 代わりにpropsで見た目バリエーションを渡す（後でBEMでやる）
 */

.app-shell {
  min-height: 100vh; /* viewport height 画面の高さ100%（表示領域全体） */
  background: linear-gradient(
    135deg,
    #667eea,
    #764ba2
  ); /* グラデーション 斜め方向 0%から青 100%で紫 */
  padding: 2rem; /* root em ルートfontサイズの2倍の余白 */
  font-family:
    -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
}
</style>
