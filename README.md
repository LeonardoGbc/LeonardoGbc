# Perfil Interativo (Frontend-first) — React + Vite (frontend) + Express (backend)

Este projeto é uma base para um perfil interativo focado em front-end, com um backend leve para:
- buscar repos públicos do GitHub (proxy -> permite usar token e evitar CORS);
- buscar uma "quote of the day";
- receber um formulário de contato (opcional: enviar por e-mail via SMTP).

Estrutura:
- frontend/ — app React + Vite (UI principal, widgets, formulários)
- backend/ — API Express (endpoints: /api/repos, /api/quote, /api/contact)

Rápido para rodar (local):
1) Backend
   - cd backend
   - copie .env.example -> .env e preencha (opcional: GITHUB_TOKEN, SMTP_*)
   - npm install
   - npm start
   - API estará em http://localhost:4000 por padrão

2) Frontend
   - cd frontend
   - npm install
   - npm run dev
   - Frontend em http://localhost:5173 (ou porta do Vite)

Endpoints úteis:
- GET /api/repos?user=<github-username>  -> lista de repositórios (top 5 por estrelas)
- GET /api/quote                         -> quote aleatória
- POST /api/contact                      -> body JSON { name, email, message }

Deploy:
- Frontend pode ir para GitHub Pages, Vercel ou Netlify.
- Backend pode ir para Render, Fly, Heroku, Railway, Vercel Serverless, etc.
- Para produção, defina GITHUB_TOKEN para aumentar limites da API do GitHub e configure SMTP se quiser receber emails.

Personalizações que posso fazer:
- transformar em TypeScript;
- usar Tailwind CSS ou component library (Chakra/Material);
- adicionar widget “Now Playing” (Spotify), WakaTime, últimas postagens do blog;
- criar workflow GitHub Actions para atualizar seções do README automaticamente.

Quer que eu:
1) Crie um repositório e abra PR com esses arquivos no seu GitHub (preciso do owner/repo)?  
2) Só entregue os arquivos (vou enviar aqui) pra você subir?  
3) Configure deploy (preciso de acesso ou instruções de deploy)?

Me diga qual opção prefere e eu prossigo.
