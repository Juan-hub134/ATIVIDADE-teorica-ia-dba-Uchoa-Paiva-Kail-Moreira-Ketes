# Atividade Teórica: Usuários Especialistas, IA e Distribuição Segura de Dados

**Aluno(s):** Allan Paiva, Guilherme Ketes, Henrick Uchoa e Juan Moreira.
**Turma:** Banco de Dados 2026 (Turma : G2)
**Data:** 16/08/2026
**Repositório Git:** https://github.com/Juan-hub134/ATIVIDADE-teorica-ia-dba-Uchoa-Paiva-Kail-Moreira-Ketes.git

## Resumo Executivo

Breve descrição do tema e da posição adotada pelo grupo.

## 1. Desenvolvimento Teórico

### 1.1 O que é o DBA e quais suas funções?
Definição de DBA e suas funções: definição do esquema, estrutura de dados e
acesso, autorização de acesso, regras de integridade.	

-Resposta: 
## Database Administrator (DBA)

O Database Administrator (DBA) é a pessoa que possui um controle central do Database Management System (DBMS) para gerenciar os dados e as informações, e as principais funções do administrador do banco de dados seriam a definição original do esquema do banco de dados, pela execução de um conjunto de instruções definidos pela DDL do DBMS.

## Definição do esquema, estrutura de armazenamento e acesso

A estrutura do armazenamento e o método de acesso também são definidos pelo DBA, podendo especificar alguns parâmetros pertencentes à organização física dos dados.

O design lógico é definido por decisões de quais atributos deveriam existir e como eles deveriam ser organizados para formar várias tabelas de acordo com as regras de negócio. A parte de como isso é feito é um problema da área de ciência da computação que pode ser abordado de duas formas complementares:

* A primeira forma seria um modelo de Entity-Relationship, que funciona utilizando a especificidade de um esquema de uma empresa que representa a estrutura lógica da database;
* A outra forma seria utilizar técnicas conhecidas como normalização, que analisam os atributos e suas dependências para auxiliar na organização das tabelas e evitar problemas como redundâncias e inconsistências.

A definição dos índices a serem criados está relacionada aos métodos de acesso e ao projeto físico do banco de dados, e não ao processo de normalização.

O DBA recebe as mudanças e as adiciona no esquema e organiza a estrutura do armazenamento de dados para refletir as mudanças necessárias das regras de negócio do projeto ou para melhorar a performance geral do banco de dados.

## Autorização de acesso

Para garantir o acesso aos dados conforme o nível do usuário, o DBA pode controlar qual parte da database cada usuário pode acessar, e as informações das autorizações de acesso são mantidas pelo DBMS e consultadas pelo sistema quando um usuário tenta realizar uma operação sobre os dados.

## Regras de integridade

Além disso, existem as regras de integridade, que servem para garantir que as mudanças feitas no database por usuários autorizados não resultem em perda da consistência dos dados. Alguns exemplos de regras podem ser:

* O nome de um instrutor não pode ser nulo;
* Dois instrutores não podem ter a mesma ID;
* O orçamento de um departamento tem que ser maior do que zero reais.

## Rotina de manutenção

Por fim, existe a rotina de manutenção, que inclui fazer backups periodicamente para prevenir perda de dados em casos de desastres como o *flooding*, ter certeza de que existe espaço sobrando em disco para operações normais e aumentar a quantidade de armazenamento conforme o necessário, além do monitoramento do funcionamento e do desempenho do banco de dados para garantir que sua performance não se deteriore com as tarefas executadas pelos usuários.

### 1.2 Perfis de usuários de banco de dados
Programadores de aplicações, usuários sofisticados, usuários especialistas,
usuários navegantes — vantagens e limitações de cada perfil.

### 1.3 Riscos do uso de IA por usuários especialistas
Consulta incorreta, exposição de dados sensíveis, degradação de performance,
vazamento por prompts — impactos na segurança e na integridade.

### 1.4 Distribuição segura de dados
Menor privilégio, views, roles customizadas, controle de execução, auditoria,
conformidade (LGPD).

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

SILBERSCHATZ, Abraham; KORTH, Henry F.; SUDARSHAN, S. *Database System Concepts*. 7. ed. McGraw-Hill.


## 4. Conclusões

Aprendizados, reflexões e principais pontos observados pelo grupo.

## Link do Repositório Git