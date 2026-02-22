<script setup lang="js"></script>

<template>
  <main class="practice">
    <!-- ページヘッダー -->
    <header class="practice__header">
      <div class="practice__heading">
        <h1 class="practice__title">User</h1>
        <p class="practice__description">Manage registered users</p>
      </div>
      <button type="button" class="practice__primary-button">Add User</button>
    </header>

    <!-- 検索・絞り込み -->
    <section>
      <input type="text" placeholder="Search by name or email" />
      <select>
        <option value="">all</option>
        <option value="active">active</option>
        <option value="invited">invited</option>
        <option value="suspended">suspended</option>
      </select>
      <button type="button">clear</button>
    </section>

    <!-- ユーザーリスト（テーブル版） -->
    <section>
      <!-- 0件時 -->
      <p>No users found</p>

      <!-- 1件以上時 -->
      <table>
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Email</th>
            <th scope="col"><span class="sr-only">Status</span></th>
            <th scope="col">Details</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>
              <strong>John Doe</strong>
              <small>john.doe@example.com</small>
            </td>
            <td>
              <span>Active</span>
            </td>
            <td>
              <button type="button">Details</button>
            </td>
          </tr>
        </tbody>
      </table>

      <table>
        <thead>
          <tr>
            <th scope="col">Name</th>
            <th scope="col">Email</th>
            <th scope="col"><span class="sr-only">Status</span></th>
            <th scope="col">Details</th>
          </tr>
        </thead>
        <tbody>
          <tr>
            <td>John Doe</td>
            <td>john.doe@example.com</td>
            <td>Active</td>
            <td>
              <button type="button">Details</button>
            </td>
          </tr>
        </tbody>
      </table>
    </section>

    <!-- ユーザーリスト（カード版） -->
    <section>
      <ul>
        <li>
          <article>
            <div>
              <strong>Jane Doe</strong>
              <small>jane.doe@example.com</small>
            </div>
            <div>
              <span>Active</span>
              <button type="button">Details</button>
            </div>
          </article>
        </li>
      </ul>
    </section>

    <!-- ページング -->
    <nav>
      <button type="button">Prev</button>
      <span>Page 1</span>
      <button type="button">Next</button>
    </nav>
  </main>
</template>

<style scoped>
/* Block */
.practice {
  padding: var(--s-2);
  background: var(--c-bg);
  color: var(--c-text);
  font-family: var(--ff-base);
}

/* Header */
.practice__header {
  display: flex;
  align-items: flex-start;
  justify-content: space-between;
  gap: var(--s-4);
  padding: var(--s-4);
  background: var(--c-surface);
  border: 1px solid var(--c-border);
  border-radius: var(--r-1);
  box-shadow: var(--sh-1);
}

.practice__heading {
  display: grid;
  gap: var(--s-1);
}

.practice__title {
  margin: var(--s-0);
  font-size: var(--fs-5);
  font-weight: var(--fw-bold);
  letter-spacing: var(--ls-tight);
}

.practice__discription {
  margin: var(--s-0);
  font-size: var(--fs-2);
  color: var(--c-muted);
}

/* Buttons */
.practice__primary-button {
  appearance: none;
  border: 1px solid var(--c-primary-border);
  background: var(--c-primary);
  color: var(--c-on-primary);
  padding: var(--s-2) var(--s-3);
  border-radius: var(--r-2);
  font-size: var(--fs-2);
  font-weight: var(--fw-bold);
  line-height: var(--lh-base);
  cursor: pointer;
}
</style>
