# 🪑 Projeto Madeira Verde – Modelagem de Software

## 🌟 Introdução
Este projeto faz parte da **A3 da disciplina de Modelagem de Software** e consiste na criação de um modelo de dados completo para a fábrica de móveis fictícia **Madeira Verde**.  
O objetivo foi aplicar conceitos de **modelagem de dados**, como **entidades, atributos, relacionamentos, cardinalidades e normalização**, representando graficamente a estrutura do banco por meio do **Modelo Entidade-Relacionamento (MER)** e implementando o **Diagrama Entidade-Relacionamento (DER)**.

---

## 🎯 Objetivo
Desenvolver um **modelo relacional em conformidade com a 3ª Forma Normal (3FN)**, garantindo:

- Organização eficiente dos dados  
- Ausência de redundância  
- Integridade referencial  

---

## 🛠 Desenvolvimento
A modelagem de dados foi baseada no cenário da fábrica fictícia Madeira Verde, especializada na fabricação de móveis sob encomenda.

### Etapas do projeto:
- 🔹 Identificação das **13 entidades principais**: `CLIENTE`, `PRODUTO`, `COMPONENTE`, `EMPREGADO`, `ENCOMENDA` e outras.  
- 🔹 Criação de **entidades associativas** para relacionamentos N:N: `PRODUTO_COMPONENTE`, `FORNECEDOR_COMPONENTE`, `PRODUTO_EMPREGADO`, `PRODUTO_ENCOMENDADO`.  
- 🔹 Aplicação da **3ª Forma Normal (3FN)** para evitar redundâncias.  
- 🔹 Elaboração do **MER e DER** com cardinalidades usando **DBDesigner**.  
- 🔹 Implementação no **SQL Server** com **script SQL** para criação das tabelas e relacionamentos.

---

## 🏗 Estrutura do Banco de Dados
O banco contém tabelas principais:

- `CLIENTE` 👤  
- `PRODUTO` 🛋️  
- `COMPONENTE` ⚙️  
- `EMPREGADO_MAO_OBRA` 👷‍♂️  
- `ENCOMENDA` 📦  
- `FORNECEDOR` 🏭  
- `MAQUINA` 🏭  
- `ESTOQUE` 📦  
- `COMPRA` 💳  
- `VENDE` 💰  

Além das tabelas associativas e de suporte (`PRODUTO_COMPONENTE`, `FORNECEDOR_COMPONENTE`, `ENDERECO_TIPO`, `COMPONENTE_TIPO`) garantindo **integridade e eficiência** do sistema.

> O script completo está disponível no arquivo `script.sql`.

---

## ✅ Conclusão
Este projeto permitiu aplicar de forma prática conceitos de **entidades, atributos, relacionamentos e normalização**, enfrentando desafios como:

- 🔹 Identificação correta das cardinalidades  
- 🔹 Separação de entidades associativas N:N  
- 🔹 Implementação da 3ª Forma Normal para integridade dos dados  

O uso do **DBDesigner** facilitou a visualização e validação do DER. Além de atender aos requisitos acadêmicos, o projeto proporcionou experiência em **análise de problemas, tomada de decisões e documentação estruturada**.

---

## 💻 Tecnologias Utilizadas
- SQL Server 🖥️  
- DBDesigner 📊  
- Modelagem de dados (MER/DER) 📐  
- Normalização até 3FN 🔄  

---

## 📝 Script SQL
O banco e todas as tabelas foram criados a partir do comando:

```sql
CREATE DATABASE WELLINGTONA3;
USE WELLINGTONA3;
-- [Tabelas, constraints e relacionamentos conforme script enviado]
