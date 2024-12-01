
# Estrutura e Funcionalidade do Banco de Dados - Projeto Fortes

Este documento detalha a estrutura e as funcionalidades de um banco de dados relacional projetado para o gerenciamento de donatários, funcionários, editais, vistorias, relatórios, reuniões e endereços. 

---

## Estrutura do Banco de Dados

### 1. Banco de Dados
```sql
CREATE DATABASE projeto_fortes;
USE projeto_fortes;
```
- **Descrição:** Cria o banco de dados `projeto_fortes` e o define como o banco de trabalho ativo.

---

### 2. Tabelas do Banco de Dados

#### 2.1. Tabela: `donatarios`
**Descrição:** Armazena informações sobre os donatários.
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
- **Colunas:**
  - `dona_id`: Identificador único (*Primary Key*).
  - `dona_cnpj`: CNPJ do donatário.
  - `dona_edital`: Edital associado.
  - `dona_pessoa_cont`: Pessoa de contato.
  - `dona_nome_representante`: Nome do representante legal.
  - `dona_cpf_representante`: CPF do representante legal.

#### 2.2. Tabela: `funcionarios`
**Descrição:** Armazena informações sobre os funcionários.
```sql
CREATE TABLE IF NOT EXISTS funcionarios(
    func_id INT PRIMARY KEY,
    func_nome VARCHAR(100) NOT NULL,
    func_email VARCHAR(100) NOT NULL,
    func_cargo VARCHAR(30) NOT NULL,
    func_data_nasc DATE NOT NULL,
    func_rg VARCHAR(25)
);
```
- **Colunas:**
  - `func_id`: Identificador único (*Primary Key*).
  - `func_nome`: Nome do funcionário.
  - `func_email`: E-mail do funcionário.
  - `func_cargo`: Cargo do funcionário.
  - `func_data_nasc`: Data de nascimento.
  - `func_rg`: RG do funcionário.

#### 2.3. Tabela: `edital`
**Descrição:** Contém informações sobre editais e suas relações.
```sql
CREATE TABLE IF NOT EXISTS edital(
    ed_id INT PRIMARY KEY,
    ed_inicio DATE NOT NULL,
    ed_fim DATE NOT NULL,
    ed_objetivo TEXT NOT NULL,
    ed_tematica VARCHAR(50) NOT NULL,
    ed_metodologia TEXT NOT NULL,
    ed_metas TEXT NOT NULL,
    ed_orcamentos_invest DECIMAL(10,2) NOT NULL,
    ed_dona_id INT NOT NULL,
    ed_func_id INT NOT NULL,
    CONSTRAINT ed_dona_id_FK FOREIGN KEY (ed_dona_id) REFERENCES donatarios (dona_id),
    CONSTRAINT ed_func_id_FK FOREIGN KEY (ed_func_id) REFERENCES funcionarios (func_id)
);
```
- **Relacionamentos:**
  - `ed_dona_id` referencia `donatarios(dona_id)`.
  - `ed_func_id` referencia `funcionarios(func_id)`.

#### 2.4. Tabela: `vistorias`
**Descrição:** Armazena informações sobre vistorias realizadas.
```sql
CREATE TABLE IF NOT EXISTS vistorias(
    vist_id INT PRIMARY KEY,
    vist_valor_pend DECIMAL(10,2),
    vist_doc_pend TEXT,
    vist_doc TEXT NOT NULL,
    vist_valor_pago DECIMAL(10,2) NOT NULL,
    vist_dona_id INT NOT NULL,
    vist_func_id INT NOT NULL,
    CONSTRAINT vist_dona_idFK FOREIGN KEY (vist_dona_id) REFERENCES donatarios (dona_id),
    CONSTRAINT vist_func_id_FK FOREIGN KEY (vist_func_id) REFERENCES funcionarios (func_id)
);
```
- **Relacionamentos:**
  - `vist_dona_id` referencia `donatarios(dona_id)`.
  - `vist_func_id` referencia `funcionarios(func_id)`.

#### 2.5. Tabela: `relatorios`
**Descrição:** Contém relatórios gerados a partir das vistorias.
```sql
CREATE TABLE IF NOT EXISTS relatiorios(
    rela_id INT PRIMARY KEY,
    rela_data DATE NOT NULL,
    rela_gastos DECIMAL(10,2) NOT NULL,
    rela_vist_id INT NOT NULL,
    CONSTRAINT rela_vist_id_FK FOREIGN KEY (rela_vist_id) REFERENCES vistorias (vist_id)
);
```

#### 2.6. Tabela: `reunioes`
**Descrição:** Registra informações sobre reuniões associadas a vistorias.
```sql
CREATE TABLE IF NOT EXISTS reunioes(
    reun_id INT PRIMARY KEY,
    reun_data DATE NOT NULL,
    reun_vist_id INT NOT NULL,
    CONSTRAINT reun_vist_id_FK FOREIGN KEY (reun_vist_id) REFERENCES vistorias (vist_id)
);
```

#### 2.7. Tabela: `endereço`
**Descrição:** Contém informações sobre endereços associados a donatários e funcionários.
```sql
CREATE TABLE IF NOT EXISTS endereço(
    ende_num_rua INT,
    ende_rua VARCHAR(100) NOT NULL,
    ende_bairro VARCHAR(100) NOT NULL,
    ende_cidade VARCHAR(50) NOT NULL,
    ende_uf CHAR(2) NOT NULL,
    ende_pais VARCHAR(50) NOT NULL,
    ende_cep VARCHAR(10) NOT NULL,
    ende_dona_id INT NOT NULL,
    ende_func_id INT NOT NULL,
    CONSTRAINT ende_dona_id_FK FOREIGN KEY (ende_dona_id) REFERENCES donatarios (dona_id),
    CONSTRAINT ende_func_id_FK FOREIGN KEY (ende_func_id) REFERENCES funcionarios (func_id)
);
```

---

## Funcionalidades do Banco de Dados

1. **Cadastro e Gerenciamento de Donatários:**
   - Permite registrar dados legais e administrativos de donatários.

2. **Gerenciamento de Funcionários:**
   - Inclui informações pessoais e profissionais de cada funcionário.

3. **Gestão de Editais:**
   - Relaciona editais a donatários e responsáveis (funcionários).

4. **Monitoramento de Vistorias:**
   - Registra valores pendentes, documentação e pagamentos relacionados às vistorias.

5. **Criação de Relatórios:**
   - Gera relatórios baseados nas vistorias realizadas.

6. **Organização de Reuniões:**
   - Controla reuniões associadas às vistorias.

7. **Gestão de Endereços:**
   - Mantém dados de localização de donatários e funcionários.

---

### Observação Final
Este banco de dados foi projetado para oferecer um sistema robusto e extensível, capaz de gerenciar diversas operações relacionadas a projetos, desde o cadastro de pessoas até o controle de reuniões e relatórios.

