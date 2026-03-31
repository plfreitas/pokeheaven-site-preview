# 🌟 PokeHeaven - Website & Portal Oficial

<img width="2752" height="1536" alt="lugia" src="https://github.com/user-attachments/assets/41ddbf71-0578-49a6-b25b-f2e8cd0a4d8c" />

> **PokeHeaven** é o portal oficial, painel de controle e ranking do servidor de Pokémon alternativo. Um sistema moderno de alta performance separado em arquitetura Cliente-Servidor.

## 🏛️ Arquitetura do Projeto

O sistema foi recentemente re-estruturado (Saindo do Vercel Serverless) para permitir a hospedagem nativa e focada em performance numa **VPS Privada**, gerando escalabilidade e independência. 

O projeto é dividido em duas camadas restritas:

### 1️⃣ Frontend (Interface UI)
A interface de usuário foi construída utilizando o stack moderno e hiper-rápido:
- **React + Vite:** Para processamento instantâneo do lado do cliente (HMR) e navegação SPA fluída.
- **Tailwind CSS:** Para estilização altamente responsiva, baseada em Glassmorphism, sombreamentos gradientes e cores dinâmicas (Cyan, White & Black).
- **TypeScript (Parcial/Ativo):** Para forte tipagem na construção dos objetos e dados providos pela API.

### 2️⃣ Backend (API & Database)
Motor principal para tratar requisições de Banco de Dados, Autenticação de Usuários e Ranking do Jogo:
- **Node.js + Express:** Servidor HTTP persistente altamente escalável escutando requisições na porta `3001`.
- **MySQL2:** Conector oficial para transações com a nuvem (Aiven) garantindo segurança (SSL habilitado) para lidar com a base de dados dos players.
- **Segurança (CORS / Dotenv):** Gerenciador de portas liberadas e variáveis de estado (senhas) ocultas.

---

## 🛠️ Como Iniciar o Projeto Localmente

Para rodar o projeto na sua máquina de desenvolvimento, você precisará acender os dois motores de forma independente.

### Backend (Servidor Node)
```bash
# 1. Acesse a pasta do backend
cd backend

# 2. Instale as dependências
npm install

# 3. Configure as Variáveis
# Certifique-se de que o arquivo .env exite com as chaves: 
# DB_HOST, DB_USER, DB_PASS, DB_NAME, DB_PORT

# 4. Inicie o servidor em modo de observação (Porta 3001 livre)
npm run dev
```

### Frontend (Servidor Vite)
```bash
# 1. Em um novo terminal, acesse o frontend
cd frontend

# 2. Instale as dependências da Interface
npm install

# 3. Inicie o servidor web (Acessível via localhost:5173)
npm run dev
```

> **Aviso:** O Proxy Vite (`vite.config.ts`) está configurado para traduzir requisições da rota `/api` do Front automaticamente para o `http://localhost:3001` no local host. Mantenha os dois ligados simultaneamente.

---

## 🚀 Como fazer o Deploy na VPS (Produção)

1. **Suba ou clone** (via GitHub Pull) esta versão para sua Máquina Virtual (Ubuntu/CentOS).
2. **Backend:** Entre na pasta `backend`, instale os pacotes (`npm install`) e instale localmente o gerenciador **PM2** (`npm install -g pm2`). Em seguida, inicie o core: `pm2 start server.js --name "pokeheaven-api"`.
3. **Frontend:** Entre na pasta `frontend`, rode `npm run build` para construir a sua versão estática do site otimizada. A pasta `dist/` resultante será gerada.
4. **Nginx:** Configure o NGINX da sua VPS para ler a pasta genérica `dist/` para a porta 80/443 do seu domínio público (`pokeheaven.com.br`) e crie uma regra de **Reverse Proxy** enviando as chamadas originadas em `/api/*` diretamente para o `localhost:3001`.

---
*Desenvolvido pela Equipe PokeHeaven em conjunto com Orion (AIOX Master).*
