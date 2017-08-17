
## adduser (root)
Cria novo usuário

```
adduser teste
```

## awk

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

## Comando at

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
