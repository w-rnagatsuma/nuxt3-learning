# Nuxt Minimal Starter

Look at the [Nuxt documentation](https://nuxt.com/docs/getting-started/introduction) to learn more.

## Setup

Make sure to install dependencies:

```bash
# npm
npm install

# pnpm
pnpm install

# yarn
yarn install

# bun
bun install
```

## Development Server

Start the development server on `http://localhost:3000`:

```bash
# npm
npm run dev

# pnpm
pnpm dev

# yarn
yarn dev

# bun
bun run dev
```

## Production

Build the application for production:

```bash
# npm
npm run build

# pnpm
pnpm build

# yarn
yarn build

# bun
bun run build
```

Locally preview production build:

```bash
# npm
npm run preview

# pnpm
pnpm preview

# yarn
yarn preview

# bun
bun run preview
```

Check out the [deployment documentation](https://nuxt.com/docs/getting-started/deployment) for more information.

## 運用ルール

### コンポーネントの配置ルール

プロジェクトでは、コンポーネントを以下の3つのディレクトリに分けて管理します：

#### `components/base/`

- **用途**: 汎用的な基本コンポーネント
- **基準**: 2回以上使用される、または今後再利用が見込まれるコンポーネント
- **例**: ボタン、入力フォーム、カード、モーダルなど
- **命名規則**: `Base` + 機能名（例: `BaseButton.vue`, `BaseCard.vue`）

#### `components/parts/`

- **用途**: ページ固有のパーツコンポーネント
- **基準**: 特定のページや機能でのみ使用される、再利用性の低いコンポーネント
- **例**: ヘッダー、フッター、セクション固有のコンポーネント
- **命名規則**: 機能を表す名前（例: `Header.vue`, `Footer.vue`）

#### `components/feature/`

- **用途**: 特定の機能に関連するコンポーネント群
- **基準**: ビジネスロジックを含む機能単位のコンポーネント
- **ディレクトリ構成**: 機能ごとにサブディレクトリを作成（例: `feature/top/`, `feature/user/`）
- **命名規則**: 機能を表す名前（例: `feature/top/Welcome.vue`）

### `composables/` vs `utils/`

#### `composables/`

- **用途**: Vue/Nuxtの機能を活用したReactive（リアクティブ）なロジック
- **特徴**:
  - `ref`, `computed`, `reactive` などの Vue API を使用
  - コンポーネントのライフサイクルに依存する処理
  - 状態管理や副作用を含む
- **命名規則**: `use` + 機能名（例: `useUser.ts`, `useAuth.ts`）

#### `utils/`

- **用途**: 純粋な関数や汎用的なヘルパー関数
- **特徴**:
  - Vueに依存しない純粋なJavaScript/TypeScript関数
  - 入力に対して常に同じ出力を返す（副作用がない）
  - プロジェクト外でも使える汎用的な処理
- **命名規則**: 機能を表す名前（例: `format.ts`, `validation.ts`）

### 粒度ルール

**「2回使ったらbase」の原則**

- 同じようなコンポーネントを2回以上実装する場合は、`components/base/` に共通コンポーネントを作成
- 最初は `parts/` で実装し、再利用の必要性が出た時点で `base/` へリファクタリング
- 過度な抽象化は避け、実際の再利用ニーズを確認してから共通化する

### 命名規則

#### ファイル名

- コンポーネント: PascalCase（例: `BaseButton.vue`, `UserProfile.vue`）
- composables: camelCase with `use` prefix（例: `useAuth.ts`, `useUser.ts`）
- utils: camelCase（例: `format.ts`, `validation.ts`）

#### 変数・関数

- 変数: camelCase（例: `userName`, `isActive`）
- 関数: camelCase（例: `fetchUser()`, `formatDate()`）
- 定数: UPPER_SNAKE_CASE（例: `API_BASE_URL`, `MAX_RETRY_COUNT`）
- 型定義: PascalCase（例: `User`, `ApiResponse`）

#### コンポーネント内

- Props: camelCase（例: `userName`, `isDisabled`）
- Emits:
  - カスタムイベント: kebab-case（例: `click-button`, `submit-form`）
  - v-model用: `update:` + camelCase（例: `update:modelValue`, `update:userName`）
