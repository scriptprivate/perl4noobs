## Listas e Arrays

No Perl, uma lista é uma coleção ordenada de valores escalares, enquanto um array é uma variável que armazena uma lista. Arrays são representados pelo símbolo `@` seguido pelo nome do array. Listas podem ser atribuídas a arrays, e elementos de arrays podem ser acessados usando índices. Arrays fornecem uma maneira conveniente de armazenar e manipular múltiplos valores no Perl.

### Acessando Elementos de um Array

Para acessar elementos de um array no Perl, você usa o nome do array seguido pelo índice do elemento desejado entre colchetes `[]`. Os índices do array começam em 0 para o primeiro elemento e incrementam em 1 para cada elemento subsequente. Aqui está um exemplo:

```perl
my @frutas = ("maçã", "banana", "laranja");
print $frutas[0];  # Saída: maçã
print $frutas[1];  # Saída: banana
print $frutas[2];  # Saída: laranja
```

No código acima, declaramos um array `@frutas` contendo três elementos. Acessamos cada elemento usando seu índice e o imprimimos no console.

### Arrays e Índices Especiais

O Perl fornece alguns índices especiais de array que podem ser usados para acessar elementos específicos em um array. Esses índices especiais permitem uma manipulação de array mais flexível e conveniente.

#### Índices Negativos

Índices negativos contam a partir do final do array, sendo que `-1` representa o último elemento, `-2` representa o penúltimo elemento e assim por diante. Aqui está um exemplo:

```perl
my @cores = ("vermelho", "verde", "azul");
print $cores[-1];  # Saída: azul
print $cores[-2];  # Saída: verde
print $cores[-3];  # Saída: vermelho
```

No código acima, usamos índices negativos para acessar elementos a partir do final do array `@cores`.

#### Índices de Intervalo

O Perl também permite especificar um intervalo de índices usando o operador `..`. Isso é útil quando você deseja acessar um subconjunto de elementos em um array. Aqui está um exemplo:

```perl
my @numeros = (1, 2, 3, 4, 5);
my @subconjunto = @numeros[1..3];  # Obter elementos nos índices 1, 2 e 3
print join(", ", @subconjunto);    # Saída: 2, 3, 4
```

No código acima, criamos um array `@numeros` e, em seguida, usamos um índice de intervalo `[1..3]` para acessar elementos nos índices 1, 2 e 3. O subconjunto resultante é armazenado no array `@subconjunto` e impresso no console.

Esses são apenas alguns exemplos de como acessar elementos em um array e usar índices especiais no Perl. Compreender esses conceitos ajudará você a manipular arrays de forma eficaz em seus programas Perl.

### Literais de Lista

No Perl, um literal de lista é uma forma de defin

ir uma lista diretamente em seu código sem atribuí-la a uma variável de array. Ele permite que você especifique uma sequência de valores separados por vírgulas dentro de parênteses ou colchetes. Literais de lista são úteis quando você precisa passar ou manipular um grupo de valores como uma única unidade.

Aqui está um exemplo de um literal de lista:

```perl
my @numeros = (1, 2, 3, 4, 5);
```

No código acima, definimos um array `@numeros` usando um literal de lista. A lista contém cinco elementos: 1, 2, 3, 4 e 5. O array `@numeros` armazenará esses valores.

Literais de lista também podem ser usados diretamente sem atribuí-los a um array. Por exemplo:

```perl
my $soma = 2 + (3, 4, 5);  # $soma será 9
```

Nesse caso, a lista `(3, 4, 5)` é usada em uma expressão para calcular a soma. A lista é tratada como uma única unidade, e seus elementos são avaliados dentro do contexto da expressão.

#### O atalho `qw`

O `qw` (quoted words) é um atalho no Perl que fornece uma forma conveniente de criar uma lista de strings sem precisar usar explicitamente aspas ou vírgulas. Ele permite que você especifique uma sequência de palavras separadas por espaços em branco.

Aqui está um exemplo de uso do atalho `qw`:

