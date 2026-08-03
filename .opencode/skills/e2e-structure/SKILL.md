---
name: e2e-structure
description: Structure et conventions pour les tests E2E Playwright
---
## Structure Playwright

```
e2e/
  fixtures/         # Fixtures personnalisées (auth, db)
  page-objects/     # Page Object Model
    LoginPage.ts
    DashboardPage.ts
    CheckoutPage.ts
  specs/            # Tests par feature
    auth.spec.ts
    products.spec.ts
    checkout.spec.ts
  utils/            # Helpers
    test-data.ts
  global-setup.ts   # Setup avant tous les tests
  global-teardown.ts
```

## Page Object Model

```ts
// e2e/page-objects/LoginPage.ts
export class LoginPage {
  constructor(private page: Page) {}

  async goto() { await this.page.goto('/login') }
  async login(email: string, password: string) {
    await this.page.fill('[data-testid="email"]', email)
    await this.page.fill('[data-testid="password"]', password)
    await this.page.click('[data-testid="submit"]')
  }
}
```

## Conventions
- `data-testid` pour les sélecteurs (pas de CSS/XPath fragiles)
- Tests indépendants et idempotents
- Un test = un parcours utilisateur
- Éviter les sleeps, préférer `waitForSelector` / `waitForURL`

## CI
```yaml
- name: E2E tests
  run: npx playwright test
  env:
    BASE_URL: ${{ deploy_url }}
```

À enrichir après chaque projet.
