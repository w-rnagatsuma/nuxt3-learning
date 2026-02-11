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

/* ヒーローセクション - ページ上部の目立つエリア */
.hero {
  text-align: center;
  padding: 3rem 0;
  color: white;
}

.subtitle {
  font-size: 1.5rem;
  opacity: 0.9;
  margin-bottom: 3rem;
}

.features {
  display: grid; /* グリッドレイアウト。「行×列」の格子状に配置 */
  /* 
   * 列の定義
   * repeat: 同じ列指定の繰り返し
   * auto-fit: 利用可能なスペースに合わせて自動的に列数を調整
   * minmax(250px, 1fr): 各列の幅は最小250px、最大は利用可能なスペースに応じて調整。1fr=fraction(1fr 2frなら1:2の割合でスペースを分割)
  */
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr)); 
  gap: 2rem;
  margin-bottom: 4rem;
}

.feature-card {
  background: white;
  border-radius: 12px;
  padding: 2rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1); /* 水平方向のズレ、垂直方向のズレ、ぼかしの半径、影の色 */
  transition: transform 0.3s ease, box-shadow 0.3s ease; /* トランジション効果 */
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: 0px 10px 40px rgba(0, 0, 0, 0.45); /* ホバー時の影の変化 */
}

.feature-card h3 {
  font-size: 1.5rem;
  margin-bottom: 0.5rem;
  color: #333;
}

.feature-card p {
  color: #666;
  line-height: 1.6;
  margin-bottom: 1rem;
}
</style>