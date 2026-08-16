# Atividade Teórica: Usuários Especialistas, IA e Distribuição Segura de Dados

**Aluno(s):** Henrick Uchoa, Allan Paiva, Juan Moreira, Guilherme Ketes
**Turma:** Banco de Dados 2026 (Turma : G2)
**Data:** 16/08/2026
**Repositório Git:** https://github.com/Juan-hub134/ATIVIDADE-teorica-ia-dba-Uchoa-Paiva-Kail-Moreira-Ketes.git

## Resumo Executivo

Breve descrição do tema e da posição adotada pelo grupo.

## 1. Desenvolvimento Teórico

### 1.1 O que é o DBA e quais suas funções?
Definição de DBA e suas funções: definição do esquema, estrutura de dados e
acesso, autorização de acesso, regras de integridade.

### 1.2 Perfis de usuários de banco de dados
Programadores de aplicações, usuários sofisticados, usuários especialistas,
usuários navegantes — vantagens e limitações de cada perfil.

### 1.3 Riscos do uso de IA por usuários especialistas
Consulta incorreta, exposição de dados sensíveis, degradação de performance,
vazamento por prompts — impactos na segurança e na integridade.

### 1.4 Distribuição segura de dados
Menor privilégio, views, roles customizadas, controle de execução, auditoria,
conformidade (LGPD).
 -Resposta:
   Menor privilégio: Cada usuário deve possuir somente as permissões necessárias para sua função. Por exemplo, um analista pode consultar vendas, mas não deve poder excluir dados ou acessar informações pessoais desnecessárias.
   Roles: São conjuntos de permissões atribuídos aos usuários de acordo com sua função. Por exemplo, pode existir uma role analista, com permissão apenas para consultar determinados dados.
   Views: Permitem disponibilizar apenas uma parte dos dados. Por exemplo, uma view de vendas pode mostrar valores e produtos, mas ocultar  CPF e endereço dos clientes.
   Controle de execução: As permissões devem ser verificadas pelo banco para impedir que uma consulta gerada pela IA execute operações não autorizadas. Isso reduz o risco de uma IA gerar uma consulta que altere ou exponha dados indevidamente.
   Auditoria: Deve registrar ações importantes, como quem acessou ou alterou os dados e quando, permitindo identificar problemas e acessos indevidos.
   LGPD: Dados pessoais devem ter acesso restrito e não devem ser enviados desnecessariamente para ferramentas de IA externas, reduzindo o risco de vazamento.

### 1.5 Atuação do DBA no cenário de IA
Monitoramento, políticas de acesso, auditoria, orientação aos usuários,
performance e backups.

### 1.6 Análise crítica: qual a melhor abordagem?
Posição fundamentada do grupo sobre como distribuir dados com segurança
no contexto do uso de IA.

## 2. Exemplos e Casos

Exemplo de view `clientes_visiveis` no PostgreSQL e exemplo de role/permissão.
Um caso real: sistema de vendas, clínica ou biblioteca.

## 3. Referências

Fontes consultadas (livros, artigos, documentação oficial do PostgreSQL,
materiais do curso).

## 4. Conclusões

Aprendizados, reflexões e principais pontos observados pelo grupo.

## Link do Repositório Git