```perl
my @frutas = qw(maçã banana laranja);
```

No código acima, definimos um array `@frutas` usando o atalho `qw`. A lista de palavras "maçã," "banana" e "laranja" é convertida em uma lista de strings e atribuída ao array. Isso é equivalente a escrever `("maçã", "banana", "laranja")`.

O atalho `qw` é especialmente útil ao trabalhar com listas de strings que não contêm caracteres especiais como espaços ou aspas. Ele fornece uma forma mais limpa e legível de definir listas de strings.

Você também pode usar o atalho `qw` em combinação com outros operadores e construções do Perl. Por exemplo:

```perl
my $frase = join(" ", qw(Esta é uma frase));  # $frase será "Esta é uma frase"
```

Neste código, o atalho `qw` é usado para definir uma lista de palavras e, em seguida, a função `join` é usada para concatenar essas palavras em uma única string com espaços entre elas.

Esses são os conceitos de literais de lista e do atalho `qw` no Perl. Compreendê-los e usá-los ajudará você a criar e manipular listas e arrays de forma mais eficaz em seus programas Perl.

### Atribuição de Lista

No Perl, a atribuição de lista é um recurso poderoso que permite atribuir múltiplos valores a múltiplas variáveis simultaneamente. É frequentemente usado para manipular arrays, atribuindo e extraindo elementos deles.

Aqui está um exemplo de atribuição de lista:

```perl
my ($nome, $idade, $cidade) = ("João", 30, "Nova York");
```

No código acima, definimos três variáveis escalares `$nome`, `$idade` e `$cidade`. Usando a atribuição de lista, atribuímos os valores "João", 30 e "Nova York" a essas variáveis, respectivamente. O número de variáveis no lado esquerdo deve corresponder ao número de valores no lado direito.

A atribuição de lista também pode ser usada para extrair elementos de um array:

```perl
my ($primeiro, $segundo, $terceiro) = @array;
```

Neste caso, atribuímos os três primeiros elementos de `@array` às variáveis `$primeiro`, `$segundo` e `$terceiro`.

### Os operadores pop e push

Os operadores `pop` e `push` são usados para manipular os elementos de um array adicionando ou removendo elementos no final.

O operador `pop` remove e retorna o último elemento de um array:

```perl
my $ultimo_elemento = pop @array;
```

Neste código, o operador `pop` remove o último elemento de `@array` e o atribui à variável escalar `$ultimo_elemento`.

O operador `push` adicion

a um ou mais elementos ao final de um array:

```perl
push @array, "novo_elemento";
```

Aqui, o operador `push` adiciona a string "novo_elemento" ao final de `@array`.

### Os operadores shift e unshift

Os operadores `shift` e `unshift` são semelhantes ao `pop` e `push`, mas operam no início de um array em vez do final.

O operador `shift` remove e retorna o primeiro elemento de um array:

```perl
my $primeiro_elemento = shift @array;
```

Neste código, o operador `shift` remove o primeiro elemento de `@array` e o atribui à variável escalar `$primeiro_elemento`.

O operador `unshift` adiciona um ou mais elementos ao início de um array:

```perl
unshift @array, "novo_elemento";
```

Neste exemplo, o operador `unshift` adiciona a string "novo_elemento" ao início de `@array`.

### O operador splice

O operador `splice` é uma ferramenta versátil para adicionar, remover ou substituir elementos em um array em qualquer posição.

Aqui está um exemplo de uso do operador `splice` para remover elementos de um array:

```perl
my @elementos_removidos = splice @array, 2, 3;
```

Neste código, o operador `splice` remove três elementos de `@array` a partir do índice 2 e os retorna como uma lista. O array `@array` será modificado de acordo.

O operador `splice` também pode ser usado para inserir elementos em um array:

```perl
splice @array, 2, 0, "novo_elemento";
```

Neste caso, o operador `splice` insere a string "novo_elemento" no índice 2 em `@array`. O segundo argumento (0) especifica que nenhum elemento deve ser removido.

