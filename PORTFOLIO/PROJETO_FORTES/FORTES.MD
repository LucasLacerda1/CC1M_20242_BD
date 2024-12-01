# Estrutura e Funcionalidades do Banco de Dados - Projeto Fortes

Este documento detalha a estrutura e funcionalidades do banco de dados definido pelo script SQL, incluindo tabelas, colunas e suas aplicações práticas.

---

## Estrutura Geral

O banco de dados é composto por duas tabelas principais: `donatarios` e `funcionarios`. Cada tabela foi projetada para armazenar informações específicas e possui uma chave primária para garantir a integridade dos dados.

---

### 1. Tabela: `donatarios`
**Descrição:** A tabela `donatarios` armazena dados de pessoas ou entidades que atuam como donatários.

#### Estrutura:
| Coluna                   | Tipo de Dados     | Restrições     | Descrição                                   |
|--------------------------|-------------------|----------------|-------------------------------------------|
| `dona_id`                | INT               | PRIMARY KEY    | Identificador único para o donatário.     |
| `dona_cnpj`              | VARCHAR(20)       | NOT NULL       | CNPJ da entidade donatária.               |
| `dona_edital`            | VARCHAR(35)       | NOT NULL       | Edital associado ao donatário.            |
| `dona_pessoa_cont`       | VARCHAR(35)       | NOT NULL       | Pessoa de contato principal.              |
| `dona_nome_representante`| VARCHAR(100)      | NOT NULL       | Nome do representante legal.              |
| `dona_cpf_representante` | VARCHAR(20)       | NOT NULL       | CPF do representante legal.               |

#### Funcionalidades:
1. **Armazenamento de Dados Legais:**
   - Cadastra CNPJ, CPF e outras informações legais de donatários.
2. **Gestão de Editais:**
   - Relaciona os donatários aos editais específicos em que estão associados.
3. **Consulta Rápida:**
   - Permite localizar donatários rapidamente usando o `dona_id`.

---

### 2. Tabela: `funcionarios`
**Descrição:** A tabela `funcionarios` armazena informações de funcionários associados ao sistema.

#### Estrutura:
| Coluna          | Tipo de Dados  | Restrições     | Descrição                                 |
|-----------------|----------------|----------------|-------------------------------------------|
| `func_id`       | INT            | PRIMARY KEY    | Identificador único para o funcionário.  |
| `func_nome`     | VARCHAR(100)   | NOT NULL       | Nome completo do funcionário.            |
| `func_email`    | VARCHAR(100)   | NOT NULL       | E-mail de contato do funcionário.        |
| `func_cargo`    | VARCHAR(30)    | NOT NULL       | Cargo ou função do funcionário.          |
| `func_data_nasc`| DATE           | NOT NULL       | Data de nascimento do funcionário.       |

#### Funcionalidades:
1. **Gestão de Recursos Humanos:**
   - Registra dados pessoais e profissionais dos funcionários.
2. **Validação de Registros:**
   - Garantia de que todos os campos obrigatórios sejam preenchidos.
3. **Consulta por Cargo:**
   - Possibilita a filtragem de funcionários com base em seu cargo ou data de nascimento.

---

## Funcionalidades Gerais do Banco de Dados
1. **Cadastro de Informações:**
   - Permite inserir dados de donatários e funcionários de forma segura e estruturada.
2. **Consulta e Relatórios:**
   - Facilita consultas para gerar relatórios administrativos ou jurídicos.
3. **Expansibilidade:**
   - Projetado para aceitar novas tabelas e relações sem impactar o funcionamento atual.
4. **Integridade dos Dados:**
   - Chaves primárias e restrições `NOT NULL` garantem consistência.

---

### Considerações Finais
Esta estrutura oferece um banco de dados simples e funcional para gerenciar informações de donatários e funcionários. Ele pode ser facilmente adaptado e expandido para atender a requisitos adicionais, como vinculação entre as tabelas ou integração com sistemas externos.

