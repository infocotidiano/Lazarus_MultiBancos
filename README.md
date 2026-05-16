# Lazarus MultiBancos
## Teste de Conexão com MariaDB/MySQL e PostgreSQL

![Daniel de Morais - Infocotidiano](./tela.PNG)

## Sobre o projeto
Aplicação em Lazarus (compatível com Delphi em lógica) para teste de conexão com bancos de dados MariaDB/MySQL e PostgreSQL. O objetivo é permitir que o usuário selecione o banco e o servidor para conectar, além de executar operações básicas de inclusão e exclusão de registros.

## Tecnologias utilizadas
- Lazarus / Free Pascal
- MariaDB 10.5 / MySQL
- PostgreSQL 13.x

## Banco de dados suportados
- MariaDB / MySQL
- PostgreSQL

## Estrutura de tabela necessária
A aplicação utiliza a tabela `cliente` com o seguinte esquema:

- `codigo` : chave primária numérica, auto incremento
- `nome` : texto com até 100 caracteres
- `telefone` : texto com até 15 caracteres

## Criação da tabela em MariaDB / MySQL
```sql
CREATE TABLE cliente (
  codigo INT(11) NOT NULL AUTO_INCREMENT,
  nome VARCHAR(100) DEFAULT NULL,
  telefone VARCHAR(15) DEFAULT NULL,
  PRIMARY KEY (codigo)
);
```

## Criação da tabela em PostgreSQL
```sql
CREATE TABLE cliente (
  codigo SERIAL PRIMARY KEY,
  nome VARCHAR(100),
  telefone VARCHAR(15)
);
```

## Observações
- Em PostgreSQL, o tipo `SERIAL` já cria a sequência e define `codigo` como chave primária.
- Para MariaDB/MySQL, o `AUTO_INCREMENT` garante a geração automática dos valores de `codigo`.
- Use sempre o mesmo nome de tabela e campos para manter a compatibilidade com a aplicação.
- A arquitetura dos drivers/DLLs de banco deve corresponder à arquitetura do executável Lazarus.
  - Se o Lazarus estiver compilado como 32 bits, use DLLs de banco de dados 32 bits.
  - Se o Lazarus estiver compilado como 64 bits, use DLLs de banco de dados 64 bits.
  - A bitness do Windows não é o fator decisivo; o importante é como o `.exe` foi criado.

## Configuração
1. Crie o banco de dados no servidor desejado.
2. Execute o script SQL apropriado para sua plataforma.
3. Configure a conexão no aplicativo Lazarus apontando para o servidor, usuário, senha e banco corretos.

## Autor
Daniel de Morais

### Link do vídeo demonstrativo
https://youtu.be/SqwgCmuKYLA?si=WlJzMmMy6xtn1Buh