Esses são os conceitos de atribuição de lista, os operadores `pop` e `push`, os operadores `shift` e `unshift` e o operador `splice` no Perl. Compreender e utilizá-los ajudará você a manipular arrays de forma eficaz e realizar várias operações em seus elementos.

### Interpolando Arrays em Strings

Em Perl, você pode interpolar arrays diretamente em strings, permitindo incluir os elementos de um array dentro de uma string. Isso pode ser útil ao construir saída dinâmica ou gerar texto formatado.

Aqui está um exemplo de interpolação de um array em uma string:

```perl
my @fruits = ("maçã", "banana", "laranja");
my $mensagem = "Eu gosto de comer @fruits.";

print $mensagem;
```

No código acima, o array `@fruits` é interpolado na string `$mensagem` usando o sigilo `@` seguido do nome do array. Quando a string é impressa, os elementos do array serão inseridos, separados por espaços. A saída será: "Eu gosto de comer maçã banana laranja".

Você também pode controlar o separador usado entre os elementos do array, especificando um valor diferente na variável `$"`, ou `$LIST_SEPARATOR`. Por padrão, `$"` é definido como um espaço, mas você pode alterá-lo para qualquer valor de string:

```perl
my @fruits = ("maçã", "banana", "laranja");
$" = ", ";  # Definindo o separador da lista como uma vírgula e um espaço
my $mensagem = "Eu gosto de comer @fruits.";

print $mensagem;
```

Neste exemplo, o array `@fruits` é interpolado na string `$mensagem`, mas o separador da lista é definido como ", ". A saída será: "Eu gosto de comer maçã, banana, laranja".

Observe que, ao interpolar arrays em strings, os elementos do array são convertidos em strings usando sua representação padrão de string, que pode não ser sempre o que você espera. Se você precisar de mais controle sobre a formatação dos elementos do array, pode usar a função `join` para concatená-los com um separador personalizado.

Entender como interpolar arrays em strings permite criar saídas dinâmicas e flexíveis, incorporando os valores dos arrays diretamente no texto.

### A estrutura de controle foreach

A estrutura de controle `foreach` em Perl permite iterar sobre os elementos de um array ou uma lista. Ela fornece uma maneira fácil de executar uma ação em cada elemento sem gerenciar explicitamente índices de array ou usar um contador de loop.

Aqui está um exemplo de uso do `foreach` para iterar sobre um array:

```perl
my @numbers = (1, 2, 3, 4, 5);

foreach my $num (@numbers) {
    print $num, " ";
}

# Saída: 1 2 3 4 5
```

No código acima, o loop `foreach` itera sobre cada elemento no array `@numbers`. A variável `$num` assume o valor de cada elemento por vez, e a ação dentro do loop (imprimir o elemento seguido de um espaço) é executada. A saída será os números separados por espaços.

#### O Favorito Padrão do Perl: `$_`

Em Perl, há uma variável especial padrão chamada `$_` (sublinhado) que é frequentemente usada implicitamente dentro de loops `foreach` ou outras operações. Quando nenhuma variável explícita é fornecida, `$_` é usada por padrão.

Aqui está um exemplo de uso de `$_` dentro de um loop `foreach

`:

```perl
my @fruits = ("maçã", "banana", "laranja");

foreach (@fruits) {
    print "Eu gosto de $_. ";
}

# Saída: Eu gosto de maçã. Eu gosto de banana. Eu gosto de laranja.
```

Neste código, `$_` representa cada elemento do array `@fruits` conforme iteramos sobre ele. Usamos `$_` diretamente no corpo do loop para se referir ao elemento atual.

#### O operador `reverse`

O operador `reverse` em Perl permite inverter a ordem dos elementos em um array ou em uma lista. Ele retorna uma nova lista ou array com os elementos na ordem inversa.

Aqui está um exemplo de uso do operador `reverse`:

