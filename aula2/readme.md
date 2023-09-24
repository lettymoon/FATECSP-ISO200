# Aula 02 - Edição de textos e Interpretadores de comandos mais utilizados

Resumo:

```bash
    - Editor Vim 
    - Linhas de comandos no vim
    - extra: Editor nano
```

## 5) Edição de textos

<img height=60 src="https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vim/vim-original.svg" />

O editor de texto mais utilizado em um sistema linux é o **vim**.

Para verificar se o vim está instalado abra o terminal e digite "vim".

Se aparecer uma tela assim é porque está.

![vim-open](image-1.png)

Caso contrario, digite:

Debian/Ubuntu: (Distribuição utilizada pelo professor)

```shell
sudo apt install vim
```

Arco:

```shell
sudo pacman -S vim
```

Fedora:

```shell
sudo dnf install vim-enhanced
```

### Modos

O vim é baseado em 2 modos:

- > Comando: Esse é o modo onde são executados os comandos, e também é o modo padrão onde o vim é iniciado.
- > Insert/Replace: Modo onde você insere, ou seja, escreve o texto.

Como o vim é inicializado no modo comando, para ir para o modo insert aperte a tecla **i**, e comece a digitar o seu texto.

Para voltar ao modo comando aperte **Esc**.

No vim não se utiliza o mouse, então se quiser navegar pelo seu código ou texto utilize as teclas **h**, **l**, **k** e **j**. Para saltar para o inicio de uma palavra utilize **w** e para o final da palavra utilize **e**. Para ir para uma nova linha **o**.

Lembre-se que todos esses comandos tem que ser utilizados no modo **comando** e não no modo **insert**.

No modo **comando** é onde também salvamos e sairmos do vim. Utilize **:w** (: antes de qualquer comando para salvar e sair do vim) para salvar o arquivo, **:wq** para salvar e sair do arquivo, **:q** para sair sem salvar do arquivo, **:q!** força sair do arquivo sem salvar caso ocorra algum erro, **:wqa** também é usado para salvar e sair do vim, mas diferente do **:wq** ele salva todos os arquivos do vim, a significa all.

Outros comandos da apostila do professor são, **:shell** que sai temporariamente do vim para o terminal sem necessariamente fechar o vim, você pode retornar ao vim com o comando **ctrl+d**, comando muito util para caso precise utilizar o terminal sem precisar fechar o arquivo ou abrir outro terminal. Outro comando mostrado na apostila é o **:X** (em maiúsculo) que é usado para critografar o arquivo. Conversando com o professor a criptografia utilizada no Debian é o "blowfish2". Para saber o tipo de critografia está sendo utilizada digite o comando, no modo comando(esc):

```shell
:set cryptmethod?
```

Ainda no modo comando, para **mover linhas** em uma posição específica no texto, pode ta utilizando o comando:

```shell
:intervalo mov posição
:1,5 mov 10
irá mover as linhas de 1 a 5 para a linha 10
```

Exemplo:

![vim-mov](image-4.png)

![vim-mov](image-5.png)

![vim-mov](image-6.png)

#### Para copiar linhas

```shell
yy - seleciona a linha do cursor
p - cola na linha abaixo do cursor
```

O **yy** vai selecionar a linha onde está o cursor e o **p** vai colar a linha selecionada abaixo do cursor.

Exemplo:

![vim-yy](image-2.png)

No exemplo acima foi utilizado 13 linhas, o cursor está na linha 5, no modo comando foi utilizado o **yy**, na linha 10 será utilizado o comando **p**.

![vim-p](image-3.png)

Já o comando **y2** seleciona a linha atual do cursor e mais duas linhas abaixo, o **y3** seleciona a linha atual do cursor e mais três linhas abaixo e assim sucessivamente. Depois é só usar o comando **p**.

#### Apagar linhas

Fuciona parecido com o **yy**, o comando **dd** vai apagar a linha na posição do cursor, o **d3** apaga a linha do cursor e mais três abaixo, e o comando **u** recupera linhas que foram apagadas, similar ao ctrl+z.

#### Dividir tela

É possível didivir a tela do vim com um diretório/arquivo utilizanddo o comando:

```shell
:split /diretório
```

Exemplo:

![vim-split](image-7.png)

O diretório é aberto a partir do diretório raiz.

![vim-split](image-8.png)

O comando ctrl+ww altera entres os arquivos. E **:only** para desfazer as divisões.

#### Busca

Para fazer um busca entre o texto é utilizado o comando **/palavra-procurada**.

Pode utilizar o **n** para buscar outra palavra igual após apertar **enter**.

#### Manual

Por último, o comando **:h** faz aparecer o manuel do editor vim.

Se depois disso tudo você acha que programar pelo vim é complicado, é porque realmente é, saia do vim e abra o vscode/atom/sublime/IntelliJ ou qualquer outra editor de sua escolha e seja feliz.

## 6) Interpretadores de comandos mais utilizados

Reusmo:

```bash
    - sh, bash, csh, tcsh, ksh
    - Ecadeamento de comandos
```
