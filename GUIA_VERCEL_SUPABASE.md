# 🚀 GUIA DE HOSPEDAGEM: VERCEL + SUPABASE (GRATUITO)

Este guia explica como colocar a sua plataforma **MG Editáveis** no ar gratuitamente utilizando:
- **Vercel**: Hospedagem global de alta performance (Frontend + API Serverless).
- **Supabase**: Banco de dados PostgreSQL na nuvem 100% gratuito para salvar usuários, CNHs, recargas e configurações.

---

## 📋 Pré-requisitos
1. Uma conta gratuita no **[Supabase](https://supabase.com)**.
2. Uma conta gratuita na **[Vercel](https://vercel.com)**.
3. O código deste projeto enviado para um repositório no **GitHub** (ou usar a Vercel CLI).

---

## 🛠️ PASSO 1: Configurar o Banco no Supabase (2 minutos)

1. Faça login no [Supabase](https://supabase.com) e clique em **New Project**.
2. Escolha um nome para o projeto (ex: `mgeditaveis`), defina uma senha e selecione uma região (ex: `São Paulo (sa-east-1)`).
3. No menu lateral esquerdo, clique no ícone **SQL Editor** (ou prima `Ctrl+K` e digite `SQL`).
4. Abra o arquivo **`supabase_setup.sql`** que está na raiz deste projeto.
5. Copie **todo o conteúdo** dele, cole no editor SQL do Supabase e clique no botão verde **Run** (Executar).
6. Pronto! A tabela `mgeditaveis_db` foi criada e **todos os seus 5 usuários e 52 CNHs já foram importados automaticamente**.

---

## 🔑 PASSO 2: Pegar as Chaves de Conexão do Supabase

1. No menu lateral do Supabase, clique no ícone de engrenagem **Project Settings** (Configurações do Projeto).
2. Clique na aba **Data API** (ou **API**).
3. Copie os dois valores abaixo:
   - **Project URL** (ex: `https://xyzabc123.supabase.co`)
   - **Project API Keys** -> chave **`anon` `public`** (começa com `eyJhbGci...`)

---

## 🌐 PASSO 3: Subir na Vercel

### Opção A: Pelo Painel da Vercel (Recomendado via GitHub)

1. Suba esta pasta do projeto para o seu repositório no [GitHub](https://github.com).
2. Acesse a [Vercel](https://vercel.com) e clique em **Add New...** -> **Project**.
3. Conecte sua conta do GitHub e selecione o repositório deste projeto.
4. Na tela de configuração de Deploy, abra a seção **Environment Variables** (Variáveis de Ambiente) e adicione as 2 chaves:
   - Nome: `SUPABASE_URL` | Valor: *(Cole a URL do seu Supabase copiada no Passo 2)*
   - Nome: `SUPABASE_KEY` | Valor: *(Cole a chave anon copiada no Passo 2)*
5. Clique no botão azul **Deploy**.
6. Em cerca de 30 segundos, seu site estará 100% ativo com SSL gratuito!

---

### Opção B: Pela Vercel CLI (Via Terminal)

Se preferir subir direto pelo terminal:
```bash
npm install -g vercel
vercel
```
Siga os prompts na tela e depois adicione as variáveis de ambiente com:
```bash
vercel env add SUPABASE_URL
vercel env add SUPABASE_KEY
vercel --prod
```

---

## ✅ PASSO 4: Testar e Acessar Online

Após o deploy, a Vercel fornecerá um link como `https://seu-projeto.vercel.app`.

### Links Principais:
- 📊 **Painel Administrativo**: `https://seu-projeto.vercel.app/admin.html` (ou `/admin`)
- 🔑 **Tela de Login / Cadastro**: `https://seu-projeto.vercel.app/login`
- 📄 **Criar CNH**: `https://seu-projeto.vercel.app/criar-cnh`
- 📱 **Web App Mobile**: `https://seu-projeto.vercel.app/index.html`
- 🩺 **API Healthcheck**: `https://seu-projeto.vercel.app/api`

---

## 🔐 Credenciais Padrão de Acesso:

- **Painel Administrativo / Master**:
  - E-mail / Usuário: `MG` ou `moritzpj@gmail.com`
  - Senha: `Comida12.@` ou `840169`
  - Chave Cloaker (se ativada): `key=adm_171`

---

## 💡 Dúvidas Frequentes

- **O que acontece se eu atualizar o código no GitHub?**  
  A Vercel atualiza o site automaticamente em segundos sem apagar nada do banco, pois os dados ficam seguros no Supabase.

- **Posso rodar o projeto localmente com o Supabase?**  
  Sim! Se quiser rodar localmente conectando no Supabase, crie um arquivo `.env` com as mesmas variáveis (`SUPABASE_URL` e `SUPABASE_KEY`) ou continue rodando normalmente com `node server.js`.
