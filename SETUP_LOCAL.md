# Ouvidoria DCE - Setup Local, ngrok e GitHub Deployment

## 📋 Pré-requisitos

- Node.js 18+ e pnpm
- MySQL 8.0+ (ou MariaDB)
- Git
- ngrok (para testes com URL pública)

## 🚀 Setup Local

### 1. Clonar o Repositório

```bash
git clone https://github.com/seu-usuario/dce-ouvidoria.git
cd dce-ouvidoria
```

### 2. Instalar Dependências

```bash
pnpm install
```

### 3. Configurar Banco de Dados

#### Opção A: MySQL Local

```bash
# Criar banco de dados
mysql -u root -p -e "CREATE DATABASE dce_ouvidoria CHARACTER SET utf8mb4 COLLATE utf8mb4_unicode_ci;"

# Criar usuário (opcional)
mysql -u root -p -e "CREATE USER 'dce_user'@'localhost' IDENTIFIED BY 'sua_senha_segura';"
mysql -u root -p -e "GRANT ALL PRIVILEGES ON dce_ouvidoria.* TO 'dce_user'@'localhost';"
```

#### Opção B: Docker (Recomendado)

```bash
docker run --name dce-mysql \
  -e MYSQL_ROOT_PASSWORD=root \
  -e MYSQL_DATABASE=dce_ouvidoria \
  -p 3306:3306 \
  -d mysql:8.0
```

### 4. Configurar Variáveis de Ambiente

Criar arquivo `.env.local` na raiz do projeto:

```env
# Database
DATABASE_URL="mysql://dce_user:sua_senha_segura@localhost:3306/dce_ouvidoria"

# Email (Gmail SMTP)
EMAIL_SERVICE=gmail
EMAIL_USER=seu-email@gmail.com
EMAIL_PASSWORD=sua-senha-de-app
EMAIL_FROM=noreply@ouvidoria-dce.com

# Frontend
FRONTEND_URL=http://localhost:3000

# JWT Secret (gere uma string aleatória segura)
JWT_SECRET=sua_chave_secreta_super_segura_aqui_123456

# Node Environment
NODE_ENV=development
```

**Nota sobre Gmail:**
1. Ativar 2FA na conta Google
2. Gerar "Senha de App" em: https://myaccount.google.com/apppasswords
3. Usar a senha de app no `.env.local`

### 5. Executar Migrações do Banco de Dados

```bash
pnpm db:push
```

### 6. Iniciar o Servidor de Desenvolvimento

```bash
pnpm dev
```

O site estará disponível em: **http://localhost:3000**

## 🌐 Usando ngrok para URL Pública

### 1. Instalar ngrok

```bash
# macOS
brew install ngrok

# Linux
wget https://bin.equinox.io/c/bNyj1mQVY4c/ngrok-v3-stable-linux-amd64.zip
unzip ngrok-v3-stable-linux-amd64.zip
sudo mv ngrok /usr/local/bin/
```

### 2. Autenticar ngrok

```bash
ngrok config add-authtoken seu_token_aqui
```

