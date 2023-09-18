## Strings e Ordenação

### Localizando uma Substring com `index`

A função `index` em Perl permite encontrar a posição de uma substring dentro de uma string. Ela retorna o índice (começando em 0) da primeira ocorrência da substring. Aqui está um exemplo:

```perl
my $string = "Olá, Mundo!";
my $substring = "Mundo";
my $index = index($string, $substring);
print "Substring encontrada no índice: $index\n";
```

Saída:
```
Substring encontrada no índice: 7
```

Neste exemplo, a função `index` procura a posição da substring "Mundo" dentro da string "Olá, Mundo!". Ela retorna 7, indicando que a substring começa no índice 7 da string.

### Manipulando uma Substring com `substr`

A função `substr` em Perl permite extrair ou modificar uma substring dentro de uma string com base nos índices especificados. Ela recebe a string, o índice de início e o comprimento (opcional para extração, obrigatório para modificação). Aqui estão alguns exemplos:

```perl
my $string = "Olá, Mundo!";

# Extrair uma substring
my $substring = substr($string, 7, 5);
print "Substring extraída: $substring\n";

# Modificar uma substring
substr($string, 7, 5) = "Universo";
print "String modificada: $string\n";
```

Saída:
```
Substring extraída: Mundo
String modificada: Olá, Universo!
```

No primeiro exemplo, a função `substr` extrai uma substring começando no índice 7 com um comprimento de 5 caracteres. Ela retorna a substring "Mundo".

No segundo exemplo, a função `substr` modifica a string original substituindo a substring "Mundo" (começando no índice 7 com um comprimento de 5) por "Universo". A string resultante é "Olá, Universo!".

Essas funções, `index` e `substr`, fornecem ferramentas úteis para manipular e extrair informações de strings em Perl. Elas são úteis ao lidar com tarefas como buscar substrings específicas ou modificar partes de uma string.

### Formatando Dados com `sprintf`

#### Usando `sprintf` com "Números de Dinheiro"

A função `sprintf` em Perl é uma ferramenta poderosa para formatar dados em padrões de saída específicos. Ao trabalhar com "números de dinheiro" ou valores de moeda, `sprintf` pode ser usado para formatá-los com precisão e opções de formatação apropriadas. Aqui está um exemplo:

```perl
my $valor = 1234.5678;
my $formatado = sprintf("%.2f", $valor);

print "Valor formatado: $formatado\n";
```

Saída:
```
Valor formatado: 1234.57
```

Neste exemplo, a função `sprintf` é usada para formatar a variável `$valor` com duas casas decimais (`%.2f`). O valor formatado resultante é armazenado na variável `$formatado`, que é então impressa no console. O especificador `%f` é usado para representar um número de ponto flutuante, e o `.2` especifica a precisão desejada.

Ajustando a string de formato passada

 para `sprintf`, é possível controlar vários aspectos da saída, como o número de casas decimais, zeros à esquerda e alinhamento.

#### Interpretando Números Não Decimais

O `sprintf` não só permite formatar números decimais, mas também pode lidar com sistemas numéricos não decimais. Você pode usar especificadores de formato para interpretar e formatar números em diferentes bases, como hexadecimal ou octal. Aqui está um exemplo:

```perl
my $numero = 255;

my $hexadecimal = sprintf("%x", $numero);
print "Hexadecimal: $hexadecimal\n";

my $octal = sprintf("%o", $numero);
print "Octal: $octal\n";
```

Saída:
```
Hexadecimal: ff
Octal: 377
```

Neste exemplo, o número decimal `255` é formatado usando `%x` para representação hexadecimal e `%o` para representação octal. Os valores resultantes são armazenados nas variáveis `$hexadecimal` e `$octal`, respectivamente, e então impressos no console.

Ao usar os especificadores de formato apropriados, é possível formatar números em várias bases e incorporá-los em sua saída ou cálculos conforme necessário.

A função `sprintf` fornece uma maneira flexível de formatar dados de acordo com padrões e requisitos específicos. Ela permite controlar a precisão, casas decimais e interpretação de base, entre outras opções de formatação. Compreender e utilizar as capacidades do `sprintf` pode melhorar significativamente sua habilidade de apresentar e manipular dados em Perl.

