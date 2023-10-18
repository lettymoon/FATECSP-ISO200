# Aula 05 - Diretórios e Arquivos

## Resumo

```bash
- Mudando permissões de arquivos e diretórios
    - Formato numérico octal
    - Permissões suid
- Extra: Como compilar códigos no linux
```

## Formato numérico octal

O farmato númerico octal é composto por 3 digitos a partir de um conjunto de oito números onde cada número define um tipo de acesso diferente.

|Comando|Descrição|
|------|------|
|```chmod xxx <arquivo ou diretório>```|Altera as permissões do usuário, grupo ou todos para ler, escrever ou executar o arquivo.|
|```chmod -R xxx <diretório>```|Altera a permissão de todos arquivos e diretórios que estão no diretório recursivamente.|

Exemplo:

                                                 R W X

|Binário|Octal|Permissão|
|------|------|------|
|000|0| Nenhum é ativado|
|001|1| Permissão de execução|
|010|2| Permissão de de gravação|
|011|3| Permissão de gravação e execução|
|100|4| Permissão de leitura|
|101|5| Permissão de leitura e execução|
|110|6| Permissão de de leitura e gravação|
|111|7| Permissão de leitura, gravação e execução|

Outra forma de usar o formato octal é somando cada permissão isolada, exemplo:

* __( 4 )__ permissão de leitura.

* __( 2 )__ permissão de gravação.

* __( 1 )__ permissão de execução.

Para atribuir as permissões de leitura e gravação soma 4+2 = 6, ``` chmod 6 <arquivo>``` 

![explicação](image-3.png)

Cada um dos 3 digitos se refere ao usuário, grupo e outros, em sequência. Com isso se usarmos os digitos 777 vamos atribuir todas as permissões ao dono, grupo e outros.

Exemplo:

Se quisermos dar permissão de leitura e gravação ao arqvivo arq.txt é só usarmos o comando:

```bash
chmod 6 arq.txt
```

Números não utilizados são consideramos como 0, então ``` chmod 6 arq.txt ``` é igual a ``` chmod 006 ```, isso quer dizer que as permissões foram atribuídas ao outros, assim como foram tiradas todas as permissões de usuário e grupos.

![chmod 6](image-6.png)

Para atribuir as mesmas permissões ao usuário terar que utilizar os zeros após o número 6, ``` chmod 600 arqcomp ```.

![chmod 600](image-7.png)

### Exemplos

|Comando|Descrição|
|------|------|
|```chmod 111 <arquivo>```|Todos podem executar o arquivo.|
|```chmod 222 <arquivo>```|Todos podem escrever no arquivo.|
|```chmod 700 <arquivo>```|Somente o dono do arquivo tem todas as permissões.|
|```chmod 600 <arquivo>```|O dono do arquivo pode ler e escrever.|
|```chmod 777 <arquivo>```|Todas as permissões para todos.|

## Permissão SUID, SGID e Sticky bit no formato octal

No formato octal podemos utilizar o quarto digito, na frente dos 3 digitos, para informar uma permissão especial.

Como já foi explicado na aula anterior sobre as permissões especiais aqui só vou ensinar como atribuir uma permissão especial no formato octal.

Funciona da mesma forma que as permissões r, w e x, a sequência para as permissões especiais é suid, sgid e sticky.

|Binário|Octal|Permissão|
|------|------|------|
|000|0| Nenhum é ativado|
|001|1| Ativa apenas o sticky|
|010|2| Ativa apenas o sgid|
|011|3| Ativa o sgid e sticky|
|100|4| Ativa apenas o suid|
|101|5| Ativa apenas o suid e sticky|
|110|6| Ativa o suid e sgid|
|111|7| Ativa todos, suid, sgid e sticky|

Agora é só colocar mais um digito na frente para atribuir uma permissão especial, ``` chmod 4765 arq.txt ```, vai atribuir as permissões de suid ao arquivo, além das permissões leitura, gravação e execução ao dono, leitura e gravação ao grupo e leitura e execução ao outros.

## Permissão suid

