---
name: dark-mode-strategy
description: Stratégies d'implémentation du dark mode, retours et patterns
---
## Approches

### 1. CSS Custom Properties (recommandée)
```css
:root {
  --bg: #ffffff;
  --text: #1a1a1a;
}
[data-theme="dark"] {
  --bg: #1a1a1a;
  --text: #f0f0f0;
}
```

### 2. Tailwind CSS `dark:` variant
```html
<div class="bg-white dark:bg-gray-900 text-gray-900 dark:text-gray-100">
```
Nécessite `darkMode: 'class'` ou `'media'` dans tailwind.config

### 3. CSS `prefers-color-scheme`
```css
@media (prefers-color-scheme: dark) {
  :root { /* dark vars */ }
}
```
Mais pas de toggle manuel possible seul.

## Implémentation

### Script d'init (avant le render, pour éviter le flash)
```html
<script>
  const theme = localStorage.getItem('theme')
    || (window.matchMedia('(prefers-color-scheme: dark)').matches ? 'dark' : 'light');
  document.documentElement.setAttribute('data-theme', theme);
</script>
```

### Toggle
```js
function toggleTheme() {
  const next = document.documentElement.getAttribute('data-theme') === 'dark' ? 'light' : 'dark';
  document.documentElement.setAttribute('data-theme', next);
  localStorage.setItem('theme', next);
}
```

## Palette dark mode
```css
[data-theme="dark"] {
  --bg: #0a0a0a;
  --bg-secondary: #1a1a1a;
  --bg-tertiary: #2a2a2a;
  --text: #e5e5e5;
  --text-secondary: #a3a3a3;
  --border: #333333;
  --primary: #...; /* version dark */
}
```

À enrichir après chaque projet.
