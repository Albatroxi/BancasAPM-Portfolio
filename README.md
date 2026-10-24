# BancasAPM-Portfolio
Sistema web para gerenciamento de bancas de avaliação, avaliadores e alocações, desenvolvido com Next.js, React, TypeScript e MySQL. Projeto de portfólio com apresentação da arquitetura e funcionalidades .


# BancasAPM — Sistema de Gestão de Bancas Avaliadoras

Aplicação web para apoiar a gestão de bancas avaliadoras, alocações, avaliadores, inscrições externas, certificados, notificações e relatórios no contexto da Academia de Polícia Militar da Bahia.

> **Nota:** revise este README e confirme os fluxos com a equipe responsável antes de publicar o repositório publicamente. Não inclua credenciais, dados pessoais, backups ou arquivos de ambiente.

## Tecnologias identificadas

- Next.js 16.2.0, React 19 e TypeScript
- MySQL (`mysql2`)
- Tailwind CSS 4 e componentes Radix UI
- JWT e bcryptjs como dependências relacionadas à autenticação
- Bibliotecas de PDF e planilhas: `jspdf`, `jspdf-autotable`, `pdf-lib` e `xlsx`

## Requisitos

- Node.js compatível com a versão do Next.js definida em `package.json`
- npm
- MySQL 8+ (conforme comentário do script SQL)
- Variáveis de ambiente necessárias ao banco e às integrações usadas no ambiente

## Instalação local

1. Clone o repositório.
2. Instale dependências:

   ```bash
   npm ci
   ```

3. Crie `.env.local` localmente, a partir de `.env.example`, e preencha os valores fornecidos pelo administrador do ambiente.
4. Configure o MySQL. O script `scripts/database_mysql.sql` cria o banco `apm_pmba`.

   **Atenção:** o script inicial contém comandos `DROP TABLE IF EXISTS`. Não o execute em um banco com dados que devam ser preservados. Use-o somente em ambiente descartável ou prepare uma migração não destrutiva.

5. Inicie o servidor:

   ```bash
   npm run dev
   ```

   O script atual usa a porta `3004`; abra `http://localhost:3004`.

## Scripts disponíveis

| Comando | Finalidade |
|---|---|
| `npm run dev` | Servidor de desenvolvimento na porta 3004 |
| `npm run build` | Build de produção |
| `npm run start` | Servidor de produção na porta 3004 |
| `npm run test-db` | Script auxiliar de teste de conexão com banco |
| `npm run test-integration` | Script auxiliar de teste de integração |
| `npm run lint` | Comando de lint definido no `package.json`; validar compatibilidade com a versão instalada |

## Áreas funcionais identificadas

- Autenticação, perfil, alteração de senha e histórico de login
- Gestão de bancas avaliadoras e alocações
- Cadastro de avaliadores, orientadores e coorientadores
- Inscrições externas e envio/geração de documentos PDF
- Solicitação e gestão de certificados
- Notificações, incluindo rotas relacionadas a WhatsApp
- Dashboard e relatórios

Consulte `docs/BancasAPM_Documentacao_Tecnica.pdf` para arquitetura, inventário de endpoints, modelo conceitual de dados, diagramas, instalação e recomendações de segurança.

## Configuração de ambiente

O SQL menciona `MYSQL_HOST`, `MYSQL_PORT`, `MYSQL_USER`, `MYSQL_PASSWORD`, `MYSQL_DATABASE` ou, alternativamente, `DATABASE_URL`. Confirme no código quais variáveis são efetivamente consumidas.

Nunca faça commit de `.env.local`, credenciais JSON, tokens, chaves ou dados reais.

## Segurança e dados

- Revise autorização no servidor para cada rota administrativa.
- Use consultas parametrizadas e validação de entrada.
- Não publique dumps/backups nem credenciais.
- Faça backup e teste restauração antes de qualquer atualização de banco.
- Proteja dados pessoais e histórico de acesso.
- Confirme licença e autorização institucional antes de tornar o código público.

## Estrutura de diretórios

- `app/`: páginas e endpoints da API
- `components/`: componentes de interface reutilizáveis
- `lib/`, `data/`, `contexts/`, `hooks/`: módulos auxiliares, serviços e estado compartilhado
- `public/`: arquivos estáticos
- `styles/`: estilos
- `scripts/`: scripts auxiliares e SQL

## Testes e validação

Antes de publicar, execute em ambiente limpo:

```bash
npm ci
npm run test-db
npm run test-integration
npm run build
```

Os testes de banco e integração dependem da configuração local. Não execute contra produção sem autorização e backup.

## Documentação

- `docs/BancasAPM_Documentacao_Tecnica.pdf` — documentação técnica e diagramas.
- `CONTRIBUTING.md` — orientações de contribuição.
- `CHANGELOG.md` — histórico de alterações.

## Licença

A licença deve ser confirmada pelo titular do projeto. O arquivo `LICENSE` existente deve ser revisado antes de publicação pública; não altere ou substitua a licença sem autorização.
