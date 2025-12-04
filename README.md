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



## Como Usar

### Para Estudantes


1. **Registrar Manifestação:**
   - Navegue até "Registrar Manifestação"
   - Selecione o tipo de manifestação
   - Preencha o título e descrição
   - Opcionalmente, anexe documentos
   - Clique em "Registrar Manifestação"
   - Você receberá um número de protocolo

2. **Acompanhar Processo:**
   - Vá para "Acompanhar Processo"
   - Digite o número do protocolo
   - Visualize o status e atualizações

### Para Administradores

3. **Acessar Painel Admin:**
   - Apenas usuários com role "admin" têm acesso
   - Clique em "Painel Admin" na navegação lateral

4. **Gerenciar Manifestações:**
   - Selecione uma manifestação da lista
   - Visualize os detalhes completos
   - Atualize o status conforme necessário
   - Adicione respostas (internas ou públicas)

## Segurança

- **Autenticação:** Utiliza Manus OAuth para autenticação segura
- **Autorização:** Apenas administradores podem acessar o painel admin
- **Dados Sensíveis:** Suporta registro anônimo de manifestações
- **Proteção CSRF:** Implementada via tRPC


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


dce-ouvidoria/
├── client/                                       # Frontend React
│   ├── src/
│   │   ├── pages/                                # Páginas da aplicação
│   │   ├── components/                           # Componentes reutilizáveis
│   │   ├── App.tsx                               # Roteamento principal
│   │   └── index.css                             # Estilos globais
│   └── public/                                   # Arquivos estáticos
├── server/                                       # Backend Node.js
│   ├── routers.ts                                # Procedimentos tRPC
│   ├── db.ts                                     # Queries do banco de dados
│   └── _core/                                    # Configuração interna
├── drizzle/                                      # Schema do banco de dados
└── package.json                                  # Dependências do projeto


## Instalação e Configuração

### Pré-requisitos
- Node.js 22+
- pnpm (gerenciador de pacotes)
- Banco de dados MySQL/TiDB



## Licença

Este projeto é fornecido como-é para fins educacionais.

## Autores

Caio Barbosa         Mateus onival
alberto              lucas Almeida
Davi vaz             Arthur



---

**Versão:** 1.0.0  
**Última atualização:** Novembro de 2025
