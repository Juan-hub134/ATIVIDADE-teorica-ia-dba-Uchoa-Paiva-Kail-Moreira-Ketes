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

-Resposta:
Segundo Silberschatz, Korth e Sudarshan (Database System Concepts, 7ª ed., Cap. 1), nem todo mundo usa o banco de dados da mesma forma. Os autores dividem os usuários em quatro grupos principais, dependendo de como eles acessam o sistema e do quanto entendem do assunto:

* **Programadores de Aplicações:** São os desenvolvedores que escrevem o código (em Java, Python, C#) e embutem comandos de banco para fazer a ponte entre a aplicação e o **SGBD (Sistema de Gerenciamento de Banco de Dados — conjunto de softwares responsável por criar, gerenciar, armazenar e manipular os dados de forma segura)**, utilizando instruções de **DML (Linguagem de Manipulação de Dados — comandos como INSERT, UPDATE e DELETE usados para consultar e alterar os dados)** e **DDL (Linguagem de Definição de Dados — comandos como CREATE e ALTER usados para definir a estrutura das tabelas)**.
  * *Vantagem:* Facilitam a vida do usuário final, criando telas e rotinas prontas que escondem a complexidade do **SQL (Linguagem de Consulta Estruturada — a linguagem padrão usada para se comunicar com bancos de dados relacionais)**.
  * *Limitação:* Podem criar gargalos de desempenho ou brechas de segurança (como SQL Injection) se o código for mal escrito.

* **Usuários Sofisticados:** Analistas de dados, pessoal de **BI (Business Intelligence — Inteligência de Negócios, focada na análise de dados para tomada de decisões)** ou cientistas de dados que não usam sistemas prontos. Eles montam e rodam as consultas diretamente na linguagem SQL usando ferramentas como `psql` ou DBeaver.
  * *Vantagem:* Têm total liberdade para fazer análises rápidas e tirar respostas do banco sem precisar pedir para a TI criar uma tela nova.
  * *Limitação:* Se rodarem uma consulta pesada sem otimização, podem travar o banco e prejudicar todo o sistema.

* **Usuários Especialistas:** Pessoal técnico que constrói aplicações fora do padrão trivial de cadastro e consulta, como sistemas de inteligência artificial, processamento de dados geográficos em **GIS (Sistemas de Informação Geográfica — softwares para análise e visualização de dados espaciais e mapas)** ou simulações científicas.
  * *Vantagem:* Conseguem extrair o máximo do SGBD, usando recursos avançados e estruturas de dados complexas.
  * *Limitação:* Criam soluções difíceis de manter e com pouca portabilidade para outros bancos.

* **Usuários Navegantes (Naïve / Leigos):** O usuário comum do dia a dia (o caixa do mercado, o atendente, o cliente no aplicativo do banco). Ele só clica em botões e preenche formulários sem nem saber que existe um banco de dados rodando por trás.
  * *Vantagem:* Não precisam aprender nada de SQL e quase não oferecem risco direto à estrutura do banco.
  * *Limitação:* Não têm flexibilidade nenhuma; só fazem exatamente o que a tela permite.

---

### O papel do DBA e o controle de acesso no dia a dia

Para o banco não virar uma bagunça com tanta gente diferente acessando, entra o **DBA (Database Administrator ou Administrador de Banco de Dados — o profissional responsável por manter o banco seguro, disponível e com bom desempenho)**. A regra de ouro aqui é o **Princípio do Menor Privilégio**: ninguém ganha mais acesso do que o estritamente necessário para fazer o seu trabalho.

Para garantir isso, o DBA usa três ferramentas essenciais do SGBD:

1. **Roles e Permissões:** Em vez de dar permissão usuário por usuário (o que seria inviável), o DBA cria papéis (ex: `role_atendimento`, `role_analista`). Cada perfil recebe só os comandos necessários (`SELECT`, `INSERT`, etc.) e os usuários são colocados dentro dessas *roles*.
2. **Views (Visões):** Funcionam como espelhos ou filtros para o banco. Se um analista precisa ver a lista de clientes, mas não pode ver o saldo nem a senha deles, o DBA cria uma *view* mostrando só os campos liberados.
3. **Auditoria:** É o registro de logs do sistema (o famoso "quem fez o quê e quando"). Serve para rastrear acessos suspeitos, identificar quem rodou uma consulta que travou o servidor e manter a conformidade com regras de segurança e privacidade.

---
### Referências Bibliográficas

* SILBERSCHATZ, Abraham; KORTH, Henry F.; SUDARSHAN, S. **Database System Concepts**. 7th ed. New York: McGraw-Hill, 2020. Capítulos 1 e 16. 


### 1.3 Riscos do uso de IA por usuários especialistas
Consulta incorreta, exposição de dados sensíveis, degradação de performance,
vazamento por prompts — impactos na segurança e na integridade.

### 1.4 Distribuição segura de dados
Menor privilégio, views, roles customizadas, controle de execução, auditoria,
conformidade (LGPD).
#### -Resposta:
   * A distribuição segura de dados busca garantir que cada usuário tenha acesso apenas às informações necessárias para sua função. O DBA (Database Administrator, administrador do banco de dados) é responsável por administrar usuários, permissões e mecanismos de segurança, controlando o acesso aos dados.

   * Menor privilégio: O menor privilégio (princípio de conceder somente as permissões necessárias) consiste em dar ao usuário apenas os acessos necessários para realizar sua função. Por exemplo, um funcionário que apenas consulta dados recebe SELECT (permissão para consultar dados), sem permissão para alterar ou excluir informações.

   * Roles e Permissões: As roles (grupos de permissões associados a uma função) permitem organizar os acessos dos usuários. Por exemplo, pode-se criar uma role para analistas e conceder a ela apenas as permissões necessárias. O GRANT (comando utilizado para conceder permissões) permite liberar um acesso, enquanto o REVOKE (comando utilizado para retirar permissões) remove esse acesso.

   * Views: Permitem disponibilizar apenas uma parte dos dados. Por exemplo, uma view de vendas pode mostrar valores e produtos, mas ocultar  CPF e endereço dos clientes.

   * Controle de execução: O controle de execução (controle de quem pode executar determinadas funções ou procedimentos) impede que qualquer usuário execute operações que não deveria.O privilégio EXECUTE (permissão para executar uma função ou procedimento) pode ser concedido somente aos usuários autorizados.

   * Auditoria: A auditoria (registro das ações realizadas no banco de dados) permite identificar quem realizou uma ação e quando ela aconteceu. Isso ajuda a investigar acessos indevidos ou alterações incorretas.

   * LGPD: A LGPD (Lei Geral de Proteção de Dados) estabelece regras para a proteção de dados pessoais. Nesse contexto, mecanismos como menor privilégio, roles, views e auditoria ajudam a controlar o acesso e reduzir a exposição de informações pessoais.

### 1.5 Atuação do DBA no cenário de IA
Monitoramento, políticas de acesso, auditoria, orientação aos usuários,
performance e backups.
#### -Resposta:
   * Monitoramento:O DBA deve acompanhar continuamente o banco de dados para identificar problemas de desempenho e atividades suspeitas. No cenário de IA, isso é ainda mais importante porque os ataques podem ser automatizados e mudar de estratégia para escapar das defesas. Por isso, o uso de monitoramento de anomalias ajuda a identificar comportamentos fora do padrão.

   * Políticas de acesso: O DBA deve definir quem pode acessar os dados e quais ações cada usuário pode realizar, seguindo o princípio do menor privilégio. No PostgreSQL, por exemplo, uma ROLE pode receber apenas a permissão SELECT, permitindo consultar dados sem alterá-los. Também podem ser utilizadas VIEWs para mostrar somente as informações necessárias para cada usuário, reduzindo a exposição de dados sensíveis. O controle de acesso é uma das principais camadas de segurança dos bancos de dados.

   * Auditoria: A auditoria consiste em registrar as atividades realizadas no banco para permitir identificar quem realizou determinada ação e quando ela ocorreu. Ela se diferencia do monitoramento porque o monitoramento acompanha as atividades e busca identificar comportamentos anormais, enquanto a auditoria mantém registros que podem ser utilizados posteriormente para investigação.

   * Orientação aos usuários: O DBA deve orientar os usuários sobre o uso correto do banco, proteção de credenciais e cuidados com permissões. Essa orientação é importante porque ataques baseados em IA também podem utilizar phishing, engenharia social e deepfakes para enganar usuários e administradores. Dessa forma, a segurança depende não apenas da tecnologia, mas também do comportamento dos usuários.

   * Performance: O DBA deve garantir que o banco continue funcionando de maneira eficiente mesmo com a utilização de mecanismos de segurança. Algumas soluções de defesa baseadas em IA podem exigir mais recursos computacionais, tornando necessário equilibrar segurança e desempenho. O estudo considera fatores como custo computacional, eficiência e escalabilidade na avaliação das defesas.

   * Backups: O DBA deve manter backups para permitir a recuperação dos dados após falhas ou ataques. No cenário de IA, backups e recuperação rápida são importantes para reduzir os impactos de ataques que possam comprometer ou alterar informações. O artigo recomenda mecanismos de backup e recuperação como parte de uma estratégia de defesa em múltiplas camadas.
   
### 1.6 Análise crítica: qual a melhor abordagem?
Posição fundamentada do grupo sobre como distribuir dados com segurança
no contexto do uso de IA.
#### -Reposta:
   * A melhor abordagem para distribuir dados com segurança no contexto do uso de IA é utilizar uma estratégia de defesa em camadas, combinando controle de acesso, menor privilégio, VIEWs, auditoria, monitoramento e backups. Essa abordagem é mais segura do que depender de apenas um mecanismo, pois os ataques baseados em IA podem ser automatizados e adaptativos, conseguindo contornar defesas tradicionais.

   * Para o grupo, os dados devem ser distribuídos somente para quem realmente precisa deles, utilizando roles e permissões (definem o que cada usuário pode acessar ou fazer) e VIEWs (mostram apenas os dados necessários). Além disso, o monitoramento (acompanhamento das atividades) e a auditoria (registro das ações realizadas) permitem identificar e investigar comportamentos suspeitos. Os backups complementam essa proteção ao possibilitar a recuperação dos dados em caso de ataques ou falhas. O artigo também recomenda uma abordagem em múltiplas camadas, com monitoramento e recuperação rápida.
## 2. Exemplos e Casos

Exemplo de view `clientes_visiveis` no PostgreSQL e exemplo de role/permissão.
Um caso real: sistema de vendas, clínica ou biblioteca.
-Reposta:

Para aplicar os conceitos apresentados anteriormente, podemos considerar uma empresa que possui um sistema de vendas e permite que usuários especialistas utilizem ferramentas de Inteligência Artificial para auxiliar na criação de consultas e na análise dos dados. Nesse cenário, o DBA precisa definir quais informações cada usuário pode acessar, evitando que uma consulta gerada pela IA permita acesso a dados que não são necessários para sua função.

### Exemplo de View `clientes_visiveis`

Uma empresa pode possuir uma tabela de clientes com informações como nome, CPF, endereço e telefone. Entretanto, um analista de vendas pode precisar apenas do nome e do telefone dos clientes para realizar suas atividades.

Nesse caso, o DBA pode criar uma **view**, chamada `clientes_visiveis`, contendo somente as informações necessárias para esse usuário. Dessa forma, o analista não precisa ter acesso direto a todos os dados existentes na tabela original.

Essa estratégia permite controlar quais informações ficam disponíveis para cada perfil de usuário. No cenário proposto, isso é importante porque uma ferramenta de IA pode gerar uma consulta que solicite mais informações do que o usuário realmente precisa. A view funciona como uma camada de controle, permitindo que o usuário consulte os dados necessários sem ter acesso a todas as informações da tabela original.

O livro **Database System Concepts**, de Abraham Silberschatz, Henry F. Korth e S. Sudarshan, apresenta as views como relações virtuais definidas a partir de consultas. No exemplo apresentado pelos autores, um funcionário precisa consultar informações de professores de determinado departamento, mas não possui autorização para acessar diretamente toda a relação de professores. A view permite disponibilizar somente as informações que esse funcionário está autorizado a consultar.

### Exemplo de Role e Permissão

Outro mecanismo importante é a utilização de **roles**. Em uma empresa, o DBA pode criar uma role específica para os analistas de vendas, definindo as permissões necessárias para esse perfil.

Por exemplo, uma `role_analista_vendas` poderia permitir que seus usuários consultassem as informações necessárias para elaborar relatórios, sem conceder acesso a dados que não fazem parte de suas atividades.

A utilização de roles facilita o gerenciamento das permissões, pois o DBA pode definir as autorizações para um determinado perfil e depois associar esse perfil aos usuários. Assim, não é necessário configurar individualmente todas as permissões de cada funcionário.

No capítulo sobre autorização do livro **Database System Concepts**, os autores apresentam o uso de roles como uma forma de organizar as autorizações do banco de dados. Uma role pode receber privilégios e depois ser atribuída a usuários, fazendo com que esses usuários recebam as permissões associadas à role.

### Caso prático: sistema de vendas

Considere uma empresa que possui milhares de clientes e realiza vendas diariamente. Os analistas utilizam ferramentas de IA para auxiliar na criação de consultas e na produção de relatórios.

Sem uma política adequada de acesso, um usuário poderia visualizar informações pessoais que não são necessárias para sua atividade. Além disso, uma consulta gerada pela IA pode solicitar uma quantidade de dados maior do que a pretendida pelo usuário.

Para evitar esse problema, o DBA pode organizar os acessos por meio de **roles e views**. Os analistas receberiam uma role compatível com suas funções e poderiam consultar views que disponibilizassem somente os dados necessários para suas atividades.

Assim, a IA seria utilizada como uma ferramenta de auxílio à análise, mas não definiria quais dados o usuário pode acessar. Essa decisão continuaria sendo controlada pelas permissões e pelas estruturas de segurança definidas no banco de dados.

Esse modelo segue o **Princípio do Menor Privilégio**, pois o usuário recebe somente as permissões necessárias para realizar sua função. Dessa forma, mesmo que a IA gere uma consulta mais complexa ou solicite informações que o usuário não deveria acessar, as permissões definidas pelo DBA continuam limitando o acesso aos dados.

### Referência utilizada nesta seção

SILBERSCHATZ, Abraham; KORTH, Henry F.; SUDARSHAN, S. **Database System Concepts**. 7th ed. New York: McGraw-Hill, 2020. Capítulos 4 e 16.

## 3. Referências

Fontes consultadas (livros, artigos, documentação oficial do PostgreSQL,
materiais do curso).

## 4. Conclusões

Aprendizados, reflexões e principais pontos observados pelo grupo.

## Link do Repositório Git