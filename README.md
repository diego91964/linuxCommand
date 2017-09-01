# Administração de usuários

## Adicionar Usuário

### Comando adduser (root)


```
adduser teste

```

Cria novo usuário sem o diretório home


```
useradd -m -d /home/userTeste userTeste

```

Cria novo usuário com o diretório home


Além disso é possível utilizar outras opções:

* -d Apontar qual é o diretório home será utilizado para este usuário

* -s Qual será o programa de inicialização do usuário, normalmente se usa o shell

* -p Para cadastrar uma senha.

* -m Criar um diretório home

* -g Adicionar usuário em um grupo (primário)

* -G Adicionar usuário em um grupo (demais grupos)


```

$ groupadd grupo
$ groupadd grupo1
$ groupadd grupo2
$ useradd -g grupo1 -G grupo2 -s /bin/bash -p usuarioTeste -d/home/usuarioTeste -m usuarioTeste

```
Para verificar se o usuário que você criou está realmente cadastrado execute:

```
cat /etc/passwd | grep usuarioTeste
```

```
Resultado usuarioTeste:x:1001:1003::/home/usuarioTeste:/bin/bash

```

Caso o comando seja executado sem o grep, todos os usuários serão listados.

## Alterar usuários

O comando usermod é utilizado para modificar um usuário

```
$ usermod usuarioTeste -g grupo

```

Para verificar os grupos que o usuário pertence execute o seguinte comando:

```
$ groups ```

```


* -d Apontar qual é o diretório home será utilizado para este usuário

* -s Qual será o programa de inicialização do usuário, normalmente se usa o shell

* -p Para cadastrar uma senha.

* -m Criar um diretório home

* -g Adicionar usuário em um grupo (primário)

* -G Adicionar usuário em um grupo (demais grupos)


## Remover usuário

O comando para remover o usuário é mais simples

```
$ userdel usuarioTeste

```

Caso você tenha realizado testes com o usuário, a seguinte mensagem pode aparecer:

```
$ userdel: user usuarioTeste is currently used by process 15977
```

Então, é necessário matar o processo executando o seguinte comando:

```

$ kill -9 159777

```


# Manipulação de dados

## Comando awk

Comando utilizado para criação de filtros de busca.

### Busca apenas a coluna 2 (coluna de ips)

```
cat exemplos/awk/ips | awk '{print $2}'

```

### Busca apenas faixa de ip (último número da coluna 2)

```
cat exemplos/awk/ips | awk -F ":" '{print substr($2,12)}'

```

### Busca apenas primeiro número do ip

```
cat exemplos/awk/ips | awk -F ":" '{print substr($2,1,4)}'

```

### Busca ips entre 2 e 5

```
cat exemplos/awk/ips | awk -F ":" '{if ((substr($2,12)) >= "2" && (substr($2,12)) <= "5" ) print}'
```

### Busca ips 192 e substitui para 192

```
cat exemplos/awk/ips | awk '{sub(substr($2,1,3),"193"); print $0}'
```

### Extra e tutorial

[Tutorial](http://rberaldo.com.br/tutorial-awk/)

[Ebook](https://www.amazon.com.br/gp/product/B004D4Y302/ref=as_li_qf_sp_asin_il_tl?ie=UTF8&camp=1789&creative=9325&creativeASIN=B004D4Y302&linkCode=as2&tag=blodober-20)

[Manual GNU](https://www.gnu.org/software/gawk/manual/gawk.html)

[Manual](https://linux.die.net/man/1/awk)

# Comando at

O comando at é utilizado para gerenciar tarefas, para utilizá-lo você deve
iniciar o agendador com o horário que deseja que a tarefa seja executada.


### Cria arquivo de teste com o texto olá

Executa comando hoje as 11:00 AM

```
at 11am today

```

```
echo olá > exemplos/at/testeat

```

### Substitui ips 192 por 193 do arquivo exemplo e cria arquivo resultado

Executa comando hoje as 11:02 AM

```
at 11:02am today

```

```
cat exemplos/at/exemplo | awk '{sub(substr($2,1,3),"193"); print $0}' > exemplos/at/resultado

```

```
^D (Control D)

```

```
O resultado deverá ser o seguinte:

warning: commands will be executed using /bin/sh
at> cat exemplos/at/exemplo | awk '{sub(substr($2,1,3),"193"); print $0}' > exemplos/at/resultado
at> <EOT>
job 5 at Fri Aug 18 11:02:00 2017
```

## Comando cal

O comando cal é utilizado para mostrar o calendário no terminal

Exibe o calendário de agosto de 2017.

```
cal 08 2017

```
Ex. de Resposta

```
August 2017       
Su Mo Tu We Th Fr Sa  
       1  2  3  4  5  
 6  7  8  9 10 11 12  
13 14 15 16 17 18 19  
20 21 22 23 24 25 26  
27 28 29 30 31
```

Exibe o calendário do ano corrente

```
cal -y

```


Exibe o calendário do ano 2000

```
cal -y 2000

```

# Comando calendar

Exibe a lista de eventos do mês corrente.

```
calendar

```

# Comando cat

O comando cat pode ser utilizado para concatenar ou printar arquivos no terminal.


## Print simples

```

cat exemplos/cat/exemplo1.txt

```

Apenas imprime o conteúdo do arquivo na tela.


## Print com número de linhas

```
cat -n exemplos/cat/exemplo1.txt

```

Imprime conteúdo do arquivo com numeração das linhas


## Concatenar dois arquivos

```

cat exemplos/cat/*.txt

```

Imprime todos os arquivos que possuem .txt como sufixo.


## Imprimir um arquivo em outro


```

cat exemplos/cat/exemplo1.txt > teste


```

Imprime o conteúdo do arquivo exemplo1.txt no arquivo teste
