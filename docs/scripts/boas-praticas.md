Olá, pessoal!

Espero que todos estejam bem.

Gostaria de compartilhar com vocês um material importante sobre boas práticas na execução de operações de manipulação de dados. Sabemos que comandos como DELETE, UPDATE e INSERT são essenciais no dia a dia, mas também podem representar riscos significativos caso não sejam realizados com a devida atenção e segurança.

Por isso, compilei esta documentação com orientações, exemplos práticos e recomendações que visam reforçar a integridade, segurança e disponibilidade dos dados, especialmente em ambientes de produção.

Segue abaixo o material:


1. Introdução

As operações DELETE, UPDATE e INSERT  são essenciais para a manipulação de dados em banco, mas também representam riscos significativos se não forem executadas com cuidado.  

Esta documentação aborda boas práticas para garantir a integridade, segurança e disponibilidade dos dados durante essas operações.

 

2. Riscos Associados a DELETE, UPDATE e INSERT



DELETE: Perda irreversível de dados, violação de integridade referencial. 

UPDATE: Sobrescrita acidental de registros, inconsistência de dados.      

INSERT: Inserção de dados inválidos, duplicação indevida. 

                

3. Boas Práticas para Operações Seguras  

      

Antes de executar qualquer operação, é fundamental realizar uma análise detalhada:

Verificar o impacto: Usar SELECT e a criação de um BACKUP antes de DELETE ou UPDATE para confirmar quais registros serão.

 

3.1 DELETE

Exemplo: validar dados que vão ser deletados

SELECT * FROM CONTAS_RECEBER_BAIXAS WHERE IDPLANILHA 1234567

Exemplo: criação de backup da tabela

CREATE TABLE TMP.CONTAS_RECEBER_BAIXAS_BKP250101 LIKE CONTAS_RECEBER_BAIXAS;

INSERT INTO TMP.CONTAS_RECEBER_BAIXAS_BKP250101

SELECT * FROM CONTAS_RECEBER_BAIXAS WHERE IDPLANILHA 1234567

Exemplo: Delete da informação

DELETE FROM CONTAS_RECEBER_BAIXAS WHERE IDPLANILHA 1234567

É de extrema importância a criação de um backup para evitarmos perda irreversível de dados e quebra de integridade.

 

3.2 UPDATE

Exemplo: validar os dados que serão atualizados

SELECT 

        * 

FROM 

        PRODUTO_GRADE 

WHERE 

        TIPOBAIXAMESTRE = 'M' AND 

        IDSUBPRODUTO = 7800

 

Exemplo: Criação de backup para salvar os dados de antes da atualização

CREATE TABLE TMP.PRODUTO_GRADE_BKP250101 LIKE PRODUTO_GRADE;

INSERT INTO TMP.PRODUTO_GRADE_BKP250101

SELECT * FROM PRODUTO_GRADE WHERE TIPOBAIXAMESTRE = 'M' AND IDSUBPRODUTO = 7800

 

Exemplo: Atualizando informação

UPDATE PRODUTO_GRADE

   SET TIPOBAIXAMESTRE = 'I'

 WHERE IDSUBPRODUTO = 7800

É de extrema importância a criação de um backup para evitarmos a sobrescrita acidental de registros, inconsistência de dados.

 

3.3 INSERT



Revisar dados antes de uma inserção, o uso de uma tabela de log é importante para termos a certeza que os dados que vão ser inseridos estão corretos

 Exemplo: insert comum

CREATE TABLE TMP.REGISTROS_LOG290525 LIKE REGISTROS

INSERT INTO TMP.REGISTROS_LOG290525 (id, data, valor) VALUES 

(1, CURRENT_DATE, 100.50)

INSERT INTO REGISTROS (id, data, valor) VALUES 

SELECT * FROM TMP.REGISTROS_LOG290525;

Exemplo: Insert com múltiplos registros 

CREATE TABLE TMP.REGISTROS_LOG290525 LIKE REGISTROS

INSERT INTO TMP.REGISTROS_LOG290525 (id, data, valor) VALUES 

(1, CURRENT DATE, 100.50),

(2, CURRENT DATE, 200.75),

(3, CURRENT DATE, 300.25);

INSERT INTO REGISTROS (id, data, valor) VALUES 

SELECT * FROM TMP.REGISTROS_LOG290525

 

Importante reforçar que os exemplos apresentados acima são meramente ilustrativos.

Em ambientes de produção, as operações são consideravelmente mais complexas e técnicas, e a realização de um backup completo de uma tabela geralmente não é viável, seja por questões de desempenho, volume de dados ou políticas de governança. Por isso, é fundamental sempre realizar backups pontuais e direcionados apenas aos dados que efetivamente serão manipulados.

Além disso, é imprescindível adotar uma postura de extrema cautela ao executar qualquer alteração em ambientes de produção, especialmente considerando que se trata de sistemas críticos e de responsabilidade direta com o cliente.
A ausência desses cuidados se caracteriza como um incidente de segurança, podendo comprometer a integridade dos dados e a confiança no ambiente.

Em caso de dúvidas ou necessidades específicas, é possível acionar o time de script, que está disponível para fornecer apoio técnico e garantir a correta execução das operações.

Time de script. Gabriel Alessandro Doré Adriana Sarturi Otavio Augusto Colares Cutrim Bernardo Jose Battistao Fioreze