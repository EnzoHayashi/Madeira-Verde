# Madeira Verde – Modelagem de Banco de Dados

![SQL Server](https://img.shields.io/badge/SQL_Server-T--SQL-red)
![Normalização](https://img.shields.io/badge/Normaliza%C3%A7%C3%A3o-3FN-blue)
![DBDesigner](https://img.shields.io/badge/Modelagem-DBDesigner-green)

Modelo de dados relacional para a **Madeira Verde**, fábrica fictícia de móveis sob encomenda, com diagramas MER/DER e script de criação em SQL Server.

## Objetivo e contexto

Projeto da avaliação A3 da disciplina de **Modelagem de Software** (Análise e Desenvolvimento de Sistemas, UAM). O objetivo foi aplicar na prática os conceitos de modelagem de dados (entidades, atributos, relacionamentos, cardinalidades e normalização) e construir um modelo relacional na **3ª Forma Normal (3FN)**, buscando:

- organização eficiente dos dados;
- ausência de redundância;
- integridade referencial.

## Escopo do modelo

O cenário cobre o ciclo de produção e venda da fábrica. O modelo possui **13 entidades principais** e, somando tabelas associativas e de apoio, o script cria **22 tabelas**, agrupadas por assunto:

| Domínio | Tabelas |
|---|---|
| Clientes e endereços | `CLIENTE`, `ENDERECO`, `ENDERECO_TIPO`, `CIDADE`, `ESTADO` |
| Produtos e componentes | `PRODUTO`, `COMPONENTE`, `COMPONENTE_TIPO`, `PRODUTO_COMPONENTE` |
| Fornecedores | `FORNECEDOR`, `FORNECEDOR_TIPO`, `COMPONENTE_FORNECEDOR` |
| Pedidos e vendas | `ENCOMENDA`, `ENCOMENDA_PRODUTO`, `VENDE`, `COMPRA`, `COMPRA_TIPO` |
| Produção e estoque | `MAQUINA`, `MANUTENCAO`, `ESTOQUE`, `EMPREGADO_MAO_OBRA` |
| Empresa | `MADEIRA_VERDE` |

## Decisões de modelagem

- **Tabelas associativas para relacionamentos N:N.** `PRODUTO_COMPONENTE`, `COMPONENTE_FORNECEDOR` e `ENCOMENDA_PRODUTO` resolvem as relações muitos-para-muitos e guardam atributos do próprio relacionamento (por exemplo, quantidade necessária e unidade de medida em `PRODUTO_COMPONENTE`; prazo, quantidade e preço unitário em `ENCOMENDA_PRODUTO`).
- **Tabelas de domínio (tipo).** `ENDERECO_TIPO`, `FORNECEDOR_TIPO`, `COMPONENTE_TIPO` e `COMPRA_TIPO` evitam repetir descrições em texto nas tabelas principais, um dos pontos da 3FN.
- **Endereço normalizado em `ESTADO` → `CIDADE` → `ENDERECO`.**
- **Chaves primárias artificiais (`IDENTITY`) e restrições `UNIQUE`** em identificadores de negócio, como CNPJ, código de produto, código de componente e número da encomenda.
- **Integridade referencial** declarada por `FOREIGN KEY` em `ALTER TABLE`, após a criação das tabelas, o que evita problemas de ordem de criação em relacionamentos circulares.
- **Convenção de nomes** com prefixo por tabela (por exemplo, `CLI_` para `CLIENTE`, `PRO_` para `PRODUTO`).

## Tecnologias

- SQL Server (T-SQL)
- DBDesigner (MER e DER)
- Normalização até a 3FN

## Estrutura do repositório

```
Madeira-Verde/
├── madeira.sql   # script de criação do banco, tabelas, chaves e relacionamentos
└── README.md
```

## Como executar

**Pré-requisito:** instância do SQL Server (local ou em contêiner) e SSMS, Azure Data Studio ou `sqlcmd`.

Pelo SSMS ou Azure Data Studio: abrir o arquivo `madeira.sql` e executar.

Pela linha de comando:

```bash
sqlcmd -S localhost -i madeira.sql
```

O script cria o banco `WELLINGTONA3` e, em seguida, todas as tabelas e relacionamentos. O nome do banco pode ser alterado nas duas primeiras linhas do script.

## Diagramas

<!-- Adicionar as imagens exportadas do DBDesigner em docs/ e descomentar:
![MER](docs/mer.png)
![DER](docs/der.png) -->

## Desafios e aprendizados

- Identificação correta das cardinalidades entre as entidades.
- Separação de entidades associativas nos relacionamentos N:N.
- Aplicação da 3ª Forma Normal para garantir integridade e evitar redundância.
- Uso do DBDesigner para visualizar e validar o DER antes da implementação em SQL.

## Melhorias futuras

- Testar o script em uma instância limpa do SQL Server e revisar a sintaxe das instruções `CREATE TABLE` e das chaves estrangeiras.
- Revisar restrições `UNIQUE` que limitam a cardinalidade dos dados (por exemplo, a unicidade da sigla do estado em `ENDERECO`).
- Padronizar nomes e tipos de colunas (por exemplo, valores monetários como `DECIMAL` em vez de `INT`, e telefones como `VARCHAR`).
- Incluir dados de exemplo (`INSERT`) e consultas que demonstrem o modelo em uso (relatórios de encomendas por cliente, consumo de componentes por produto).
- Versionar os diagramas MER/DER junto ao script.
