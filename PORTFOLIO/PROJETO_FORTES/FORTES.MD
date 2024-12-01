
# Projeto Fortes - Definição do Banco de Dados

Este documento contém a descrição completa do banco de dados definido no arquivo SQL `PROJETO_FORTES_DDL.sql`. Ele especifica as tabelas, colunas e relações que compõem a estrutura do banco de dados.

---

## Estrutura do Banco de Dados

### 1. Criação do Banco de Dados
```sql
CREATE DATABASE projeto_fortes;
USE projeto_fortes;
```
- **Objetivo:** Criar o banco de dados chamado `projeto_fortes` e definir que todas as operações subsequentes ocorrerão neste banco.
- **Nota:** Caso o banco de dados já exista, a execução pode gerar um erro. Certifique-se de verificar sua existência antes de criar.

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
- **Descrição:** A tabela `donatarios` armazena informações sobre os donatários associados ao sistema.
- **Colunas:**
  - `dona_id`: Inteiro que serve como chave primária da tabela. Cada donatário possui um identificador único.
  - `dona_cnpj`: Campo de texto (até 20 caracteres) que armazena o CNPJ do donatário.
  - `dona_edital`: Texto (até 35 caracteres) representando o edital associado ao donatário.
  - `dona_pessoa_cont`: Nome da pessoa de contato principal do donatário (até 35 caracteres).
  - `dona_nome_representante`: Nome completo do representante legal do donatário (até 100 caracteres).
  - `dona_cpf_representante`: CPF do representante legal (até 20 caracteres).
- **Regras:** Nenhuma das colunas permite valores nulos.

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
- **Descrição:** A tabela `funcionarios` armazena dados dos funcionários do sistema.
- **Colunas:**
  - `func_id`: Identificador único do funcionário (*Primary Key*).
  - `func_nome`: Nome completo do funcionário (até 100 caracteres).
  - `func_email`: Endereço de e-mail do funcionário (até 100 caracteres).
  - `func_cargo`: Cargo ou função do funcionário na organização (até 30 caracteres).
  - `func_data_nasc`: Data de nascimento do funcionário no formato de data.
- **Regras:** Todas as colunas são obrigatórias, garantindo que nenhum registro seja inserido sem informações completas.

---

### Considerações Gerais
- **Integridade dos Dados:** O uso de chaves primárias em ambas as tabelas assegura a integridade e unicidade dos registros.
- **Extensibilidade:** Novas tabelas ou colunas podem ser adicionadas para expandir a funcionalidade do banco.
- **Validações:** Os tipos de dados foram escolhidos para minimizar inconsistências. Campos como `CNPJ` e `CPF` são armazenados como texto para preservar formatações especiais.

---

## Instruções para Uso
1. **Requisitos:** É necessário um servidor MySQL para executar o script.
2. **Execução do Script:**
   - Abra seu cliente MySQL ou ferramenta de gerenciamento de banco de dados.
   - Execute o conteúdo do arquivo `PROJETO_FORTES_DDL.sql`.
3. **Verificação:**
   - Após a execução, confirme se as tabelas `donatarios` e `funcionarios` foram criadas corretamente.
   - Utilize o comando `SHOW TABLES;` para listar as tabelas existentes no banco.

---

### Autor e Documentação
- Este script e documentação foram gerados automaticamente e representam um exemplo básico de estruturação de banco de dados.

Se houver dúvidas ou melhorias, entre em contato com o responsável pelo projeto.
