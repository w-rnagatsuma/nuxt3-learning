# Copilot Prompt: Nuxt/Vue CSS設計（scoped + BEM + tokens）へ整える

あなたは Nuxt/Vue プロジェクトのCSS設計を改善するリファクタ担当です。
目的は「壊れにくく、迷いにくく、統一感があり、変更に強いCSS」にすることです。

## 前提

- Nuxt プロジェクト
- Tailwind は使わない
- 基本は `<style scoped>` を使用
- SCSS は使わない（素のCSS）
- 既存のコンポーネントにバラバラなCSSが存在する想定

---

## ゴール（最終状態）

1. **Design Tokens（CSS変数）** を `assets/styles/tokens.css` に定義し、全体から `var(--token)` で参照できる
2. グローバルCSSは **tokens と base だけ**（リセット/タイポなど最小）
3. それ以外の見た目は **各コンポーネントの `<style scoped>` に閉じる**
4. クラス命名は **BEM** で統一（`block`, `block__element`, `block--modifier`）
5. CSSは **浅いセレクタ**（基本クラス1つ）で当てる。深い子孫セレクタは避ける
6. 色/余白/角丸/文字サイズなどの **直書きを減らし tokens に寄せる**
7. 「共通UI」は可能なら CSS共通化より **コンポーネント化**（例: BaseButton）を優先

---

## まず作るファイル（必須）

### 1) assets/styles/tokens.css

以下を初期値の例として作成（必要に応じて追加して良いが、むやみに増やさない）

```css
:root {
  /* colors */
  --c-text: #111827;
  --c-muted: #6b7280;
  --c-bg: #ffffff;
  --c-surface: #f9fafb;
  --c-border: #e5e7eb;
  --c-primary: #2563eb;
  --c-danger: #dc2626;

  /* spacing (4px scale) */
  --s-1: 4px;
  --s-2: 8px;
  --s-3: 12px;
  --s-4: 16px;
  --s-6: 24px;
  --s-8: 32px;

  /* radius */
  --r-1: 6px;
  --r-2: 10px;

  /* typography */
  --fs-1: 12px;
  --fs-2: 14px;
  --fs-3: 16px;
  --fw-regular: 400;
  --fw-bold: 700;
  --lh-base: 1.6;

  /* shadow */
  --sh-1: 0 1px 2px rgba(0, 0, 0, 0.06);
}
```