(Obter token em: https://dashboard.ngrok.com/auth/your-authtoken)

### 3. Expor a Porta 3000

```bash
ngrok http 3000
```

Você receberá uma URL pública como: `https://abc123.ngrok.io`

### 4. Atualizar Variáveis de Ambiente

Editar `.env.local`:

```env
FRONTEND_URL=https://abc123.ngrok.io
```

### 5. Testar Login

1. Abrir: `https://abc123.ngrok.io/login`
2. Usar email: `teste@sempreceub.com`
3. RA: `12345678`
4. Você receberá um código no console (em desenvolvimento)

## 📦 Deploy no GitHub

### 1. Criar Repositório no GitHub

```bash
# Inicializar git (se não estiver)
git init

# Adicionar remote
git remote add origin https://github.com/seu-usuario/dce-ouvidoria.git

# Criar branch main
git branch -M main
```

### 2. Configurar .gitignore

Certifique-se de que `.gitignore` contém:

```
node_modules/
.env
.env.local
.env.*.local
dist/
build/
.DS_Store
*.log
```

### 3. Fazer Commit e Push

```bash
git add .
git commit -m "Initial commit: Ouvidoria DCE com autenticação segura"
git push -u origin main
```

### 4. Configurar GitHub Pages (Opcional)

Se quiser hospedar o frontend em GitHub Pages:

```bash
# Instalar gh-pages
pnpm add -D gh-pages

# Adicionar script ao package.json
"deploy": "pnpm build && gh-pages -d dist"

# Deploy
pnpm deploy
```

## 🔒 Sistema de Segurança de Login

### Fluxo de Autenticação

1. **Email + RA**
   - Validação de email institucional (@sempreceub.com)
   - Validação de RA (7-10 dígitos)

2. **Código de Verificação**
   - Código de 6 dígitos enviado por email
   - Válido por 15 minutos
   - **Previne uso malicioso de RA de terceiros**

3. **Criação de Senha** (novos usuários)
   - Mínimo 8 caracteres
   - Maiúscula + minúscula + número + caractere especial
   - Hashing com bcrypt (10 rounds de salt)

### Proteções Implementadas

- ✅ Senhas nunca em texto plano
- ✅ Bcrypt com 10 rounds de salt
- ✅ Validação de email institucional
- ✅ Código de verificação por email
- ✅ Rate limiting para força bruta
- ✅ Mensagens de erro genéricas

## 📝 Estrutura do Projeto

```
dce-ouvidoria/
├── client/                 # Frontend React
│   ├── src/
│   │   ├── pages/         # Páginas (Login, Home, Manifestacao, etc)
│   │   ├── components/    # Componentes reutilizáveis
│   │   └── lib/           # Utilitários
│   └── index.html
├── server/                 # Backend Node.js/Express
│   ├── routers/           # Procedimentos tRPC
│   ├── db.ts              # Funções de banco de dados
│   ├── security.ts        # Validações de segurança
│   ├── email.ts           # Serviço de email
│   └── _core/             # Configuração interna
├── drizzle/               # Schema e migrações do BD
├── .env.local             # Variáveis de ambiente (não commitar)
└── package.json
```

## 🧪 Testando Localmente

### Teste de Login

1. Abrir: http://localhost:3000/login
2. Email: `teste@sempreceub.com`
3. RA: `12345678`
4. Código: Verificar no console do servidor (em desenvolvimento)
5. Senha: `Senha123!@#`

### Teste de Manifestação

1. Fazer login
2. Clicar em "Registrar Manifestação"
3. Preencher formulário
4. Submeter
5. Copiar protocolo
6. Usar em "Acompanhar Processo"

## 🐛 Troubleshooting

### Erro: "Cannot find package 'bcrypt'"

```bash
pnpm install bcrypt @types/bcrypt
```

### Erro: "Database connection failed"

- Verificar se MySQL está rodando
- Verificar `DATABASE_URL` no `.env.local`
- Executar: `pnpm db:push`

### Emails não chegam

- Verificar credenciais Gmail
- Habilitar "Menos seguro" ou usar "Senha de App"
- Verificar spam

### ngrok não conecta

- Verificar token de autenticação
- Verificar se porta 3000 está rodando
- Tentar: `ngrok http 3000 --log=stdout`

## 📚 Referências

- [Bcrypt Security Best Practices](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html)
- [OWASP Authentication Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Authentication_Cheat_Sheet.html)
- [ngrok Documentation](https://ngrok.com/docs)
- [GitHub Deployment](https://docs.github.com/en/pages)

## 📞 Suporte

Para dúvidas ou problemas, abrir uma issue no GitHub ou contactar o DCE.

---

**Desenvolvido para a disciplina de Programação Web**
Ouvidoria DCE - Voz Estudantil
