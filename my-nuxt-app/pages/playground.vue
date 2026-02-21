<script setup lang="ts">
const title = ref('Nuxt Playground');
const note = ref('ここで自由に試せます');
const count = ref(0);
const apiUrl = ref('/api');
const isLoading = ref(false);
const responseStatus = ref<number | null>(null);
const responseBody = ref('');
const responseError = ref('');

const upperTitle = computed(() => title.value.toUpperCase());

const resetAll = () => {
  title.value = 'Nuxt Playground';
  note.value = 'ここで自由に試せます';
  count.value = 0;
};

const runApiTest = async () => {
  isLoading.value = true;
  responseError.value = '';
  responseStatus.value = null;
  responseBody.value = '';

  try {
    const result = await fetch(apiUrl.value, { method: 'GET' });
    const text = await result.text();

    responseStatus.value = result.status;

    try {
      responseBody.value = JSON.stringify(JSON.parse(text), null, 2);
    } catch {
      responseBody.value = text;
    }

    if (!result.ok) {
      responseError.value = 'HTTPエラーが返されました';
    }
  } catch (error) {
    responseError.value = error instanceof Error ? error.message : '通信に失敗しました';
  } finally {
    isLoading.value = false;
  }
};
</script>

<template>
  <main class="playground">
    <header class="playground__hero">
      <h1 class="playground__title">Playground</h1>
      <p class="playground__lead">検証・実験用のページです。自由に値を変えて挙動を確認できます。</p>
      <NuxtLink to="/" class="playground__back-link">トップに戻る</NuxtLink>
    </header>

    <section class="playground__grid">
      <article class="playground__card">
        <h2 class="playground__card-title">リアクティブ入力</h2>
        <label class="playground__field">
          <span class="playground__field-label">タイトル</span>
          <input v-model="title" type="text" class="playground__input" />
        </label>
        <label class="playground__field">
          <span class="playground__field-label">メモ</span>
          <textarea v-model="note" rows="4" class="playground__textarea" />
        </label>
      </article>

      <article class="playground__card">
        <h2 class="playground__card-title">カウンター</h2>
        <p class="playground__count">{{ count }}</p>
        <div class="playground__actions">
          <button type="button" class="playground__button" @click="count--">-1</button>
          <button type="button" class="playground__button" @click="count++">+1</button>
          <button type="button" class="playground__button" @click="resetAll">リセット</button>
        </div>
      </article>

      <article class="playground__card playground__card--preview">
        <h2 class="playground__card-title">プレビュー</h2>
        <p class="playground__preview-line"><strong>title:</strong> {{ title }}</p>
        <p class="playground__preview-line"><strong>title(upper):</strong> {{ upperTitle }}</p>
        <p class="playground__preview-line"><strong>note:</strong> {{ note }}</p>
      </article>

      <article class="playground__card playground__card--api-test">
        <h2 class="playground__card-title">API疎通テスト</h2>
        <label class="playground__field">
          <span class="playground__field-label">URL</span>
          <input
            v-model="apiUrl"
            type="text"
            placeholder="/api/example"
            class="playground__input"
          />
        </label>
        <div class="playground__api-actions">
          <button
            type="button"
            :disabled="isLoading"
            class="playground__button"
            @click="runApiTest"
          >
            {{ isLoading ? '実行中...' : 'GET実行' }}
          </button>
        </div>

        <p v-if="responseStatus !== null" class="playground__result-line">
          <strong>Status:</strong> {{ responseStatus }}
        </p>
        <p v-if="responseError" class="playground__error-line">{{ responseError }}</p>
        <pre v-if="responseBody" class="playground__result-body">{{ responseBody }}</pre>
      </article>
    </section>
  </main>
</template>

<style scoped>
.playground {
  max-width: 1200px;
  margin: 0 auto;
  color: var(--c-bg);
}

.playground__hero {
  text-align: center;
  padding: var(--s-8) 0;
}

.playground__title {
  margin-bottom: var(--s-3);
}

.playground__lead {
  margin-bottom: var(--s-4);
  line-height: var(--lh-base);
}

.playground__back-link {
  color: var(--c-bg);
  text-decoration: underline;
}

.playground__grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: var(--s-6);
}

.playground__card {
  background: var(--c-bg);
  color: var(--c-text);
  border: 1px solid var(--c-border);
  border-radius: var(--r-2);
  padding: var(--s-6);
  box-shadow: var(--sh-1);
}

.playground__card-title {
  margin-bottom: var(--s-3);
  font-size: var(--fs-3);
}

.playground__field {
  display: grid;
  gap: var(--s-2);
  margin-bottom: var(--s-3);
}

.playground__field-label {
  font-size: var(--fs-2);
  color: var(--c-text);
}

.playground__input,
.playground__textarea,
.playground__button {
  width: 100%;
  border: 1px solid var(--c-border);
  border-radius: var(--r-1);
  padding: var(--s-2) var(--s-3);
  font: inherit;
}

.playground__textarea {
  resize: vertical;
}

.playground__button {
  background: var(--c-surface);
  color: var(--c-text);
  cursor: pointer;
}

.playground__api-actions {
  margin-bottom: var(--s-3);
}

.playground__button:disabled {
  opacity: 0.7;
  cursor: wait;
}

.playground__result-line {
  margin-bottom: var(--s-2);
}

.playground__error-line {
  color: var(--c-danger);
  margin-bottom: var(--s-3);
}

.playground__result-body {
  background: var(--c-surface);
  border: 1px solid var(--c-border);
  border-radius: var(--r-1);
  padding: var(--s-3);
  white-space: pre-wrap;
  word-break: break-word;
}

.playground__count {
  font-size: var(--s-8);
  font-weight: var(--fw-bold);
  margin: 0 0 var(--s-3);
}

.playground__actions {
  display: grid;
  gap: var(--s-2);
}

.playground__preview-line {
  line-height: var(--lh-base);
}
</style>
