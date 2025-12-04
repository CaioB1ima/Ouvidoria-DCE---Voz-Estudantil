# Ouvidoria DCE - Voz Estudantil

Sistema de ouvidoria para o Diretório Central dos Estudantes (DCE), desenvolvido como projeto final da disciplina de Programação Web.

## Visão Geral

A **Ouvidoria DCE** é uma plataforma digital que permite aos estudantes registrar manifestações, sugestões, reclamações e elogios de forma segura e transparente. O sistema oferece um canal direto de comunicação entre os estudantes e a administração do DCE, garantindo que todas as vozes sejam ouvidas.

## Funcionalidades Principais

### Para Estudantes
- **Registrar Manifestação:** Envie suas manifestações, sugestões, reclamações ou denúncias em categorias específicas
- **Acompanhar Processo:** Consulte o status de suas manifestações usando o número de protocolo
- **Perguntas Frequentes:** Acesse respostas para dúvidas comuns sobre a ouvidoria
- **Registro Anônimo:** Opção de registrar manifestações de forma anônima

### Para Administradores (DCE)
- **Painel Administrativo:** Visualize todas as manifestações recebidas
- **Gerenciar Status:** Atualize o status das manifestações (Recebida, Em Análise, Encaminhada, Concluída)
- **Responder Manifestações:** Adicione comentários internos ou respostas públicas
- **Acompanhamento:** Monitore o progresso de cada manifestação

## Tipos de Manifestação

1. **Sobre eventos:** Feedback e sugestões sobre eventos do DCE
2. **Informações:** Dúvidas e pedidos de informações
3. **Consultoria jurídica:** Questões legais e direitos estudantis
4. **Reclamações:** Problemas e insatisfações
5. **Sugestões:** Ideias para melhorias
6. **Trabalhe conosco:** Interesse em participar do DCE

## Tecnologias Utilizadas

### Frontend
- React 19
- TypeScript
- Tailwind CSS 4
- Wouter (roteamento)
- shadcn/ui (componentes)
- Lucide React (ícones)

### Backend
- Node.js com Express
- tRPC (RPC type-safe)
- Drizzle ORM (banco de dados)
- MySQL/TiDB (banco de dados)

### Autenticação
- Manus OAuth (autenticação segura)
- JWT (sessões)

## Estrutura do Projeto

```
dce-ouvidoria/
├── client/                 # Frontend React
│   ├── src/
│   │   ├── pages/         # Páginas da aplicação
│   │   ├── components/    # Componentes reutilizáveis
│   │   ├── App.tsx        # Roteamento principal
│   │   └── index.css      # Estilos globais
│   └── public/            # Arquivos estáticos
├── server/                # Backend Node.js
│   ├── routers.ts         # Procedimentos tRPC
│   ├── db.ts              # Queries do banco de dados
│   └── _core/             # Configuração interna
├── drizzle/               # Schema do banco de dados
└── package.json           # Dependências do projeto
```

## Instalação e Configuração

### Pré-requisitos
- Node.js 22+
- pnpm (gerenciador de pacotes)
- Banco de dados MySQL/TiDB

### Passos de Instalação

1. **Clone o repositório:**
```bash
git clone https://github.com/seu-usuario/dce-ouvidoria.git
cd dce-ouvidoria
```

2. **Instale as dependências:**
```bash
pnpm install
```

3. **Configure as variáveis de ambiente:**
Crie um arquivo `.env` na raiz do projeto com as seguintes variáveis:
```
DATABASE_URL=mysql://usuario:senha@localhost:3306/dce_ouvidoria
JWT_SECRET=sua_chave_secreta_aqui
VITE_APP_ID=seu_app_id
OAUTH_SERVER_URL=https://api.manus.im
```

4. **Execute as migrações do banco de dados:**
```bash
pnpm db:push
```

5. **Inicie o servidor de desenvolvimento:**
```bash
pnpm dev
```

O aplicativo estará disponível em `http://localhost:3000`.

## Como Usar

### Para Estudantes

1. **Fazer Login:**
   - Clique em "Login" na página inicial
   - Autentique-se com suas credenciais Manus

2. **Registrar Manifestação:**
   - Navegue até "Registrar Manifestação"
   - Selecione o tipo de manifestação
   - Preencha o título e descrição
   - Opcionalmente, anexe documentos
   - Clique em "Registrar Manifestação"
   - Você receberá um número de protocolo

3. **Acompanhar Processo:**
   - Vá para "Acompanhar Processo"
   - Digite o número do protocolo
   - Visualize o status e atualizações

### Para Administradores

1. **Acessar Painel Admin:**
   - Apenas usuários com role "admin" têm acesso
   - Clique em "Painel Admin" na navegação lateral

2. **Gerenciar Manifestações:**
   - Selecione uma manifestação da lista
   - Visualize os detalhes completos
   - Atualize o status conforme necessário
   - Adicione respostas (internas ou públicas)

## Segurança

- **Autenticação:** Utiliza Manus OAuth para autenticação segura
- **Autorização:** Apenas administradores podem acessar o painel admin
- **Dados Sensíveis:** Suporta registro anônimo de manifestações
- **Proteção CSRF:** Implementada via tRPC

## Deploy

### Deploy no GitHub Pages (Frontend)

1. Configure o repositório GitHub
2. Ative GitHub Pages nas configurações do repositório
3. Execute: `pnpm build`
4. Faça push dos arquivos para a branch `gh-pages`

### Deploy em Produção

Para deploy em produção, recomenda-se:
- Usar um serviço como Vercel, Netlify ou Railway
- Configurar variáveis de ambiente seguras
- Usar um banco de dados gerenciado
- Implementar CI/CD com GitHub Actions

## Contribuindo

Este é um projeto acadêmico. Para contribuições:

1. Faça um fork do repositório
2. Crie uma branch para sua feature (`git checkout -b feature/AmazingFeature`)
3. Commit suas mudanças (`git commit -m 'Add some AmazingFeature'`)
4. Push para a branch (`git push origin feature/AmazingFeature`)
5. Abra um Pull Request

## Licença

Este projeto é fornecido como-é para fins educacionais.

## Autores

Desenvolvido como projeto final da disciplina de Programação Web.

## Suporte

Para dúvidas ou problemas, abra uma issue no repositório GitHub.

---

**Versão:** 1.0.0  
**Última atualização:** Novembro de 2025