### Ordenação Avançada

#### Ordenando um Hash por Valor

Ao trabalhar com hashes em Perl, ordená-los com base em seus valores pode ser uma tarefa útil. No entanto, como os hashes são coleções inerentemente não ordenadas, não é possível ordenar diretamente um hash em si. Em vez disso, você pode ordenar as chaves do hash com base em seus valores correspondentes. Aqui está um exemplo de ordenação de um hash por valor:

```perl
my %pontuacao = ("barney" => 195, "fred" => 205, "dino" => 30);

sub por_pontuacao {
    $pontuacao{$b} <=> $pontuacao{$a};
}

my @vencedores = sort por_pontuacao keys %pontuacao;

foreach my $vencedor (@vencedores) {
    print "$vencedor: $pontuacao{$vencedor}\n";
}
```

Saída:
```
fred: 205
barney: 195
dino: 30
```

Neste exemplo, temos um hash `%pontuacao` representando as pontuações de diferentes personagens. Definimos uma sub-rotina `por_pontuacao` que compara os valores do hash usando o operador spaceship `<=>`. A função `sort` é então usada com `por_pontuacao` como sub-rotina de ordenação para ordenar as chaves do hash `%pontuacao` com base em seus valores. As chaves ordenadas são armazenadas no array `@vencedores`.

Por fim, iteramos sobre o array `@vencedores` e imprimimos os nomes dos personagens junto com suas respectivas pontuações.

#### Ordenando por Múltiplas Ch

aves

Em alguns cenários, pode ser necessário ordenar uma lista com base em múltiplas chaves ou critérios. O Perl fornece uma maneira conveniente de fazer isso usando uma sub-rotina de ordenação personalizada que incorpora várias comparações. Vamos considerar um exemplo de ordenação de uma lista de clientes com base em múltiplos critérios:

```perl
my %multas = (
    "cliente1" => 10,
    "cliente2" => 5,
    "cliente3" => 5,
    "cliente4" => 8
);

my %itens = (
    "cliente1" => 3,
    "cliente2" => 5,
    "cliente3" => 2,
    "cliente4" => 7
);

my %nomes = (
    "cliente1" => "João da Silva",
    "cliente2" => "Maria Souza",
    "cliente3" => "Pedro Santos",
    "cliente4" => "Ana Oliveira"
);

my @idsClientes = keys %multas;

@idsClientes = sort {
    $multas{$b} <=> $multas{$a} ||
    $itens{$b} <=> $itens{$a} ||
    $nomes{$a} cmp $nomes{$b} ||
    $a cmp $b
} @idsClientes;

foreach my $idCliente (@idsClientes) {
    print "$idCliente: $nomes{$idCliente}\n";
}
```

Saída:
```
cliente4: Ana Oliveira
cliente1: João da Silva
cliente3: Pedro Santos
cliente2: Maria Souza
```

Neste exemplo, temos três hashes `%multas`, `%itens` e `%nomes`, representando as multas, itens e nomes de diferentes clientes. Começamos obtendo a lista de IDs de clientes usando `keys %multas` e armazenamos os IDs no array `@idsClientes`.

Em seguida, usamos a função `sort` com uma sub-rotina de ordenação personalizada que incorpora múltiplas comparações. A sub-rotina de ordenação compara primeiro as multas dos clientes (`$multas{$b} <=> $multas{$a}`) em ordem decrescente. Se as multas forem iguais, ela compara o número de itens emprestados (`$itens{$b} <=> $itens{$a}`). Se tanto as multas quanto os itens forem iguais, ela compara os nomes dos clientes (`$nomes{$a} cmp $nomes{$b}`) em ordem crescente. Por fim, se todos os critérios anteriores forem iguais, ela compara os próprios IDs dos clientes (`$a cmp $b`) em ordem crescente.

O array `@idsClientes` ordenado é então usado para iterar e imprimir os IDs dos clientes e seus respectivos nomes.

Ao usar uma sub-rotina de ordenação personalizada e incorporar múltiplas comparações, é possível realizar uma ordenação avançada com base em múltiplas chaves ou critérios em Perl. Isso permite controlar precisamente a ordem e priorizar diferentes aspectos dos dados que você está ordenando.