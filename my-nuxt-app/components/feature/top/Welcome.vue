<template>
  <section class="top-welcome">
    <header class="top-welcome__hero">
      <h1 class="top-welcome__title">Nuxt3学習</h1>
      <p class="top-welcome__subtitle">Nuxt3の基礎を学ぶためのアプリケーション</p>
    </header>
    <section class="top-welcome__cards">
      <article class="top-welcome__card">
        <h3 class="top-welcome__card-title">お問い合わせ</h3>
        <p class="top-welcome__card-text">
          質問やフィードバックがあれば、遠慮なくお問い合わせください
        </p>
      </article>

      <article class="top-welcome__card">
        <h3 class="top-welcome__card-title">データリスト</h3>
        <p class="top-welcome__card-text">データの一覧表示と管理が簡単に行えます</p>
      </article>

      <article class="top-welcome__card">
        <h3 class="top-welcome__card-title">公式ドキュメント</h3>
        <p class="top-welcome__card-text">
          公式のNuxt3ドキュメントへのリンクやリソースを提供します
        </p>
      </article>

      <article class="top-welcome__card">
        <h3 class="top-welcome__card-title">Playground</h3>
        <p class="top-welcome__card-text">検証や実験を気軽に行える遊び場ページです</p>
        <NuxtLink to="/playground" class="top-welcome__card-link">開く</NuxtLink>
      </article>
    </section>
  </section>
</template>

<style scoped>
.top-welcome__hero {
  text-align: center;
  padding: var(--s-8) 0;
  color: var(--c-bg);
}

.top-welcome__title {
  margin-bottom: var(--s-2);
}

.top-welcome__subtitle {
  font-size: var(--fs-3);
  line-height: var(--lh-base);
  opacity: 0.9;
  margin-bottom: var(--s-8);
}

.top-welcome__cards {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: var(--s-6);
  margin-bottom: var(--s-8);
}

.top-welcome__card {
  background: var(--c-bg);
  border: 1px solid var(--c-border);
  border-radius: var(--r-2);
  padding: var(--s-6);
  box-shadow: var(--sh-1);
  transition:
    transform 0.2s ease,
    box-shadow 0.2s ease;
}

.top-welcome__card:hover {
  transform: translateY(-2px);
}

.top-welcome__card-title {
  font-size: var(--fs-3);
  margin-bottom: var(--s-2);
  color: var(--c-text);
}

.top-welcome__card-text {
  color: var(--c-muted);
  line-height: var(--lh-base);
  margin-bottom: var(--s-3);
  font-size: var(--fs-2);
}

.top-welcome__card-link {
  color: var(--c-primary);
  font-weight: var(--fw-bold);
  text-decoration: underline;
}
</style>