```perl
my @numbers = (1, 2, 3, 4, 5);
my @reversed_numbers = reverse @numbers;

print join(", ", @reversed_numbers);

# Saída: 5, 4, 3, 2, 1
```

No código acima, `reverse @numbers` inverte a ordem dos elementos no array `@numbers`, e o novo array invertido é armazenado em `@reversed_numbers`. A função `join` é então usada para unir os elementos de `@reversed_numbers` com um separador de vírgula e espaço antes de imprimi-los.

#### O operador `sort`

O operador `sort` em Perl permite ordenar os elementos de um array ou de uma lista em ordem ascendente. Ele retorna uma nova lista ou array com os elementos ordenados.

Aqui está um exemplo de uso do operador `sort`:

```perl
my @fruits = ("banana", "apple", "orange");
my @sorted_fruits = sort @fruits;

print join(", ", @sorted_fruits);

# Saída: apple, banana, orange
```

Neste código, `sort @fruits` ordena os elementos do array `@fruits` em ordem alfabética, e o novo array ordenado é armazenado em `@sorted_fruits`. A função `join` é usada para unir os elementos de `@sorted_fruits` com um separador de vírgula e espaço antes de imprimi-los.

Compreender a estrutura de controle `foreach`, a variável padrão `$_` do Perl, o operador `reverse` e o operador `sort` fornece ferramentas poderosas para iterar sobre arrays, manipular a ordem dos elementos e realizar operações nos elementos do array.

#### O operador `each`

O operador `each` é usado para iterar sobre pares chave-valor de um array associativo (também conhecido como hash) em Perl. Ele permite obter cada par chave-valor um de cada vez e é frequentemente usado em conjunto com um loop `while`.

A sintaxe para usar o operador `each` é a seguinte:
```perl
while (my ($chave, $valor) = each %hash) {
    # Código para processar cada par chave-valor
}
```

O operador `each` retorna o próximo par chave-valor do hash e avança o iterador. Ele retorna uma lista de dois elementos em contexto escalar, em que o primeiro elemento é a chave e o segundo elemento é o valor correspondente. Uma vez que todos os pares chave-valor tenham sido iterados, o operador `each` retorna uma lista vazia, indicando o fim do hash.

Aqui está um exemplo que demonstra o uso do operador `each`:
```perl
my %fruta_cor = (
    maçã   => 'vermelha',
    banana => 'amarela',
    cereja => 'vermelha',
);

while (my ($fruta, $cor) = each %fruta_cor) {
    print "A cor da $fruta é $cor\n";
}
```
Saída:
```
A cor da maçã é vermelha
A cor da banana é amarela
A cor da cereja é vermelha
```

No exemplo acima, temos um hash `%fruta_cor` contendo nomes de frutas como chaves e suas cores correspondentes como valores. O loop `while` usando o operador `each` itera sobre cada par chave-valor, extrai a fruta e a cor, e as imprime.

É importante observar que o operador `each` modifica o iterador interno do hash, o que pode ter implicações se você modificar o hash durante a iteração. Para redefinir explicitamente o iterador, você pode usar a expressão `keys %hash` antes de iterar novamente sobre o hash.

O operador `each` fornece uma maneira conveniente de iterar sobre os pares chave-valor de um hash em Perl, permitindo que você processe cada elemento individualmente.

### Contexto Escalar e Contexto de Lista

Em Perl, expressões podem ser avaliadas tanto em contexto escalar quanto em contexto de lista. O contexto no qual uma expressão é avaliada determina como a expressão se comporta e o que ela retorna.

#### Usando Expressões que Produzem Listas em Contexto Escalar

Existem expressões que normalmente produzem uma lista quando utilizadas, mas se forem usadas em contexto escalar, retornam um resultado modificado. O comportamento específico em contexto escalar depende da própria expressão.

Um exemplo é a função `sort`. Em contexto de lista, ela ordena uma lista e retorna a lista ordenada. No entanto, quando usada em contexto escalar, ela retorna `undef`. Aqui está um exemplo:

