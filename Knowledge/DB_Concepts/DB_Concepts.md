# Base de dados

[Back](../Knowledge.md)

## 5 Passos

1. Todas as entidades tornam-se tabelas
   - Atributo chave -> chave primaria
   - Atributo composto -> decompor passando a ser os campos de atributos decompostos
   - atributo multiplo -> passo5 -> criação de nova tabela

2. 1-N N-1
   - criar chave estrangeira no lado N apartir da chave primaria do 1
     - participação total -> NN - Not Null

3. 1-1
   - criação de chave estrangeira no lado onde haverá mais registos. o campo criado é chave unica (UK), e se for participação total Not Null (NN)

4. M-N
   - é criada uma tabela com 2 chaves estrangeiras, cada respondente a primaria da tabela de origem
   - o conjunto das chaves estrangeiras, forma uma chave primária composta
   - (UK)

5. Atributo multivalor
   - é criada uma tabela com chave estrangeira correspondente a chave primaria da tabela de origem, acrescido do atributo multivalor. Os dois campos criados são uma chave primaria para a nova tabela.

## Formulas normais

1. Valores atómicos
   - evitar colunas/atributos/campos repetidos

2. Dependencias
   - identificar chaves primárias  
   - identificar dependentes  
   - identificar relações  
   - separação em tabelas  

3. Decompor
   - Verificar se os atributos não chaves de cada tabela têm uma relação entre si
   - se sim decompor
     - >ex: codigo postal e localidade podem estar relacionadas numa tabela a parte
   - Evitar campos calculados
