# FluxoApp — Painel Admin

Painel de administração completo do FluxoApp, hospedado no GitHub Pages.

## 🚀 Como hospedar no GitHub Pages

1. Crie um repositório no GitHub chamado `fluxoapp-painel`
2. Faça upload deste arquivo `index.html` para o repositório
3. Vá em **Settings → Pages**
4. Em **Source**, selecione `Deploy from a branch`
5. Selecione a branch `main` e pasta `/ (root)`
6. Clique em **Save**
7. Aguarde 1-2 minutos e acesse: `https://SEU_USUARIO.github.io/fluxoapp-painel`

## 🔐 Configurar acesso admin no Firebase

1. Acesse o [Console do Firebase](https://console.firebase.google.com)
2. Vá em **Authentication → Users**
3. Clique em **Add user**
4. Crie uma conta com seu email e senha de admin
5. Use esse email/senha para entrar no painel

## ✅ Funcionalidades

- **Dashboard** — Stats em tempo real: total, ativos, trial, expirados
- **Usuários** — Listar, buscar, filtrar, editar, bloquear/desbloquear, +30 dias
- **Cupons** — Criar códigos de dias grátis, desconto ou acesso vitalício
- **Receita** — Estimativa financeira por plano

## 🛡️ Segurança (Firestore Rules)

Configure as regras do Firestore para que apenas usuários autenticados como admin possam escrever:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{uid} {
      allow read, write: if request.auth != null;
    }
    match /cupons/{id} {
      allow read: if request.auth != null;
      allow write: if request.auth != null;
    }
  }
}
```
