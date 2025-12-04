# Projeto Ouvidoria DCE - Todo List

## Funcionalidades Principais

### Autenticacao e Seguranca
- [x] Sistema de Login com RA (Registro Academico) e Senha (Manus OAuth)
- [x] Protecao contra uso malicioso de RA de terceiros (autenticacao via Manus OAuth)
- [x] Sistema de autenticacao seguro com JWT/Session
- [x] Logout funcional

### Modulo Estudante (Publico)
- [x] Pagina Inicial (Home) com informacoes sobre a ouvidoria
- [x] Formulario de Registro de Manifestacao com opcoes: Sobre eventos, Informacoes, Sobre consultoria juridica, Reclamacoes, Sugestoes, Trabalhe conosco
- [x] Campo de Titulo (obrigatorio)
- [x] Campo de Descricao (obrigatorio)
- [x] Funcionalidade de Anexar Documentos (titulo opcional)
- [x] Geracao de Numero de Protocolo unico apos envio
- [x] Pagina de Acompanhamento de Protocolo (consultar status da manifestacao)
- [x] Pagina de Perguntas Frequentes (FAQ) com perguntas relacionadas as opcoes de manifestacao

### Modulo DCE (Administrativo)
- [x] Painel Admin com listagem de manifestacoes
- [x] Listagem de todas as manifestacoes recebidas
- [x] Funcionalidade para visualizar detalhes de cada manifestacao
- [x] Funcionalidade para alterar status da manifestacao (Recebida, Em Analise, Encaminhada, Concluida)
- [x] Funcionalidade para adicionar comentarios internos (visiveis apenas para DCE)
- [x] Funcionalidade para adicionar resposta publica (visivel no acompanhamento de protocolo)

### Design e Interface
- [x] Design moderno estilo Canvas/Notion com sidebar navigation
- [x] Cor verde (#4CAF50) como cor primaria
- [x] Responsividade Mobile First
- [x] Barra lateral com navegacao (Inicio, Registrar Manifestacao, Acompanhar Processo, Painel Admin, Perguntas Frequentes)
- [x] Componentes UI consistentes com shadcn/ui

### Banco de Dados
- [x] Tabela de Usuarios (RA, Senha, E-mail, Role)
- [x] Tabela de Manifestacoes (Protocolo, Tipo, Titulo, Descricao, Status, Data de Criacao)
- [x] Tabela de Anexos (Referencia a Manifestacao, URL do arquivo)
- [x] Tabela de Respostas (Comentarios internos e publicos)

### Deploy e Documentacao
- [ ] Configurar GitHub Actions para CI/CD
- [ ] Preparar instrucoes de deploy
- [x] Criar README.md com instrucoes de uso
- [ ] Testar deploy em ambiente de producao


## Bugs Reportados e Correcoes
- [ ] Remover texto de icones nas abas (home, doc, list, help, settings)
- [ ] Usar apenas icones visuais compactos
- [ ] Corrigir problema de clique nas abas de navegacao
- [ ] Corrigir problema de scroll da pagina (volta para o topo)
- [ ] Melhorar responsividade da navegacao
