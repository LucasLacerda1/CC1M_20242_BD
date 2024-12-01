# Definição do Banco de Dados - Projeto Fortes

Este arquivo contém a definição e criação de um banco de dados utilizando SQL. Abaixo estão os principais detalhes do script.

## Estrutura do Banco de Dados

### 1. Criação do Banco de Dados
```sql
CREATE DATABASE teste_davi;
USE teste_davi;
```
- **Banco de Dados:** `teste_davi`.

---

### 2. Tabela: `donatarios`
```sql
CREATE TABLE IF NOT EXISTS donatarios(
    dona_id INT PRIMARY KEY,
    dona_cnpj VARCHAR(20) NOT NULL,
    dona_edital VARCHAR(35) NOT NULL,
    dona_pessoa_cont VARCHAR(35) NOT NULL,
    dona_nome_representante VARCHAR(100) NOT NULL,
    dona_cpf_representante VARCHAR(20) NOT NULL
);
```
- **Descrição:** Armazena informações sobre os donatários.
- **Colunas:**
  - `dona_id`: Identificador único (*Primary Key*).
  - `dona_cnpj`: CNPJ do donatário (obrigatório).
  - `dona_edital`: Edital associado (obrigatório).
  - `dona_pessoa_cont`: Nome da pessoa de contato (obrigatório).
  - `dona_nome_representante`: Nome do representante (obrigatório).
  - `dona_cpf_representante`: CPF do representante (obrigatório).

---

### 3. Tabela: `funcionarios`
```sql
CREATE TABLE IF NOT EXISTS funcionarios(
    func_id INT PRIMARY KEY,
    func_nome VARCHAR(100) NOT NULL,
    func_email VARCHAR(100) NOT NULL,
    func_cargo VARCHAR(30) NOT NULL,
    func_data_nasc DATE NOT NULL
);
```
- **Descrição:** Armazena informações sobre os funcionários.
- **Colunas:**
  - `func_id`: Identificador único (*Primary Key*).
  - `func_nome`: Nome do funcionário (obrigatório).
  - `func_email`: E-mail do funcionário (obrigatório).
  - `func_cargo`: Cargo do funcionário (obrigatório).
  - `func_data_nasc`: Data de nascimento do funcionário (obrigatório).

---

## Uso
1. Execute o script em um banco de dados MySQL para criar as tabelas e o banco de dados.
2. Certifique-se de que possui permissões para criar bancos de dados.

---

### Autor
Gerado automaticamente a partir do script `PROJETO_FORTES_DDL.sql`.
