# ScalableAngular

This project was generated using [Angular CLI](https://github.com/angular/angular-cli) version 19.2.13.

## Development server

To start a local development server, run:

```bash
ng serve
```

Once the server is running, open your browser and navigate to `http://localhost:4200/`. The application will automatically reload whenever you modify any of the source files.

## Code scaffolding

Angular CLI includes powerful code scaffolding tools. To generate a new component, run:

```bash
ng generate component component-name
```

For a complete list of available schematics (such as `components`, `directives`, or `pipes`), run:

```bash
ng generate --help
```

## Building

To build the project run:

```bash
ng build
```

This will compile your project and store the build artifacts in the `dist/` directory. By default, the production build optimizes your application for performance and speed.

## Running unit tests

To execute unit tests with the [Karma](https://karma-runner.github.io) test runner, use the following command:

```bash
ng test
```

## Running end-to-end tests

For end-to-end (e2e) testing, run:

```bash
ng e2e
```

Angular CLI does not come with an end-to-end testing framework by default. You can choose one that suits your needs.

## Additional Resources

For more information on using the Angular CLI, including detailed command references, visit the [Angular CLI Overview and Command Reference](https://angular.dev/tools/cli) page.





##################################################
##################################################
##################################################





# Diagramas do Projeto Angular Escalável

## 1. Estrutura de Pastas

```text
src/
 └── app/
      ├── core/          # Serviços principais, interceptadores, guards
      │     ├── auth.guard.ts
      │     ├── auth.interceptor.ts
      │     └── api.service.ts
      ├── shared/       # Componentes e serviços reutilizáveis
      │     └── ...
      ├── features/     # Módulos por funcionalidade
      │     ├── auth/
      │     │     ├── auth.module.ts
      │     │     └── login/
      │     │           └── login.component.ts
      │     └── dashboard/
      │           ├── dashboard.module.ts
      │           └── home/
      │                 └── home.component.ts
      ├── app-routing.module.ts
      └── app.module.ts
```

---

## 2. Diagrama de Fluxo — Autenticação

```text
Usuário → LoginComponent → AuthService → API → Token (localStorage)
                       ↓
                    Router → Dashboard
```

**Explicação:**
- Usuário preenche login.
- `AuthService` faz chamada HTTP via `ApiService`.
- Recebe token → armazena no `localStorage`.
- Redireciona para `Dashboard`.

---

## 3. Diagrama de Comunicação — Interceptador HTTP

```text
HttpClient → AuthInterceptor → API
                       ↓
             (Adiciona Header Authorization)
```

**Explicação:**
- Toda requisição passa pelo `AuthInterceptor`.
- Token JWT é adicionado no cabeçalho `Authorization`.

---

## 4. Fluxo de Rotas

```text
'' → /dashboard
     ↳ lazy load → DashboardModule

'/auth' → lazy load → AuthModule
           ↳ /auth/login → LoginComponent

Proteção → AuthGuard → se não autenticado → /auth/login
```

**Explicação:**
- Rotas organizadas com `lazy loading`.
- `AuthGuard` protege rotas de usuários não autenticados.

---

## 5. Diagrama de Deploy

```text
Local Dev → Git → GitHub → GitHub Pages → Deploy Prod

Testes: Karma/Jasmine + Cypress
Lint: ESLint
CI/CD: opcional via GitHub Actions
```

**Explicação:**
- Desenvolvimento local.
- Versionamento com Git.
- Deploy automático para GitHub Pages.




