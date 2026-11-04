# Coruja Surf — Entrega 2: Modelo Lógico, Implementação SQL e Apresentação Final

**Projeto:** Sistema de Gestão de Vendas, Estoque e Pedidos
**Disciplina:** Modelagem de Banco de Dados
**SGBD:** MySQL 8.0+

O projeto tem como objetivo desenvolver um banco de dados relacional para organizar as informações da Coruja Surf, facilitando o controle de clientes, usuários, produtos, estoque, vendas, pedidos, pagamentos e notificações.


## Sumário

- [Integrantes](#integrantes)
- [1. Revisão e modelagem do sistema](#11-revisão-do-modelo-conceitual)
  - [Caracterização da organização](#caracterização-da-organização)
  - [Problemas, escopo e processos](#problemas-identificados)
  - [Requisitos e regras de negócio](#requisitos-funcionais)
  - [Conversão para o modelo lógico](#12-conversão-do-modelo-conceitual-para-o-modelo-lógico)
  - [Chaves primárias e estrangeiras](#13-definição-de-chaves-primárias-e-estrangeiras)
  - [Normalização](#14-processo-de-normalização)
  - [Decisões técnicas](#15-justificativas-técnicas-das-decisões)
  - [BI e IA](#16-proposta-de-bi-e-ia)
- [2. Modelo lógico relacional](#2-modelo-lógico-relacional)
- [3. Implementação SQL](#3-implementação-sql)
- [4. Massa de dados](#4-massa-de-dados)
- [5. Organização do repositório](#5-repositório-github)
- [6. Uso de inteligência artificial](#6-uso-de-inteligência-artificial)
- [7. Apresentação final](#7-apresentação-corporativa-final)


---

## Integrantes

| Nome completo                     | RGM         | GitHub                              |
| --------------------------------- | ----------- | ----------------------------------- |
| Victor Alves Raimundo             | [47745908]  | [zVitou](https://github.com/zVitou) |
| Rafael Dias Andrade               | [PREENCHER] | [syntax-rafa](https://github.com/syntax-rafa) |
| Gustavo Henrique Ribeiro da Silva | [PREENCHER] | [PREENCHER]                         |
| João Paulo [sobrenome completo]   | [PREENCHER] | [PREENCHER]                         |

---

## 1.1 Revisão do Modelo Conceitual

### Caracterização da organização

A Coruja Surf é uma organização do ramo de comércio varejista de vestuário, com vendas presenciais e on-line, voltada para roupas de estilo surf.

| Informação                       | Dados                                            |
| -------------------------------- | ------------------------------------------------ |
| Nome                             | Coruja Surf                                      |
| Ramo de atuação                  | Comércio de vestuário                            |
| Tipo de atividade                | Vendas presenciais e on-line                     |
| Fins lucrativos                  | Sim                                              |
| Responsável entrevistado         | Antônio Gracia Ferreira Júnior                   |
| CNPJ                             | Não informado pelo entrevistado                  |
| Pessoas que utilizarão o sistema | 1 proprietário e aproximadamente 4 colaboradores |
| Principal dispositivo de uso     | Celular / smartphone                             |
| Controle atual                   | Registros manuais em papel                       |
| Sistema integrado atual          | Não possui                                       |

O levantamento identificou que a empresa realiza seus controles predominantemente de forma manual, sem um sistema integrado para organizar cadastros, vendas, pedidos e estoque.

O relatório também aponta que as operações de vendas e o acompanhamento das atividades on-line demandam tempo e trabalho manual.

### Problemas identificados

| Código | Problema                                                                                                        |
| ------ | --------------------------------------------------------------------------------------------------------------- |
| P1     | Controle de estoque inadequado, dificultando saber as quantidades disponíveis e os produtos que estão acabando. |
| P2     | Falta de cadastro estruturado de clientes, produtos e funcionários.                                             |
| P3     | Dificuldade para acompanhar vendas, pedidos e seus respectivos históricos.                                      |
| P4     | Dificuldade para acompanhar pagamentos e comprovantes.                                                          |
| P5     | Falta de notificações sobre novos pedidos, pagamentos e estoque baixo.                                          |
| P6     | Necessidade de restringir informações administrativas e financeiras ao proprietário.                            |

### Escopo do sistema

O sistema proposto deverá organizar as informações da operação da Coruja Surf, incluindo:

- Cadastro de clientes.
- Cadastro de usuários e controle de acesso.
- Cadastro de produtos.
- Controle de estoque.
- Registro de vendas presenciais.
- Registro de pedidos on-line.
- Registro dos itens de vendas e pedidos.
- Controle de pagamentos e comprovantes.
- Consulta de históricos.
- Notificações sobre estoque, pedidos e pagamentos.

### Justificativa da escolha

A Coruja Surf foi escolhida por apresentar necessidades relacionadas à organização de dados e ao controle de vendas e estoque. O levantamento permitiu identificar oportunidades de melhoria por meio de um banco de dados relacional, centralizando informações que atualmente são controladas manualmente.

### Evidências da organização

- **Responsável entrevistado:** Antônio Gracia Ferreira Júnior.
- **Localização compartilhada:** [Google Maps — Coruja Surf](https://maps.app.goo.gl/jXdKenokzq6ur3Av8?g_st=aw).
- **CNPJ:** não disponibilizado pelo entrevistado.
- **Endereço completo:** não informado diretamente.
- **Outros dados comerciais:** algumas informações não puderam ser disponibilizadas pelo entrevistado.

### Relato da entrevista

A entrevista foi realizada por meio de uma **videochamada pelo WhatsApp**, com o responsável Antônio Gracia Ferreira Júnior.

| Informação                 | Registro                        |
| -------------------------- | ------------------------------- |
| Entrevistado               | Antônio Gracia Ferreira Júnior  |
| Meio utilizado             | Videochamada pelo WhatsApp      |
| Data                       | Não informada                   |
| Horário visível na captura | 11h39                           |
| Local físico da entrevista | Não informado                   |
| Evidência                  | Captura de tela da videochamada |

Durante a entrevista, foram abordadas questões relacionadas ao funcionamento da empresa, ao controle de vendas, ao estoque, aos pedidos e às necessidades de informatização.

Algumas informações solicitadas não foram disponibilizadas pelo entrevistado, que informou não poder fornecê-las. Por esse motivo, esses dados foram mantidos como não informados, sem estimativas ou preenchimentos por suposição.

**Evidência da entrevista:** inserir a captura de tela da videochamada na pasta `evidencias/`, com o nome `entrevista_videochamada.jpg`.

### Processos de negócio

| Código | Processo             | Descrição                                                |
| ------ | -------------------- | -------------------------------------------------------- |
| PR01   | Cadastro de clientes | Registro das informações dos clientes.                   |
| PR02   | Cadastro de produtos | Registro dos produtos comercializados.                   |
| PR03   | Controle de estoque  | Acompanhamento das quantidades disponíveis.              |
| PR04   | Venda presencial     | Registro das vendas e dos produtos vendidos.             |
| PR05   | Pedido on-line       | Registro e acompanhamento dos pedidos.                   |
| PR06   | Pagamentos           | Registro de valores, formas de pagamento e comprovantes. |
| PR07   | Histórico            | Consulta de vendas, clientes e pedidos.                  |
| PR08   | Notificações         | Avisos sobre estoque baixo, pedidos e pagamentos.        |
| PR09   | Controle de usuários | Gerenciamento de usuários e permissões.                  |

### Requisitos funcionais

| Código | Requisito                                                           |
| ------ | ------------------------------------------------------------------- |
| RF01   | Cadastrar e consultar clientes.                                     |
| RF02   | Consultar o histórico de vendas e pedidos dos clientes.             |
| RF03   | Cadastrar e consultar produtos.                                     |
| RF04   | Controlar entradas e saídas do estoque.                             |
| RF05   | Consultar quantidade disponível e estoque mínimo.                   |
| RF06   | Registrar vendas e seus respectivos itens.                          |
| RF07   | Registrar pedidos on-line e acompanhar seus status.                 |
| RF08   | Registrar pagamentos e comprovantes.                                |
| RF09   | Consultar históricos de vendas e pedidos.                           |
| RF10   | Gerar notificações sobre novos pedidos, pagamentos e estoque baixo. |
| RF11   | Cadastrar usuários e controlar seus perfis.                         |
| RF12   | Restringir informações financeiras conforme o perfil de acesso.     |
| RF13   | Permitir marcar notificações como lidas.                            |

### Requisitos não funcionais

| Código | Requisito                                                       |
| ------ | --------------------------------------------------------------- |
| RNF01  | O sistema deverá priorizar dispositivos móveis.                 |
| RNF02  | O acesso deverá ocorrer por autenticação de usuário.            |
| RNF03  | O sistema deverá possuir controle de acesso por perfil.         |
| RNF04  | As senhas deverão ser armazenadas como hash.                    |
| RNF05  | O banco deverá manter a integridade dos dados.                  |
| RNF06  | As consultas de histórico deverão ser organizadas e eficientes. |
| RNF07  | O modelo deverá permitir futuras expansões.                     |

### Regras de negócio

| Código | Regra                                                                                       |
| ------ | ------------------------------------------------------------------------------------------- |
| RN01   | As vendas presenciais e os pedidos on-line serão registrados separadamente.                 |
| RN02   | Toda venda deverá registrar os produtos vendidos.                                           |
| RN03   | A saída de produtos deverá atualizar o estoque.                                             |
| RN04   | Pedidos on-line poderão possuir comprovantes de pagamento.                                  |
| RN05   | O sistema deverá acompanhar os status de vendas, pedidos e pagamentos.                      |
| RN06   | Deverá existir alerta quando o estoque estiver igual ou abaixo do mínimo.                   |
| RN07   | Informações administrativas e financeiras deverão ser restritas ao proprietário.            |
| RN08   | O sistema deverá diferenciar os perfis de proprietário e funcionário.                       |
| RN09   | A utilização deverá priorizar dispositivos móveis.                                          |
| RN10   | Todo produto cadastrado deverá possuir um registro de estoque.                              |
| RN11   | Preços e quantidades não poderão ser negativos.                                             |
| RN12   | Cada pagamento deverá pertencer a uma venda ou a um pedido, nunca aos dois simultaneamente. |
| RN13   | O valor total de uma venda ou pedido deverá corresponder à soma dos itens.                  |
| RN14   | O histórico deverá ser preservado conforme as regras de exclusão e integridade do banco.    |

### Correções da Entrega 1

| Apontamento do professor                 | Correção realizada |
| ---------------------------------------- | ------------------ |
| [PREENCHER conforme a correção recebida] | [PREENCHER]        |

**Observação:** os apontamentos reais da primeira entrega ainda precisam ser inseridos pelo grupo.

---

## 1.2 Conversão do Modelo Conceitual para o Modelo Lógico

O modelo conceitual foi convertido em tabelas relacionais, utilizando chaves primárias e estrangeiras para representar os relacionamentos entre as entidades.

As dez tabelas utilizadas na implementação atual são:

1. `cliente`
2. `usuario`
3. `produto`
4. `estoque`
5. `venda`
6. `item_venda`
7. `pedido`
8. `item_pedido`
9. `pagamento`
10. `notificacao`

Os relacionamentos entre as tabelas permitem organizar os dados e evitar repetições desnecessárias.

As tabelas `item_venda` e `item_pedido` representam os produtos que fazem parte de cada venda ou pedido.

---

## 1.3 Definição de Chaves Primárias e Estrangeiras

| Tabela        | Chave primária   | Chaves estrangeiras        |
| ------------- | ---------------- | -------------------------- |
| `cliente`     | `id_cliente`     | —                          |
| `usuario`     | `id_usuario`     | —                          |
| `produto`     | `id_produto`     | —                          |
| `estoque`     | `id_estoque`     | `id_produto`               |
| `venda`       | `id_venda`       | `id_cliente`, `id_usuario` |
| `item_venda`  | `id_item_venda`  | `id_venda`, `id_produto`   |
| `pedido`      | `id_pedido`      | `id_cliente`               |
| `item_pedido` | `id_item_pedido` | `id_pedido`, `id_produto`  |
| `pagamento`   | `id_pagamento`   | `id_venda`, `id_pedido`    |
| `notificacao` | `id_notificacao` | `id_usuario`               |

---

## 1.4 Processo de Normalização

### Primeira Forma Normal (1FN)

As tabelas possuem atributos individuais, evitando armazenar vários valores em uma única coluna.

Os produtos de uma venda ou pedido são armazenados separadamente nas tabelas `item_venda` e `item_pedido`.

### Segunda Forma Normal (2FN)

As tabelas possuem chaves primárias próprias, evitando dependências parciais dos atributos em relação à chave.

Os dados dos produtos são armazenados em sua própria tabela, enquanto os itens mantêm apenas as informações necessárias da operação.

### Terceira Forma Normal (3FN)

Os dados de clientes, produtos e usuários são mantidos em tabelas separadas, evitando repetições e dependências desnecessárias.

A tabela `estoque` também é separada de `produto`, permitindo organizar o controle das quantidades disponíveis.

---

## 1.5 Justificativas Técnicas das Decisões

- **Chaves primárias:** identificam cada registro de forma única.
- **Chaves estrangeiras:** mantêm os relacionamentos entre as tabelas.
- **UNIQUE:** impede a repetição de informações que devem ser únicas, como e-mails.
- **NOT NULL:** define campos obrigatórios.
- **CHECK:** valida valores, impedindo quantidades e preços negativos.
- **ENUM:** limita campos a opções previamente definidas.
- **DEFAULT:** define valores iniciais automaticamente.
- **Triggers:** criam registros de estoque ao cadastrar produtos e recalculam os totais das vendas e pedidos.

O banco também utiliza views para facilitar consultas de estoque baixo, históricos e vendas por período.

**Pontos que precisam ser conferidos na implementação:** a regra de pagamento ligado exclusivamente a uma venda ou pedido e a atualização automática do estoque nas operações de saída.

---

## 1.6 Proposta de BI e IA

O banco de dados poderá servir como base para a criação de indicadores que auxiliem a administração da Coruja Surf.

### Indicadores propostos

| Código | Indicador                  | Objetivo                                       |
| ------ | -------------------------- | ---------------------------------------------- |
| K1     | Faturamento mensal         | Acompanhar os resultados das vendas.           |
| K2     | Ticket médio               | Identificar o valor médio das operações.       |
| K3     | Produtos com estoque baixo | Acompanhar produtos que precisam de reposição. |
| K4     | Taxa de cancelamento       | Analisar vendas e pedidos cancelados.          |
| K5     | Pagamentos pendentes       | Acompanhar pagamentos ainda não confirmados.   |
| K6     | Formas de pagamento        | Identificar as formas mais utilizadas.         |
| K7     | Produtos mais vendidos     | Identificar os produtos com maior saída.       |

### Possibilidades de BI

Com esses dados, poderá ser desenvolvido um painel de indicadores para acompanhar vendas, estoque, pedidos e pagamentos.

### Possibilidades de IA

Futuramente, a inteligência artificial poderá auxiliar na previsão de demanda, sugestão de reposição de produtos e identificação de padrões nas vendas.

Essas funcionalidades são propostas futuras e não fazem parte da implementação SQL atual.

---

## 2. Modelo Lógico Relacional

O modelo lógico representa a estrutura relacional do banco de dados: tabelas, atributos, tipos de dados, chaves primárias (PK), chaves estrangeiras (FK) e relacionamentos.

### Estrutura utilizada na implementação SQL

O script SQL atual contém dez tabelas:

| Tabela | Finalidade |
| --- | --- |
| `cliente` | Armazenar os dados dos clientes. |
| `usuario` | Armazenar usuários, credenciais e perfis de acesso. |
| `produto` | Cadastrar os produtos comercializados. |
| `estoque` | Controlar quantidade atual e estoque mínimo dos produtos. |
| `venda` | Registrar vendas presenciais e o usuário responsável. |
| `item_venda` | Registrar os produtos que compõem cada venda. |
| `pedido` | Registrar pedidos realizados por clientes. |
| `item_pedido` | Registrar os produtos que compõem cada pedido. |
| `pagamento` | Registrar pagamentos relacionados a vendas ou pedidos. |
| `notificacao` | Armazenar notificações destinadas aos usuários. |

### Relacionamentos principais

- Um cliente pode possuir várias vendas e vários pedidos.
- Um usuário pode registrar várias vendas e receber várias notificações.
- Um produto possui um registro de estoque.
- Uma venda possui seus itens na tabela `item_venda`.
- Um pedido possui seus itens na tabela `item_pedido`.
- Os itens de venda e de pedido referenciam os produtos cadastrados.
- Os pagamentos podem estar associados a uma venda ou a um pedido, conforme a estrutura atual do SQL.

### Diagrama do modelo lógico

**Arquivo previsto:** `diagramas/Modelo_Logico_Coruja_Surf.pdf`

O diagrama lógico que foi elaborado inicialmente pelo grupo apresenta diferenças em relação às dez tabelas implementadas no SQL. Para a entrega final, ele deverá ser atualizado para refletir a estrutura descrita nesta seção, incluindo as tabelas `VENDA`, `ITEM_VENDA`, `ITEM_PEDIDO`, `ESTOQUE` e `NOTIFICACAO`, além das respectivas PKs e FKs.

**Software utilizado:** [PREENCHER com o nome do programa usado para criar o diagrama].

---

## 3. Implementação SQL

O banco de dados foi desenvolvido utilizando MySQL 8.0 ou versão compatível.

**Nome do banco:** `coruja_surf`

O script SQL contempla:

- Criação do banco de dados.
- Criação das tabelas.
- Definição das chaves primárias e estrangeiras.
- Restrições de integridade.
- Inserção de dados fictícios.
- Triggers para atualização de informações.
- Views para consultas.
- Consultas de demonstração.

### Consultas gerenciais planejadas

| Código | Pergunta respondida                                             |
| ------ | --------------------------------------------------------------- |
| G01    | Quais produtos estão com estoque abaixo ou igual ao mínimo?     |
| G02    | Quantos clientes, produtos e usuários ativos estão cadastrados? |
| G03    | Qual o histórico de vendas e seus responsáveis?                 |
| G04    | Qual o status atual dos pedidos on-line?                        |
| G05    | Quais pagamentos estão pendentes?                               |
| G06    | Quais notificações ainda não foram lidas?                       |
| G07    | Quantos usuários existem por perfil?                            |
| G08    | Qual o faturamento por mês?                                     |
| G09    | Qual o ticket médio por mês?                                    |
| G10    | Qual a taxa de cancelamento?                                    |
| G11    | Quanto foi pago por forma de pagamento?                         |
| G12    | Quais produtos são mais vendidos?                               |

### Consultas de auditoria planejadas

| Código | Verificação                                                                 |
| ------ | --------------------------------------------------------------------------- |
| A01    | Existem pagamentos ligados a uma venda e pedido ao mesmo tempo ou a nenhum? |
| A02    | Existem vendas sem itens?                                                   |
| A03    | Existem pedidos sem itens?                                                  |
| A04    | Os totais correspondem à soma dos itens?                                    |
| A05    | Existem produtos sem registro de estoque?                                   |
| A06    | Existem produtos com estoque baixo sem notificação?                         |

**Importante:** as consultas acima devem estar implementadas e testadas no arquivo SQL final antes da entrega.

---

## 4. Massa de Dados

Os dados utilizados no banco são fictícios e servem para demonstrar o funcionamento das tabelas e relacionamentos.

O script atual possui uma pequena massa de dados de exemplo, incluindo clientes, usuários, produtos, vendas, pedidos, pagamentos e notificações.

A quantidade atual deve ser ampliada ou justificada conforme os números reais de movimentação da organização, caso o entrevistado os disponibilize.

| Tabela        | Registros atuais |
| ------------- | ---------------: |
| `cliente`     |                3 |
| `usuario`     |                2 |
| `produto`     |                4 |
| `estoque`     |                4 |
| `venda`       |                2 |
| `item_venda`  |                3 |
| `pedido`      |                1 |
| `item_pedido` |                2 |
| `pagamento`   |                2 |
| `notificacao` |                2 |

Os dados permitem demonstrar situações como estoque baixo, vendas, pedidos, pagamentos pendentes e notificações.

---

## 5. Repositório GitHub

O repositório do projeto está disponível em:

[**Entrega 2 — Coruja Surf (GitHub)**](https://github.com/zVitou/Entrega-2-quarta-feira)


### Relação dos artefatos

| Artefato | Caminho sugerido no repositório | Situação |
| --- | --- | --- |
| Relatório técnico | `README.md` | Este arquivo |
| DER conceitual | `DER_Coruja_Surf_Conceitual (1).xlsx` | A enviar/confirmar versão revisada |
| Modelo lógico | `mermaid-diagram.png` | Atualizar diagrama para corresponder ao SQL |
| Dicionário de dados | `documentos/dicionario_de_dados_coruja_surf.pdf` | A enviar |
| Levantamento de requisitos | `Relatorio_Levantamento_Requisitos_Coruja_Surf (1).pdf` | A enviar |
| Script SQL | `dicionario_de_dados_coruja_surf.pdf` | A enviar |
| Evidência da entrevista | `prova_entrevista.jpg` | A enviar |
| Slides da apresentação | `apresentacao/apresentacao_final.pptx` | A enviar |

### Evidência da entrevista

A entrevista foi realizada por videochamada pelo WhatsApp. A captura de tela deverá ser adicionada à pasta `evidencias/` com o nome `entrevista_videochamada.jpg`. A imagem registra a chamada, mas não informa a data da entrevista.

### Histórico e colaboração

O grupo deverá manter os arquivos atualizados e utilizar commits para registrar as alterações realizadas por cada integrante. Antes da entrega, conferir se todos os caminhos apresentados nesta seção correspondem a arquivos realmente existentes no repositório.

---

## ## 6. Uso de Inteligência Artificial

| **Item** | **Registro** |
|---|---|
| **Ferramenta utilizada** | ChatGPT (OpenAI),Cloude ia|
| **Etapa do trabalho** | Levantamento de requisitos, identificação das entidades, definição de atributos e relacionamentos e revisão do modelo de dados. |
| **Motivação** | Utilizar a IA como apoio para compreender os requisitos do sistema Coruja Surf, organizar as informações e auxiliar na construção do modelo do banco de dados. |
| **Prompt utilizado** | Solicitação de auxílio para identificar as entidades, atributos, chaves primárias e estrangeiras e relacionamentos necessários para o banco de dados da Coruja Surf, considerando os requisitos apresentados no trabalho. |
| **Resposta recebida** | A IA sugeriu entidades como CLIENTE, PRODUTO, PEDIDO, ITEM_PEDIDO, PAGAMENTO, USUARIO e MOVIMENTACAO_ESTOQUE, além de possíveis atributos, chaves e relacionamentos entre elas. |
| **Fontes verificadas** | Enunciado do trabalho, requisitos apresentados pelo professor e materiais de referência utilizados na atividade. |
| **Trechos corrigidos ou rejeitados** | Foram realizados ajustes no modelo conforme as orientações do professor. Foram mantidas as entidades necessárias, incluindo ITEM_PEDIDO, e removida a entidade FORNECEDOR, pois a empresa produz suas próprias roupas. Também foram considerados os pagamentos parcelados. |
| **Justificativa da escolha final** | O modelo final foi definido com base nos requisitos do projeto e nas correções realizadas pelo grupo, utilizando as sugestões da IA apenas como apoio. |
| **Reflexão crítica** | A inteligência artificial ajudou a organizar as ideias e facilitou o desenvolvimento do modelo de dados. Porém, suas sugestões precisaram ser analisadas e corrigidas para atender corretamente às necessidades do sistema. O grupo manteve a responsabilidade pelas decisões finais. |

---

## 7. Apresentação Corporativa Final

A apresentação deverá ter aproximadamente oito minutos e seguir a sequência:

1. Contextualização da empresa e dos problemas identificados.
2. Apresentação da solução proposta.
3. Demonstração do modelo lógico.
4. Explicação da implementação SQL.
5. Demonstração das consultas gerenciais e de auditoria.
6. Apresentação das possibilidades de BI e IA.
7. Benefícios que o sistema poderá oferecer à organização.

**Link dos slides:** [INSERIR LINK].

---


