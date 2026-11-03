[README.md](https://github.com/user-attachments/files/34329564/README.md)
# Coruja Surf — Entrega 2: Modelo Lógico, Implementação SQL e Apresentação Final

Modelagem de um sistema de gestão de informações para uma loja de roupas com vendas presenciais e online.

> Itens marcados com `[PREENCHER]` dependem de informações que só o grupo tem (RGM, telefone, datas, números reais). Apague este aviso antes de entregar.

## Integrantes

| Nome completo do aluno | RGM | Usuário do GitHub |
|---|---|---|
| Victor Alves Raimundo | [PREENCHER] | zVitou |
| Rafael Dias Andrade | [PREENCHER] | [PREENCHER] |
| Gustavo Henrique Ribeiro da Silva | [PREENCHER] | [PREENCHER] |
| João Paulo [sobrenome completo] | [PREENCHER] | [PREENCHER] |

## Índice de artefatos

| Artefato | Arquivo |
|---|---|
| DER conceitual revisado | [PREENCHER: ex. `diagramas/DER_Coruja_Surf.pdf`] |
| Modelo lógico | [PREENCHER: ex. `diagramas/Modelo_Logico_Coruja_Surf.pdf`] |
| Dicionário de dados (HTML ou .md para GTI) | [PREENCHER: ex. `docs/dicionario_de_dados.html`] |
| Levantamento completo | [PREENCHER: ex. `levantamento/levantamento.md`] |
| Script SQL completo | [PREENCHER: ex. `docs/script.sql`] |
| Massa de dados (se separada) | [PREENCHER: ex. `docs/massa_de_dados.sql`] |
| Slides da apresentação | [PREENCHER] |
| Evidências (fotos JPG/PNG) | [PREENCHER: ex. `evidencias/`] |

---

## 1.1 Revisão do Modelo Conceitual

### Caracterização da organização

**Nome e natureza:** Coruja Surf — comércio varejista de vestuário (roupas de estilo surf), com vendas presenciais e online. Organização com fins lucrativos.

**Contexto e porte:**

| Item | Valor |
|---|---|
| Fins lucrativos | Sim |
| Pessoas que usarão o sistema | 1 proprietário + cerca de 4 colaboradores |
| Dispositivo principal de uso | Celular |
| Clientes cadastrados/ativos | [PREENCHER: número informado pelo responsável] |
| Vendas presenciais por semana/mês | [PREENCHER] |
| Pedidos online por semana/mês | [PREENCHER] |
| Produtos (itens distintos com tamanho/cor) no catálogo | [PREENCHER] |
| Controle atual | Papel, sem sistema integrado |

**Problemas e necessidades identificados:**

| Código | Problema |
|---|---|
| P1 | Controle de estoque inadequado: não se sabe com precisão o que há disponível nem o que está acabando. |
| P2 | Falta de cadastro de clientes, produtos e funcionários (dados espalhados em papel). |
| P3 | Dificuldade para acompanhar vendas e pedidos (online e presencial) e seus históricos. |
| P4 | Dificuldade para acompanhar pagamentos e comprovantes (o que foi pago, pendente ou recusado). |
| P5 | Falta de avisos sobre pedidos novos, pagamentos recebidos e estoque baixo. |
| P6 | Falta de controle de acesso: informações financeiras e administrativas não são restritas ao proprietário. |

**Escopo do sistema:** o banco reúne os dados de toda a operação da loja: clientes, produtos, estoque, vendas presenciais com itens, pedidos online com itens, pagamentos, usuários com perfis e notificações. Não se restringe ao estoque, que é apenas um dos problemas declarados.

**Justificativa da escolha:** [PREENCHER: por que a Coruja Surf; declarar se algum integrante tem vínculo com a loja ou com o responsável. O vínculo não gera desconto, mas não dispensa a comprovação da entrevista no local].

**Evidências da organização:**

- Perfil no Google Meu Negócio: [PREENCHER link]
- Endereço completo: [PREENCHER]
- Contato (telefone/e-mail/rede social): [PREENCHER]
- Fotos (arquivos JPG/PNG dentro do repositório): [PREENCHER: ex. `evidencias/fachada.jpg`]

> Pendências da Entrega 1 que precisam ser fechadas nesta etapa: CNPJ, endereço e contato, site/rede social, regras detalhadas de pagamento, estoque e permissões, necessidade de relatórios.

**Responsável pela organização:** Antônio Gracia Ferreira Júnior — telefone: [PREENCHER].

### Relato da entrevista

- **Quem:** Antônio Gracia Ferreira Júnior (proprietário) [CONFIRMAR função]. Integrantes presentes: [PREENCHER].
- **Quando e onde:** [PREENCHER data] na loja Coruja Surf, [PREENCHER endereço].
- **Comprovação:** foto da entrevista no local: [PREENCHER arquivo, ex. `evidencias/entrevista.jpg`] (já existe `IMG-20260913-WA0112.jpg` na raiz; mova para a pasta de evidências e confira se mostra o ambiente da loja).
- **Achados por observação presencial:** [PREENCHER: como a venda é anotada, onde fica o estoque, que papéis circulam].
- **Achados por resposta do entrevistado:** [PREENCHER].
- **Nova visita (se houve) e o que mudou desde a Entrega 1:** [PREENCHER].
- **Levantamento completo:** [levantamento/levantamento.md](levantamento/levantamento.md)

**Resumo do levantamento:** a loja opera com registros em papel. O proprietário precisa saber o que vende, o que está em estoque, quais pedidos online estão pendentes e quais pagamentos foram recebidos. Os colaboradores usam o sistema pelo celular, com acesso restrito. Funcionário não deve ver informações financeiras e administrativas.

### Processos de negócio

| Código | Processo | Dados envolvidos |
|---|---|---|
| PR01 | Cadastro de clientes | nome, telefone, e-mail, endereço, data de cadastro |
| PR02 | Cadastro de produtos | nome, descrição, categoria, tamanho, cor, preço, situação (ativo/inativo) |
| PR03 | Controle de estoque | por produto: quantidade atual, estoque mínimo, data da última atualização |
| PR04 | Venda presencial | data, cliente (opcional), usuário que registrou, status; para cada item: produto, quantidade, preço unitário (subtotal e total calculados) |
| PR05 | Pedido online | data, cliente, status (Recebido → Pagamento pendente → Pago → Em preparação → Enviado → Concluído/Cancelado), observação; para cada item: produto, quantidade, preço unitário |
| PR06 | Pagamento e comprovante | valor, forma (Pix, dinheiro, cartão de crédito/débito, boleto, transferência), parcelas, status, comprovante, data |
| PR07 | Consulta de históricos | vendas, pedidos e clientes |
| PR08 | Notificações | tipo (estoque baixo, pagamento recebido, novo pedido, aviso geral), mensagem, destinatário, lida/não lida |
| PR09 | Controle de usuários e permissões | nome, e-mail, senha (hash), perfil (Proprietário/Funcionário), ativo |

**Processos prováveis não incluídos e justificativa:** [PREENCHER após confirmar com o responsável]. Candidatos a justificar: compras de fornecedores, trocas e devoluções, emissão de nota fiscal, entrega/frete, programa de fidelidade.

### Requisitos

**Requisitos funcionais**

| Código | Requisito |
|---|---|
| RF01 | Cadastrar e consultar clientes com nome, telefone, e-mail, endereço e data de cadastro. |
| RF02 | Consultar o histórico de vendas e pedidos de cada cliente. |
| RF03 | Cadastrar e consultar produtos com nome, descrição, categoria, tamanho, cor, preço e situação. |
| RF04 | Controlar entradas e saídas de estoque de cada produto, atualizando a quantidade atual. |
| RF05 | Consultar a quantidade disponível e o estoque mínimo de cada produto. |
| RF06 | Registrar vendas com data, cliente (opcional), usuário responsável e status e, para cada item, produto, quantidade e preço unitário, calculando subtotal e total. |
| RF07 | Registrar pedidos online com cliente, data, observação e itens (produto, quantidade, preço unitário) e acompanhar o status. |
| RF08 | Registrar pagamentos de venda ou pedido com valor, forma, parcelas, status, comprovante e data. |
| RF09 | Consultar históricos de vendas e pedidos por período, status e cliente. |
| RF10 | Gerar notificações de novo pedido, pagamento recebido e estoque baixo. |
| RF11 | Cadastrar usuários com nome, e-mail, senha e perfil, e ativar/desativar acesso. |
| RF12 | Diferenciar proprietário e funcionário, restringindo informações financeiras ao proprietário. |
| RF13 | Marcar notificações como lidas. |

**Requisitos não funcionais**

| Código | Requisito |
|---|---|
| RNF01 | Interface responsiva, priorizando celulares. |
| RNF02 | Autenticação de usuários por e-mail e senha. |
| RNF03 | Controle de acesso por perfil. |
| RNF04 | Senhas armazenadas somente como hash, nunca em texto puro. |
| RNF05 | Consistência dos dados garantida por chaves, restrições e transações. |
| RNF06 | Consultas rápidas nos históricos (índices por data e status). |
| RNF07 | Possibilidade de expansão futura do modelo. |

**Requisitos prováveis não incluídos e justificativa:** [PREENCHER].

### Regras de negócio

| Código | Regra |
|---|---|
| RN01 | A venda pode ser presencial ou online (vendas presenciais em `venda`; online em `pedido`). |
| RN02 | Toda venda deve registrar os produtos vendidos (itens com quantidade e preço unitário). |
| RN03 | A saída de produtos deve atualizar o estoque. |
| RN04 | Pedidos online podem ter comprovante de pagamento. |
| RN05 | O sistema acompanha o status de vendas, pedidos e pagamentos. |
| RN06 | Deve haver alerta quando a quantidade atual for menor ou igual ao estoque mínimo. |
| RN07 | Informações administrativas e financeiras são restritas ao proprietário. |
| RN08 | Existem os perfis Proprietário e Funcionário. |
| RN09 | A utilização deve priorizar dispositivos móveis. |
| RN10 | Todo produto cadastrado nasce com registro de estoque (quantidade 0, mínimo 5). |
| RN11 | Preço, quantidade em estoque e valores monetários não podem ser negativos; a quantidade de cada item deve ser maior que zero. |
| RN12 | Cada pagamento pertence a uma venda **ou** a um pedido, nunca aos dois. |
| RN13 | O valor total da venda/pedido é a soma dos subtotais dos seus itens. |
| RN14 | Venda/pedido com cliente excluído permanece no histórico (cliente fica nulo). Venda, pedido, produto e usuário com histórico não podem ser excluídos. |

**Regras prováveis não incluídas e justificativa:** [PREENCHER]. Candidatos: LGPD (dados pessoais de clientes), emissão de nota fiscal, política de troca, validade/unicidade de CPF.

### Notação e software do DER

- DER criado no software: [PREENCHER: ex. brModelo]
- Arquivo: [PREENCHER]

**Resumo do DER revisado (entidades e cardinalidades):**

| Relacionamento | Cardinalidade |
|---|---|
| Cliente realiza Venda | Cliente (0,n) — Venda (0,1) |
| Cliente realiza Pedido | Cliente (0,n) — Pedido (0,1) |
| Usuário registra Venda | Usuário (0,n) — Venda (1,1) |
| Usuário recebe Notificação | Usuário (0,n) — Notificação (1,1) |
| Produto possui Estoque | Produto (1,1) — Estoque (1,1) |
| Venda é composta de Produto (entidade associativa ITEM_VENDA: quantidade, preço unitário, subtotal) | Venda (1,n) — Produto (0,n) |
| Pedido é composto de Produto (entidade associativa ITEM_PEDIDO: quantidade, preço unitário, subtotal) | Pedido (1,n) — Produto (0,n) |
| Venda possui Pagamento | Venda (0,n) — Pagamento (0,1) |
| Pedido possui Pagamento | Pedido (0,n) — Pagamento (0,1) |

### Caso A — apontamentos da correção da Entrega 1

| Apontamento da correção da E1 | O que mudou no trabalho | Por quê |
|---|---|---|
| [PREENCHER com cada apontamento recebido] | [PREENCHER] | [PREENCHER] |

> Atenção: apontamento não citado nesta tabela é tratado como não corrigido.

---

## 1.2 Conversão do Modelo Conceitual para o Modelo Lógico

**Entidades → Tabelas:** cada entidade virou uma tabela: `cliente`, `usuario`, `produto`, `estoque`, `venda`, `item_venda`, `pedido`, `item_pedido`, `pagamento`, `notificacao`.

**Atributos → Colunas:**

| Tipo de atributo | Conversão |
|---|---|
| Identificadores | `INT AUTO_INCREMENT` (chave substituta) |
| Textos curtos | `VARCHAR` com tamanho ajustado ao conteúdo |
| Textos longos | `TEXT` (descrição, observação, mensagem) |
| Valores monetários | `DECIMAL(10,2)` |
| Datas com hora | `DATETIME` com `DEFAULT CURRENT_TIMESTAMP` quando for data de criação |
| Domínios fechados (perfil, status, forma de pagamento, tipo de notificação) | `ENUM` |
| Indicadores sim/não | `BOOLEAN` |
| Atributos derivados (`subtotal` do item) | Coluna gerada (`GENERATED ALWAYS AS ... STORED`) |

**Relacionamentos → Chaves:**

| Relacionamento | Tradução |
|---|---|
| 1:N (cliente→venda, cliente→pedido, usuário→venda, usuário→notificação, venda→pagamento, pedido→pagamento) | FK no lado N |
| 1:1 (produto→estoque) | FK em `estoque.id_produto` com `UNIQUE` |
| N:N (venda–produto, pedido–produto) | Tabelas associativas `item_venda` e `item_pedido`, com FK para os dois lados e atributos próprios (quantidade, preço unitário, subtotal) |
| Pagamento de venda ou de pedido | Duas FKs opcionais em `pagamento` (`id_venda`, `id_pedido`), uma sempre nula (RN12) |

**Cardinalidades:** (0,1) no lado do cliente nas vendas e pedidos vira FK `NULL`; (1,1) vira FK `NOT NULL`; (1,n) de venda/pedido para itens é garantida pela aplicação (o banco permite a venda sem itens; ver auditoria A02/A03).

**Generalização/especialização:** o DER não possui. [CONFIRMAR]

---

## 1.3 Definição de Chaves Primárias e Estrangeiras

| Tabela | Chave primária | Chaves estrangeiras |
|---|---|---|
| `cliente` | `id_cliente` | — |
| `usuario` | `id_usuario` | — |
| `produto` | `id_produto` | — |
| `estoque` | `id_estoque` | `id_produto` → `produto` (UNIQUE) |
| `venda` | `id_venda` | `id_cliente` → `cliente` (NULL); `id_usuario` → `usuario` |
| `item_venda` | `id_item_venda` | `id_venda` → `venda`; `id_produto` → `produto` |
| `pedido` | `id_pedido` | `id_cliente` → `cliente` (NULL) |
| `item_pedido` | `id_item_pedido` | `id_pedido` → `pedido`; `id_produto` → `produto` |
| `pagamento` | `id_pagamento` | `id_venda` → `venda` (NULL); `id_pedido` → `pedido` (NULL) |
| `notificacao` | `id_notificacao` | `id_usuario` → `usuario` |

---

## 1.4 Processo de Normalização (1FN, 2FN e 3FN)

**1FN — grupos repetitivos e multivalorados:** os itens de uma venda ou pedido não ficam como lista dentro da venda/pedido: viraram linhas em `item_venda` e `item_pedido`. Cada coluna guarda um único valor. O endereço do cliente é tratado como texto único `[CONFIRMAR: se o grupo decidir separar logradouro, número, bairro e CEP, atualizar aqui e no SQL]`. Tamanho e cor ficam em colunas próprias de `produto`, e cada variação é um produto.

**2FN — dependências parciais:** as tabelas usam chave primária simples (`id_...`), então não há dependência parcial. Nas tabelas de itens, quantidade e preço dependem do item inteiro (venda + produto), não só de uma parte.

**3FN — dependências transitivas:**

| Situação | Tratamento |
|---|---|
| Dados do produto (nome, categoria, preço) repetidos em cada item | Ficam só em `produto`; o item guarda apenas a FK |
| Dados do cliente repetidos em cada venda/pedido | Ficam só em `cliente`; venda/pedido guardam a FK |
| Dados de estoque misturados ao produto | Separados em `estoque`, pois mudam em ritmo diferente e por motivos diferentes |
| `preco_unitario` no item | **Não é redundância**: é o preço praticado no momento da venda (histórico), que pode diferir do preço atual do produto |
| `valor_total` em `venda` e `pedido` | Atributo derivado mantido deliberadamente por desempenho, protegido por triggers que o recalculam (RN13) |

**Justificativa do processo:** a 1FN evita itens empilhados numa célula e permite somar vendas por produto. A 2FN e a 3FN evitam que uma mudança de nome, preço ou endereço precise ser feita em vários lugares e gere inconsistência.

---

## 1.5 Justificativas Técnicas das Decisões

**Chaves primárias:** `INT AUTO_INCREMENT` em todas as tabelas, pois não há identificador natural estável (e-mail e nome mudam; produtos têm variações de tamanho/cor).

**Chaves estrangeiras e relacionamentos:**

| FK | Relacionamento | Ação | Motivo |
|---|---|---|---|
| `venda.id_cliente`, `pedido.id_cliente` | Cliente realiza venda/pedido | `ON DELETE SET NULL` | Preserva o histórico se o cliente for removido (RN14) |
| `venda.id_usuario` | Usuário registra venda | `RESTRICT` | Toda venda tem responsável (RN05, RN07) |
| `item_venda.id_venda`, `item_pedido.id_pedido` | Venda/pedido possui itens | `CASCADE` | Item não existe sem a venda/pedido |
| `item_*.id_produto`, `estoque.id_produto` | Produto em itens e estoque | `RESTRICT` | Produto com histórico não é apagado (RN14) |
| `pagamento.id_venda`, `pagamento.id_pedido` | Pagamento de venda ou pedido | `RESTRICT` | Pagamento é registro financeiro (RN05, RN14) |
| `notificacao.id_usuario` | Usuário recebe notificação | `CASCADE` | Notificação só faz sentido para o usuário |

**Restrições:**

| Restrição | Regra |
|---|---|
| `email UNIQUE` em `cliente` e `usuario` | RN08 (identificação única do usuário) |
| `usuario.senha_hash NOT NULL` | RNF04 |
| `usuario.perfil ENUM('Proprietario','Funcionario')` | RN07, RN08 |
| `produto.preco >= 0`; `estoque.quantidade_atual >= 0`; `estoque.estoque_minimo >= 0` | RN11 |
| `item_*.quantidade > 0`; `item_*.preco_unitario >= 0`; `valor_total >= 0` | RN02, RN11 |
| `estoque.id_produto UNIQUE` | Um registro de estoque por produto (RN03, RN10) |
| `ENUM` de status em venda, pedido e pagamento | RN05 |
| `ENUM` de forma de pagamento | RN04 |
| Índices por data e status | RNF06 |
| `CHECK ((id_venda IS NULL) <> (id_pedido IS NULL))` em `pagamento` | RN12 (**adicionar ao script**, hoje só está no comentário) |

**Decisões arquiteturais:**

| Decisão | Motivo |
|---|---|
| Venda (presencial) e pedido (online) em tabelas separadas | Fluxos e status diferentes (o pedido tem etapas de envio) |
| Triggers de criação de estoque e de recálculo de totais | Mantêm RN10 e RN13 sem depender da aplicação |
| Views (`vw_estoque_baixo`, `vw_historico_vendas`, `vw_historico_pedidos`, `vw_total_vendas_por_mes`) | Consultas prontas para a interface e para BI |
| Baixa automática de estoque na aplicação ou em procedure transacional | Limitação conhecida do script atual (RN03) `[PREENCHER: decisão final do grupo]` |

---

## 1.6 Proposta de Arquitetura Analítica para BI e IA

**Informações estratégicas:** quais produtos giram mais e quais ficam parados; quando o estoque vai acabar; faturamento por período, categoria e canal (presencial × online); formas de pagamento mais usadas; gargalos no fluxo dos pedidos online; clientes mais recorrentes.

**KPIs propostos:**

| Código | KPI | Fórmula | Período |
|---|---|---|---|
| K1 | Faturamento | Soma de `valor_total` das vendas confirmadas/concluídas e pedidos pagos | Mensal |
| K2 | Ticket médio | Faturamento ÷ número de vendas/pedidos | Mensal |
| K3 | Produtos abaixo do estoque mínimo | Contagem em que `quantidade_atual <= estoque_minimo` | Diário |
| K4 | Taxa de cancelamento | Cancelados ÷ total de vendas/pedidos | Mensal |
| K5 | Pagamentos pendentes | Contagem e valor de pagamentos com status Pendente | Semanal |
| K6 | Participação por forma de pagamento | Valor por forma ÷ valor total pago | Mensal |
| K7 | Produtos mais vendidos | Soma de `quantidade` por produto | Mensal |

**Potencial para BI:** o modelo fornece fatos (`item_venda`, `item_pedido`, `pagamento`) ligados a dimensões (`produto`, `cliente`, `usuario`, tempo), o que sustenta dashboards de faturamento, estoque e pagamentos. As views já agregam por mês e por situação.

**Aplicações de IA:** previsão de demanda por produto e categoria a partir do histórico de itens; sugestão de reposição quando o estoque tende a ficar abaixo do mínimo; recomendação de produtos complementares a partir de itens comprados juntos; detecção de padrões de recusa/estorno em pagamentos.

**Rastreabilidade** (as consultas G/A abaixo precisam existir no script com esses códigos; ver seção 3):

| Problema ou KPI | Tabelas envolvidas | Consulta |
|---|---|---|
| P1 — controle de estoque inadequado | `produto`, `estoque` | G01 |
| P2 — falta de cadastros | `cliente`, `produto`, `usuario` | G02 |
| P3 — acompanhar vendas e pedidos | `venda`, `pedido`, `item_venda`, `item_pedido`, `cliente`, `usuario` | G03, G04 |
| P4 — acompanhar pagamentos | `pagamento`, `venda`, `pedido` | G05 |
| P5 — falta de avisos | `notificacao`, `usuario` | G06 |
| P6 — controle de acesso | `usuario` | G07 |
| K1 — faturamento mensal | `venda`, `pedido` | G08 |
| K2 — ticket médio | `venda`, `pedido` | G09 |
| K3 — abaixo do mínimo | `produto`, `estoque` | G01 |
| K4 — taxa de cancelamento | `venda`, `pedido` | G10 |
| K5 — pagamentos pendentes | `pagamento` | G05 |
| K6 — forma de pagamento | `pagamento` | G11 |
| K7 — produtos mais vendidos | `item_venda`, `item_pedido`, `produto` | G12 |
| RN12, RN13, RN03, RN02 (auditoria) | conforme a regra | A01 a A06 |

---

## 2. Modelo Lógico Relacional

- Software utilizado: [PREENCHER: ex. brModelo]
- Arquivo do diagrama: [PREENCHER]

O diagrama mostra tabelas, colunas com tipo, PK, FK e cardinalidades convertidas. NOT NULL, UNIQUE, CHECK e DEFAULT estão no dicionário de dados: [PREENCHER link].

---

## 3. Script SQL Completo

- Arquivo: [PREENCHER: `docs/script.sql`]
- SGBD: MySQL 8.0+

Ordem do script: CREATE DATABASE → CREATE TABLE com constraints → INSERT (massa) → SELECT com JOIN → UPDATE → DELETE → consultas gerenciais (G01…) → consultas de auditoria (A01…).

| Código | Pergunta | Atende |
|---|---|---|
| G01 | Quais produtos estão com estoque abaixo ou igual ao mínimo? | P1, K3 |
| G02 | Quantos clientes, produtos e usuários ativos estão cadastrados? | P2 |
| G03 | Qual o histórico de vendas, com cliente e usuário responsável? | P3 |
| G04 | Qual o status atual dos pedidos online e seus itens? | P3 |
| G05 | Quais pagamentos estão pendentes, e de quanto? | P4, K5 |
| G06 | Quais notificações não lidas cada usuário tem? | P5 |
| G07 | Quantos usuários há por perfil e quais estão ativos? | P6 |
| G08 | Qual o faturamento por mês? | K1 |
| G09 | Qual o ticket médio por mês? | K2 |
| G10 | Qual a taxa de cancelamento de vendas e pedidos? | K4 |
| G11 | Quanto foi pago por forma de pagamento? | K6 |
| G12 | Quais os produtos mais vendidos? | K7 |
| A01 | Existe pagamento ligado a venda e pedido ao mesmo tempo, ou a nenhum? | RN12 |
| A02 | Existe venda sem nenhum item? | RN02 |
| A03 | Existe pedido sem nenhum item? | RN02 |
| A04 | O `valor_total` de alguma venda/pedido difere da soma dos itens? | RN13 |
| A05 | Existe produto sem registro de estoque? | RN10 |
| A06 | Existe estoque abaixo do mínimo sem notificação de estoque baixo? | RN06 |

> Estas consultas ainda precisam ser escritas no script com cabeçalho `-- G01 — pergunta / -- Atende: ...`. Teste o script do zero antes de entregar.

---

## 4. Massa de Dados

- Arquivo: [PREENCHER: dentro do script ou `docs/massa_de_dados.sql`]
- Os dados são fictícios; nenhum dado real de cliente da Coruja Surf foi usado.

| Tabela | Registros | Justificativa com base no porte real |
|---|---|---|
| `usuario` | [PREENCHER] | 1 proprietário + 4 colaboradores |
| `cliente` | [PREENCHER] | [PREENCHER: clientes ativos informados] |
| `produto` | [PREENCHER] | [PREENCHER: catálogo real, com variações de tamanho e cor] |
| `estoque` | igual a `produto` | Um registro por produto (RN10) |
| `venda` / `item_venda` | [PREENCHER] | [PREENCHER: vendas por semana × período coberto] |
| `pedido` / `item_pedido` | [PREENCHER] | [PREENCHER: pedidos online por semana × período coberto] |
| `pagamento` | [PREENCHER] | Um ou mais por venda/pedido |
| `notificacao` | [PREENCHER] | Estoque baixo, novos pedidos, pagamentos |

**Situações que a massa precisa cobrir:** vendas e pedidos cancelados; clientes sem compras; produtos abaixo do mínimo; pagamentos em todas as formas e status (incluindo recusado e estornado); registros em vários meses; venda sem cliente; notificações lidas e não lidas.

---

## 5. Repositório GitHub

- Relatório técnico: este `README.md`
- Dicionário de dados: [PREENCHER link]
- Diagramas: [PREENCHER links]
- Levantamento e evidências: [PREENCHER links]
- Script SQL: [PREENCHER link]
- Histórico de commits distribuído entre todos os integrantes, cada um com a própria conta do GitHub e nome compatível com a tabela de Integrantes.

---

## 6. Uso de Inteligência Artificial

Preencha **uma linha por uso relevante** (inclusive os da Entrega 1, como o ChatGPT usado no README e no dicionário, se continuaram nesta etapa).

| Item | Registro |
|---|---|
| Ferramenta e etapa | [PREENCHER: ex. Claude — organização do README conforme esqueleto e rascunho da seção de rastreabilidade] |
| Motivação | [PREENCHER] |
| Prompt(s) utilizados | [PREENCHER texto exato ou muito próximo] |
| Resposta recebida | [PREENCHER resumo] |
| Fontes consultadas e verificadas | [PREENCHER] |
| Trechos rejeitados ou corrigidos | [PREENCHER] |
| Justificativa da escolha final | [PREENCHER] |
| Reflexão crítica | [PREENCHER limites, erros e vieses] |

Repita a tabela para cada uso: levantamento de processos/requisitos/regras, normalização, geração da massa de dados, consultas SQL, slides. Se alguma etapa não usou IA, declare isso explicitamente.

---

## 7. Apresentação Corporativa Final

- Slides: [PREENCHER link/arquivo]

Roteiro do pitch (8 minutos): 1) problema; 2) solução; 3) modelo lógico; 4) SQL rodando; 5) consultas G e A; 6) BI e IA; 7) benefícios para decisão.
