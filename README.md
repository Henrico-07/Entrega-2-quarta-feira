[README_Esqueleto_Coruja_Surf.md](https://github.com/user-attachments/files/34329207/README_Esqueleto_Coruja_Surf.md)
# CORUJA SURF — Modelo Lógico, Implementação SQL e Apresentação Final

> **Entrega 2 — Modelagem de Banco de Dados**  
> Este documento reúne a documentação técnica do projeto Coruja Surf. Os campos indicados como **[PREENCHER]** precisam ser completados ou confirmados pelo grupo antes da entrega.

---

## 1. Revisão do modelo conceitual

### 1.1 Caracterização da organização e levantamento dos requisitos

#### 1.1.1 Identificação e contexto da organização

- **Organização:** Coruja Surf
- **Responsável entrevistado:** Antônio Gracia Ferreira Júnior
- **CNPJ:** [PREENCHER — não informado no material consultado]
- **Endereço:** [PREENCHER]
- **Telefone/contato:** [PREENCHER]
- **Perfil de atuação:** comércio de roupas, com produção própria e vendas on-line.
- **Porte e equipe:** o levantamento menciona aproximadamente quatro funcionários, além do proprietário. Confirmar se esse número continua correto.
- **Principais dispositivos utilizados:** celular, conforme informado no levantamento.

A Coruja Surf trabalha com roupas de fabricação própria, sem depender de fornecedores externos para a produção. As vendas on-line têm importância para a operação. Segundo o levantamento, parte dos controles é realizada em papel e não existe atualmente um sistema dedicado que concentre o controle de vendas, pedidos e estoque.

**Evidências da organização:**  
[INSERIR FOTOS/IMAGENS DA ORGANIZAÇÃO, PRODUTOS, LOCAL OU PERFIL COMERCIAL, COM AUTORIZAÇÃO.]

#### 1.1.2 Entrevista e observação

- **Pessoa entrevistada:** Antônio Gracia Ferreira Júnior.
- **Data da entrevista:** [PREENCHER]
- **Local ou meio utilizado:** [PREENCHER]
- **Integrantes que participaram:** [PREENCHER]
- **Houve observação presencial dos processos?** [PREENCHER]
- **Registro fotográfico autorizado:** [PREENCHER / ANEXAR EVIDÊNCIA]

Descrever como são realizados atualmente o cadastro de produtos, o controle de estoque, as vendas, os pedidos on-line e os pagamentos. Não incluir procedimentos que não tenham sido confirmados na entrevista.

#### 1.1.3 Problemas identificados

Com base no levantamento disponível, foram identificadas as seguintes necessidades. O grupo deve confirmar e detalhar cada problema com exemplos reais da organização.

- **P1 — Controle de estoque:** necessidade de registrar entradas e saídas de produtos e acompanhar as quantidades disponíveis, pois o controle atual não é considerado adequado.
- **P2 — Controle de vendas e pedidos:** necessidade de centralizar o registro e o acompanhamento das vendas e dos pedidos on-line, que atualmente não contam com um sistema dedicado.

**Outros pontos levantados:** necessidade de cadastro de clientes e produtos, histórico de operações, registro de pagamentos e notificações relacionadas a estoque, pagamentos e pedidos.

#### 1.1.4 Escopo da solução

O sistema proposto busca apoiar a organização das informações de clientes, usuários, produtos, estoque, vendas, itens de venda, pedidos, itens de pedido, pagamentos e notificações.

**Dentro do escopo:**
- Cadastro e consulta de clientes, usuários e produtos.
- Controle das quantidades em estoque.
- Registro de vendas e seus respectivos itens.
- Registro de pedidos on-line e seus respectivos itens.
- Registro de pagamentos relacionados às vendas ou aos pedidos.
- Consulta ao histórico de vendas e pedidos.
- Notificações relacionadas a estoque, pagamentos e pedidos.

**Fora do escopo ou ainda não especificado:**
- Integração com plataformas externas: [PREENCHER / CONFIRMAR].
- Regras completas de entrega e logística: [PREENCHER / CONFIRMAR].
- Regras detalhadas de cálculo de frete: [PREENCHER / CONFIRMAR].
- Automação da produção das roupas: [PREENCHER / CONFIRMAR].

#### 1.1.5 Requisitos funcionais

Os requisitos abaixo representam as funcionalidades previstas no modelo atual. O grupo deve revisar se todos foram efetivamente solicitados ou validados na entrevista.

| Código | Requisito funcional |
|---|---|
| RF01 | Permitir cadastrar, consultar e atualizar clientes. |
| RF02 | Permitir cadastrar, consultar e atualizar usuários do sistema. |
| RF03 | Permitir cadastrar, consultar e atualizar produtos. |
| RF04 | Permitir registrar e consultar as quantidades de produtos em estoque. |
| RF05 | Permitir registrar vendas. |
| RF06 | Permitir incluir e consultar os itens de cada venda. |
| RF07 | Permitir registrar pedidos on-line. |
| RF08 | Permitir incluir e consultar os itens de cada pedido. |
| RF09 | Permitir registrar pagamentos relacionados a vendas ou pedidos. |
| RF10 | Permitir consultar o histórico de vendas e pedidos. |
| RF11 | Permitir registrar notificações relacionadas a estoque, pagamentos e pedidos. |

#### 1.1.6 Requisitos não funcionais

Os requisitos abaixo são propostas iniciais do grupo e precisam ser validados com o professor e, quando possível, com a organização.

| Código | Requisito não funcional |
|---|---|
| RNF01 | O banco de dados deverá ser implementado em MySQL 8 ou versão compatível. |
| RNF02 | A estrutura deverá manter a integridade dos dados por meio de chaves primárias e estrangeiras. |
| RNF03 | O acesso às informações deverá ser controlado conforme os perfis definidos para o sistema. |
| RNF04 | O sistema deverá permitir utilização em dispositivos móveis, considerando que o celular é o principal dispositivo mencionado no levantamento. |
| RNF05 | As senhas dos usuários não deverão ser armazenadas em texto puro. |

#### 1.1.7 Regras de negócio

As regras abaixo foram organizadas a partir das informações disponíveis. As regras marcadas como propostas precisam ser confirmadas.

| Código | Regra de negócio |
|---|---|
| RN01 | A Coruja Surf trabalha com roupas de fabricação própria, sem fornecedores externos, conforme o levantamento. |
| RN02 | Uma venda pode possuir um ou mais itens de venda. |
| RN03 | Um pedido pode possuir um ou mais itens de pedido. |
| RN04 | Os pagamentos devem estar relacionados a uma venda ou a um pedido. **Confirmar a regra de exclusividade:** cada pagamento pertence a somente um desses registros. |
| RN05 | A compra parcelada pode gerar taxas, e o levantamento informa que essas taxas são pagas pelo cliente. |
| RN06 | O sistema deverá permitir notificações relacionadas a estoque, pagamentos e pedidos. |
| RN07 | O acesso a informações restritas deverá ser limitado a usuários autorizados; os perfis e permissões ainda precisam ser definidos. |
| RN08 | O critério para considerar um produto com estoque baixo ainda precisa ser definido pela organização. |

#### 1.1.8 Correções da Entrega 1

Preencher esta tabela com os apontamentos reais feitos pelo professor. Não inventar correções.

| Apontamento do professor na Entrega 1 | Alteração realizada na Entrega 2 | Onde pode ser verificada |
|---|---|---|
| [PREENCHER] | [PREENCHER] | [PREENCHER] |
| [PREENCHER] | [PREENCHER] | [PREENCHER] |

#### 1.1.9 Diagrama Entidade-Relacionamento revisado

Inserir abaixo o DER conceitual revisado, após aplicar as correções da Entrega 1.

**[INSERIR IMAGEM DO DER CONCEITUAL REVISADO]**

Arquivo: `diagramas/DER_Coruja_Surf.pdf`

---

### 1.2 Conversão do modelo conceitual para o modelo lógico

O modelo lógico foi organizado em tabelas relacionais para representar os dados necessários ao funcionamento do sistema. A implementação SQL atual contém as seguintes tabelas:

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

A tabela `item_pedido` foi incluída na implementação SQL para representar os produtos que compõem cada pedido. O dicionário de dados e os diagramas devem ser atualizados para refletir essa tabela e manter a documentação consistente com o banco implementado.

**[INSERIR EXPLICAÇÃO DA CONVERSÃO DAS ENTIDADES E RELACIONAMENTOS DO DER PARA AS TABELAS.]**

### 1.3 Chaves primárias e estrangeiras

Preencher a tabela com os nomes exatos das colunas existentes no script SQL.

| Tabela | Chave primária (PK) | Chaves estrangeiras (FK) |
|---|---|---|
| `cliente` | [PREENCHER] | [PREENCHER] |
| `usuario` | [PREENCHER] | [PREENCHER] |
| `produto` | [PREENCHER] | [PREENCHER] |
| `estoque` | [PREENCHER] | [PREENCHER] |
| `venda` | [PREENCHER] | [PREENCHER] |
| `item_venda` | [PREENCHER] | [PREENCHER] |
| `pedido` | [PREENCHER] | [PREENCHER] |
| `item_pedido` | [PREENCHER] | [PREENCHER] |
| `pagamento` | [PREENCHER] | [PREENCHER] |
| `notificacao` | [PREENCHER] | [PREENCHER] |

### 1.4 Normalização

Descrever como as tabelas atendem às formas normais, utilizando exemplos do próprio banco.

#### Primeira Forma Normal (1FN)

[EXPLICAR como os atributos armazenam valores atômicos e como os grupos repetidos foram separados em tabelas próprias.]

#### Segunda Forma Normal (2FN)

[EXPLICAR como os atributos não-chave dependem da chave primária completa, especialmente nas tabelas que possuem chave composta, se houver.]

#### Terceira Forma Normal (3FN)

[EXPLICAR como foram evitadas dependências transitivas entre atributos que não são chave.]

### 1.5 Justificativas técnicas

Explicar as decisões de modelagem com referência às regras de negócio (RNxx), por exemplo:

- Uso de PK para identificar unicamente cada registro.
- Uso de FK para manter relacionamentos e integridade referencial.
- Uso de `NOT NULL`, `UNIQUE`, `CHECK`, `DEFAULT` e tipos enumerados, quando aplicável.
- Separação entre `produto` e `estoque`.
- Separação entre `venda` e `item_venda`, e entre `pedido` e `item_pedido`.
- Como a tabela `pagamento` relaciona pagamentos às operações correspondentes.
- Como os perfis de usuário e as notificações apoiam as necessidades levantadas.

**[PREENCHER com justificativas específicas e os códigos RN correspondentes.]**

### 1.6 Proposta de BI/IA e indicadores

A estrutura do banco pode apoiar consultas gerenciais sobre vendas, pedidos e estoque. Os indicadores abaixo são sugestões iniciais; confirmar com a organização quais seriam úteis.

| Indicador (KPI) | Objetivo | Tabelas envolvidas | Consulta SQL |
|---|---|---|---|
| Quantidade de produtos com estoque baixo | Apoiar o acompanhamento do estoque | `produto`, `estoque` | G01 — [CRIAR/IDENTIFICAR] |
| Total de vendas por período | Acompanhar o desempenho das vendas | `venda`, `item_venda` | G02 — [CRIAR/IDENTIFICAR] |
| Produtos mais vendidos | Identificar os produtos com maior saída | `produto`, `item_venda`, `venda` | G03 — [CRIAR/IDENTIFICAR] |
| Pedidos por situação | Acompanhar os pedidos on-line | `pedido`, `item_pedido` | G04 — [CRIAR/IDENTIFICAR] |

**Possibilidade de BI/IA:** [DESCREVER uma proposta realista, como painel de indicadores ou análise de histórico para apoiar decisões. Não afirmar que existe inteligência artificial implementada se ela não estiver no projeto.]

---

## 2. Modelo lógico relacional

Inserir o diagrama lógico com as tabelas, colunas, tipos de dados, PK, FK e cardinalidades. O diagrama deve estar coerente com o script SQL final.

**[INSERIR IMAGEM/PDF DO MODELO LÓGICO.]**

Arquivo sugerido: `diagramas/Modelo_Logico_Coruja_Surf.pdf`

---

## 3. Implementação SQL

O banco de dados foi desenvolvido para MySQL 8 ou versão compatível.

- **Banco:** `coruja_surf`
- **Script:** `sql/Bancod-de-dados-CORUJA_SURF.sql`

O script deve conter, em ordem organizada:

1. Criação do banco de dados.
2. Criação das tabelas.
3. Definição de PK, FK e demais restrições.
4. Inserção dos dados de teste.
5. Consultas de relacionamento (`JOIN`).
6. Comandos de atualização (`UPDATE`) e exclusão (`DELETE`) demonstrativos.
7. Consultas gerenciais identificadas como G01, G02 etc.
8. Consultas de auditoria identificadas como A01, A02 etc.

Cada consulta gerencial ou de auditoria deve conter comentário explicando seu código, a pergunta respondida e o problema ou regra de negócio relacionada.

### 3.1 Consultas gerenciais

| Código | Pergunta respondida | Problema/KPI relacionado |
|---|---|---|
| G01 | [PREENCHER] | [P1/P2 ou KPI] |
| G02 | [PREENCHER] | [P1/P2 ou KPI] |
| G03 | [PREENCHER] | [P1/P2 ou KPI] |
| G04 | [PREENCHER] | [P1/P2 ou KPI] |

### 3.2 Consultas de auditoria

| Código | Regra verificada | Como a consulta verifica |
|---|---|---|
| A01 | RN01 — [VALIDAR] | [PREENCHER] |
| A02 | RN02 — [VALIDAR] | [PREENCHER] |
| A03 | RN03 — [VALIDAR] | [PREENCHER] |
| A04 | RN04 — [VALIDAR] | [PREENCHER] |

**Atenção:** revisar no script se existe uma consulta de auditoria para cada regra de negócio que precisa ser verificada. A lista acima é apenas uma estrutura inicial.

---

## 4. Dados de teste

Os dados inseridos no banco devem ser fictícios, coerentes com o contexto da Coruja Surf e suficientes para demonstrar as consultas.

| Tabela | Quantidade de registros | Justificativa |
|---|---:|---|
| `cliente` | [PREENCHER] | [PREENCHER] |
| `usuario` | [PREENCHER] | [PREENCHER] |
| `produto` | [PREENCHER] | [PREENCHER] |
| `estoque` | [PREENCHER] | [PREENCHER] |
| `venda` | [PREENCHER] | [PREENCHER] |
| `item_venda` | [PREENCHER] | [PREENCHER] |
| `pedido` | [PREENCHER] | [PREENCHER] |
| `item_pedido` | [PREENCHER] | [PREENCHER] |
| `pagamento` | [PREENCHER] | [PREENCHER] |
| `notificacao` | [PREENCHER] | [PREENCHER] |

Explicar como o volume e a variedade dos dados permitem testar situações diferentes, como estoque baixo, vendas com vários itens, pedidos e pagamentos.

---

## 5. Organização do repositório

Manter os arquivos organizados e atualizar os documentos para que todos representem a mesma versão do banco de dados.

Estrutura sugerida:

```text
Trabalho-Modelagem-de-Banco-de-Dados/
├── README.md
├── diagramas/
│   ├── DER_Coruja_Surf.pdf
│   └── Modelo_Logico_Coruja_Surf.pdf
├── levantamento/
│   ├── levantamento.md
│   └── fotos/
├── docs/
│   └── dicionario_de_dados.md
├── sql/
│   └── Bancod-de-dados-CORUJA_SURF.sql
└── apresentacao/
    └── slides.pdf
```

**Observação:** ajustar os nomes e caminhos conforme os arquivos que realmente estiverem no GitHub. Não deixar links apontando para arquivos inexistentes.

---

## 6. Uso de inteligência artificial

Preencher esta seção de acordo com o uso real de ferramentas de IA pelo grupo. Se uma etapa não utilizou IA, declarar isso.

| Etapa | Ferramenta utilizada | Objetivo | Prompt ou solicitação | Resultado aproveitado e validação |
|---|---|---|---|---|
| [PREENCHER] | [PREENCHER] | [PREENCHER] | [PREENCHER] | [PREENCHER] |

### 6.1 Análise crítica

Descrever quais respostas da IA foram aceitas, modificadas ou rejeitadas, como as informações foram conferidas e quais decisões foram tomadas pelo grupo. A IA não substitui a validação dos requisitos, do modelo e do código SQL.

---

## 7. Apresentação final

A apresentação deverá ter aproximadamente oito minutos e seguir a sequência solicitada:

1. **Contexto e problema:** apresentar a Coruja Surf e os problemas identificados.
2. **Solução proposta:** explicar o sistema e seu escopo.
3. **Modelo lógico:** mostrar as tabelas e os relacionamentos.
4. **Implementação SQL:** demonstrar a estrutura do banco.
5. **Consultas:** executar e explicar consultas gerenciais e de auditoria.
6. **Potencial de BI/IA:** apresentar indicadores e possibilidades de análise.
7. **Benefícios:** explicar como a solução pode ajudar a organização.

**Link dos slides:** [INSERIR LINK DO ARQUIVO OU DA APRESENTAÇÃO]

---

## Checklist antes da entrega

- [ ] Revisar os apontamentos reais da Entrega 1 e preencher a tabela de correções.
- [ ] Confirmar os dados de identificação e contato da organização.
- [ ] Completar os dados da entrevista e anexar evidências autorizadas.
- [ ] Inserir o DER conceitual revisado.
- [ ] Inserir o diagrama lógico atualizado.
- [ ] Atualizar o dicionário de dados para corresponder ao SQL, incluindo `item_pedido`.
- [ ] Conferir nomes de tabelas, colunas, PK e FK em todos os documentos.
- [ ] Revisar normalização e justificativas técnicas.
- [ ] Criar e identificar consultas gerenciais G01 etc.
- [ ] Criar e identificar consultas de auditoria A01 etc.
- [ ] Conferir a quantidade e a variedade dos dados de teste.
- [ ] Documentar o uso real de IA.
- [ ] Inserir os slides finais.
- [ ] Verificar se todos os arquivos estão na branch `main` e se os links funcionam.
