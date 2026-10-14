# Gestão do Vitor

App pessoal (celular primeiro) para garantir entregas e gerir pessoas: radar do dia, delegações com cobrança pronta para copiar, 1:1 por cadência, decisões, tempo com o time, XP em duas trilhas e assistente Claude.

**Privacidade:** pessoas existem só como código (até 8 caracteres). Não há nome, e-mail, telefone nem anotações sobre pessoas. Títulos e resultados devem ser genéricos.

## Publicar (cerca de 15 minutos)

### 1. Supabase (banco e login)
1. Crie um projeto em supabase.com.
2. SQL Editor: cole o conteúdo de `supabase/schema.sql` e execute.
3. Authentication > Users > Add user: seu e-mail e uma senha forte, marcando **Auto Confirm User**.
4. Authentication > Sign In / Providers: desative **Allow new users to sign up**.
5. Project Settings > API: copie a **Project URL** e a chave **anon / publishable**.

> Já tinha rodado o `schema.sql` antes do diário? Rode só o `supabase/migracao-diario.sql`.

### 2. GitHub
Crie um repositório privado e envie esta pasta (`git init`, `git add .`, `git commit`, `git push`).

### 3. Vercel
1. Importe o repositório (Framework: Next.js, sem mudar nada).
2. Em Environment Variables, cadastre:
   - `NEXT_PUBLIC_SUPABASE_URL`
   - `NEXT_PUBLIC_SUPABASE_ANON_KEY`
   - `ANTHROPIC_API_KEY` (console.anthropic.com)
   - `ALLOWED_EMAIL` (o e-mail do usuário criado)
   - opcional: `CLAUDE_MODEL` (padrão `claude-sonnet-5-5`)
3. Deploy.

### 4. Instalar no celular
Abra o endereço da Vercel no navegador, entre e use "Adicionar à tela inicial".

## Fechar o dia (memória da rotina)
Na tela Radar, botão "Fechar o dia": cole ou suba um .txt/.md com o resumo do dia, o Claude destila (trocando nomes por "uma pessoa"), você aprova e salva. O texto original não é guardado. A memória é refeita sozinha quando passa de 7 dias, ou no botão "Atualizar memória agora", e o assistente passa a usá-la.

## Rodar local
```
cp .env.example .env.local   # preencha
npm install
npm run dev
```

## Cuidados
- Confirme com a política da empresa antes de usar com dados reais de trabalho.
- O assistente só sugere e redige; nada é enviado a ninguém.
