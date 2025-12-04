# Ouvidoria DCE - Voz Estudantil

Sistema de ouvidoria para o Diretório Central dos Estudantes (DCE), desenvolvido como projeto final da disciplina de Programação Web.

# LOGIN              https://ouvidoriadce.manus.space/login
# MANIFESTAÇÕES DCE https://ouvidoriadce.manus.space/manifestacao

HOSPEDADO PELA MANUS

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

• **Sobre eventos:** Feedback e sugestões sobre eventos do DCE
• **Informações:** Dúvidas e pedidos de informações
• **Consultoria jurídica:** Questões legais e direitos estudantis
• **Reclamações:** Problemas e insatisfações
• **Sugestões:** Ideias para melhorias
• **Trabalhe conosco:** Interesse em participar do DCE



## Como Usar

### Para Estudantes


• **Registrar Manifestação:**
   - Navegue até "Registrar Manifestação"
   - Selecione o tipo de manifestação
   - Preencha o título e descrição
   - Opcionalmente, anexe documentos
   - Clique em "Registrar Manifestação"
   - Você receberá um número de protocolo

• **Acompanhar Processo:**
   - Vá para "Acompanhar Processo"
   - Digite o número do protocolo
   - Visualize o status e atualizações

### Para Administradores

• **Acessar Painel Admin:**
   - Apenas usuários com role "admin" têm acesso
   - Clique em "Painel Admin" na navegação lateral
• **Gerenciar Manifestações:**
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




## Licença

Este projeto é fornecido como-é para fins educacionais.

## Autores

Caio Barbosa, alberto, Mateus onival, alberto, lucas Almeida, Davi vaz e Arthur



---

**Versão:** 1.0.0  
**Última atualização:** Novembro de 2025
