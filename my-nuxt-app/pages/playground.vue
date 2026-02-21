<script setup lang="ts">
const title = ref('Nuxt Playground');
const note = ref('ここで自由に試せます');
const count = ref(0);

const upperTitle = computed(() => title.value.toUpperCase());

const resetAll = () => {
  title.value = 'Nuxt Playground';
  note.value = 'ここで自由に試せます';
  count.value = 0;
};
</script>

<template>
  <main class="playground">
    <header class="hero">
      <h1>Playground</h1>
      <p>検証・実験用のページです。自由に値を変えて挙動を確認できます。</p>
      <NuxtLink to="/" class="back-link">トップに戻る</NuxtLink>
    </header>

    <section class="grid">
      <article class="card">
        <h2>リアクティブ入力</h2>
        <label class="field">
          タイトル
          <input v-model="title" type="text" />
        </label>
        <label class="field">
          メモ
          <textarea v-model="note" rows="4" />
        </label>
      </article>

      <article class="card">
        <h2>カウンター</h2>
        <p class="count">{{ count }}</p>
        <div class="actions">
          <button type="button" @click="count--">-1</button>
          <button type="button" @click="count++">+1</button>
          <button type="button" @click="resetAll">リセット</button>
        </div>
      </article>

      <article class="card preview">
        <h2>プレビュー</h2>
        <p><strong>title:</strong> {{ title }}</p>
        <p><strong>title(upper):</strong> {{ upperTitle }}</p>
        <p><strong>note:</strong> {{ note }}</p>
      </article>
    </section>
  </main>
</template>

<style scoped>
.playground {
  max-width: 1200px;
  margin: 0 auto;
  color: white;
}

.hero {
  text-align: center;
  padding: 2rem 0;
}

.hero h1 {
  margin-bottom: 0.75rem;
}

.hero p {
  margin-bottom: 1rem;
}

.back-link {
  color: white;
  text-decoration: underline;
}

.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
}

.card {
  background: white;
  color: #333;
  border-radius: 12px;
  padding: 1.5rem;
  box-shadow: 0 10px 30px rgba(0, 0, 0, 0.1);
}

.field {
  display: grid;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.field input,
.field textarea,
.actions button {
  width: 100%;
  border: 1px solid #ddd;
  border-radius: 8px;
  padding: 0.6rem 0.75rem;
  font: inherit;
}

.count {
  font-size: 2rem;
  font-weight: 700;
  margin: 0 0 1rem;
}

.actions {
  display: grid;
  gap: 0.5rem;
}

.preview p {
  line-height: 1.6;
}
</style>
