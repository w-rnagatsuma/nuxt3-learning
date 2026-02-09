<template>
  <main class="welcome">
    <section class="content">
      <header class="hero">
        <h1>Nuxt3学習</h1>
        <p class="subtitle">Nuxt3の基礎を学ぶためのアプリケーション</p>  
      </header>
      <section class="features">
        <article class="feature-card">
          <h3>お問い合わせ</h3>
          <p>質問やフィードバックがあれば、遠慮なくお問い合わせください</p>
        </article>

        <article class="feature-card">
          <h3>データリスト</h3>
          <p>データの一覧表示と管理が簡単に行えます</p>
        </article>

        <article class="feature-card">
          <h3>公式ドキュメント</h3>
          <p>公式のNuxt3ドキュメントへのリンクやリソースを提供します</p>
        </article>
      </section>
    </section>
  </main>
</template>

<style scoped>
.welcome {
  min-height: 100vh; /* viewport height 画面の高さ100%（表示領域全体） */
  background: linear-gradient(135deg, #667eea, #764ba2); /* グラデーション　斜め方向　0%から青　100%で紫 */
  padding: 2rem; /* root em ルートfontサイズの2倍の余白 */
  font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen, Ubuntu, Cantarell, sans-serif;
}

.content {
  max-width: 1200px; /* 最大幅1200px 一般的によく使われるらしい */
  margin: 0 auto;
}

.hero {
  text-align: center;
  padding: 3rem 0;
  color: white;
}
</style>