```perl
my @numbers = (5, 3, 1, 4, 2);
my $sorted = sort @numbers;   # $sorted é indefinido
```

Outro exemplo é a função `reverse`. Em contexto de lista, ela retorna uma lista invertida, mas em contexto escalar, ela retorna uma string invertida ou a concatenação invertida de todas as strings em uma lista. Aqui está um exemplo:

```perl
my @words = qw(apple banana cherry);
my $reversed = reverse @words;   # $reversed é "yrrehc ananab elppa"
```

#### Usando Expressões que Produzem Escalares em Contexto de Lista

Inversamente, algumas expressões normalmente produzem um resultado escalar, mas podem ser usadas em contexto de lista. Nesses casos, o valor escalar é automaticamente promovido para criar uma lista de um único elemento. Esse comportamento permite flexibilidade em atribuições de listas e concatenação. Aqui está um exemplo:

```perl
my $count = 42;
my @list = ($count);   # @list contém um único elemento [42]
```

#### Forçando o Contexto Escalar

Às vezes, pode ser necessário forçar explicitamente um contexto escalar quando Perl está esperando um contexto de lista. Para fazer isso, você pode usar a função `scalar`, que instrui Perl a fornecer um contexto escalar.

Aqui está um exemplo que demonstra a forçagem de contexto escalar:

```perl
my @fruits = qw(apple banana cherry);
my $fruit_count = scalar @fruits;   # $fruit_count é 3
```

No exemplo acima, a função `scalar` é usada para obter a contagem de elementos no array `@fruits`, forçando o array a ser avaliado em contexto escalar.

Forçar o contexto escalar pode ser útil quando você precisa realizar operações que exigem um único valor escalar, como contar os elementos de um array ou obter o tamanho de uma string.

Compreender o contexto escalar e o contexto de lista é crucial em Perl, pois isso determina como as expressões são avaliadas e quais resultados elas produzem. Estar ciente do contexto no qual as expressões são usadas permite que você escreva código Perl mais eficiente e flexível.

### <STDIN> em Contexto de Lista

Em Perl, `<STDIN>` é um operador especial usado para ler a entrada do usuário a partir da entrada padrão. Por padrão, `<STDIN>` lê a entrada linha por linha e retorna a próxima linha como uma string em contexto escalar. No entanto, quando usado em contexto de lista, `<STDIN>` retorna todas as linhas restantes até o final do arquivo como elementos separados de um array.

Aqui está um exemplo que demonstra o uso de `<STDIN>` em contexto de lista:

```perl
print "Digite algumas linhas de texto (pressione Ctrl+D no Unix ou Ctrl+Z no Windows para finalizar):\n";

my @linhas = <STDIN>;  # Lê as linhas da entrada padrão

print "Você digitou ", scalar @linhas, " linhas:\n";

foreach my $linha (@linhas) {
    print $linha;
}
```

No código acima, o usuário é solicitado a digitar algumas linhas de texto. O operador `<STDIN>` é usado em uma atribuição de array (`@linhas = <STDIN>`) para ler todas as linhas de entrada até o final do arquivo. Cada linha é armazenada como um elemento separado no array `@linhas`.

Após a leitura da entrada, o código imprime o número de linhas digitadas (`scalar @linhas`) e, em seguida, itera sobre cada linha usando um loop `foreach` para exibi-las.

É importante observar que, quando a entrada vem de um arquivo, o uso de `<STDIN>` em contexto de lista lerá o restante do arquivo. No entanto, quando a entrada vem do teclado, você precisará indicar o final do arquivo. Em sistemas Unix, pressionar Ctrl+D é usado para sinalizar o final da entrada, enquanto em sistemas Windows, Ctrl+Z é usado.

Usar `<STDIN>` em contexto de lista é uma maneira conveniente de ler várias linhas de entrada e processá-las como elementos separados em um array. Isso permite lidar com a entrada de forma interativa ou a partir de arquivos de maneira simples.
