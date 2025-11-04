# 🧠 Modelagem do Sistema Pravi

## Casos de Uso

| Ator | Caso de Uso | Descrição |
|------|-------------|-----------|
| Usuário | Cadastrar-se | Criar conta |
| Usuário | Logar | Acessar conta |
| Usuário | Cadastrar alimento | Adicionar alimento |
| Usuário | Editar/excluir alimento | Atualizar/remover alimento |
| Usuário | Receber notificação | Alerta por e-mail |
| Usuário | Consultar orientações | Visualizar dicas de conservação |

## Diagrama de Classes (Textual)

**Usuário**  
- Atributos: id, nome, e-mail, dataNascimento, nomeFamilia  
- Métodos: cadastrar(), autenticar()

**Alimento**  
- Atributos: id, nome, validade, compra, categoria, tipo, idUsuario  
- Métodos: cadastrar(), editar(), excluir()

**Família**  
- Atributos: idFamilia, nomeFamilia

## Modelo Conceitual

- Usuario → Alimento (1:N)  
- Família → Usuario (1:N)

## Modelo Lógico

### Tabela: Usuario

| Campo | Tipo | Restrição |
|-------|------|-----------|
| id_usuario | INT | PK, AUTO_INCREMENT |
| nome | VARCHAR(100) | NOT NULL |
| email | VARCHAR(100) | UNIQUE, NOT NULL |
| data_nascimento | DATE | NOT NULL |
| nome_familia | VARCHAR(100) | NULL |
| id_familia | INT | FK → Familia(id_familia) |
| senha | VARCHAR(255) | NOT NULL |

### Tabela: Alimento

| Campo | Tipo | Restrição |
|-------|------|-----------|
| id_alimento | INT | PK, AUTO_INCREMENT |
| nome | VARCHAR(100) | NOT NULL |
| data_validade | DATE | NOT NULL |
| categoria | VARCHAR(100) | NOT NULL |
| tipo | VARCHAR(50) | NOT NULL |
| id_usuario | INT | FK → Usuario(id_usuario) |
| data_compra | DATE | NOT NULL |
| quantidade | INT | NOT NULL |

### Tabela: Familia

| Campo | Tipo | Restrição |
|-------|------|-----------|
| id_familia | INT | PK, AUTO_INCREMENT |
| id_usuario | INT | FK → Usuario(id_usuario) |
