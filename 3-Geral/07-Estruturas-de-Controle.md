## Estruturas de Controle

As estruturas de controle em Perl permitem controlar o fluxo de execução em seus programas. Elas permitem tomar decisões, executar ações repetidamente e lidar com diferentes condições com base no valor verdade de expressões específicas.

### O que é Verdade?

Em Perl, o conceito de verdade é baseado no valor verdade das expressões. Uma expressão é considerada verdadeira se for diferente de zero, não vazia ou definida. Por outro lado, uma expressão é considerada falsa se for zero, vazia ou indefinida.

Perl fornece várias estruturas de controle que permitem avaliar o valor verdade das expressões e executar ações de acordo.

#### As declarações `if`, `elsif` e `else`

A declaração `if` é usada para executar condicionalmente um bloco de código se uma determinada condição for verdadeira. Aqui está a sintaxe básica:

```perl
if ($condicao) {
    # código a ser executado se $condicao for verdadeira
}
```

Opcionalmente, você pode usar a declaração `elsif` para avaliar condições adicionais:

```perl
if ($condicao1) {
    # código a ser executado se $condicao1 for verdadeira
}
elsif ($condicao2) {
    # código a ser executado se $condicao2 for verdadeira
}
```

Se nenhuma das condições for verdadeira, você pode usar a declaração `else` para executar um bloco de código:

```perl
if ($condicao1) {
    # código a ser executado se $condicao1 for verdadeira
}
elsif ($condicao2) {
    # código a ser executado se $condicao2 for verdadeira
}
else {
    # código a ser executado se nenhuma das condições for verdadeira
}
```

### As declarações `given` e `when`

As declarações `given` e `when` em Perl fornecem uma maneira conveniente de escrever declarações semelhantes a switch. Elas permitem comparar uma variável com uma série de valores e executar código com base na condição correspondente.

Aqui está um exemplo de uso de `given` e `when`:

```perl
given ($variavel) {
    when ($valor1) {
        # código a ser executado se $variavel corresponder a $valor1
    }
    when ($valor2) {
        # código a ser executado se $variavel corresponder a $valor2
    }
    default {
        # código a ser executado se nenhuma das condições for verdadeira
    }
}
```

A declaração `given` define a variável a ser correspondida, e as declarações `when` definem as condições a serem verificadas. Se ocorrer uma correspondência, o bloco de código correspondente é executado. Se nenhuma das condições corresponder, o bloco `default` é executado.

### Estruturas de Loop

Perl fornece várias estruturas de loop que permitem repetir um bloco de código várias vezes ou iterar sobre uma lista de valores.

#### O Loop `while`

O loop `while` executa repetidamente um bloco de código enquanto uma determinada condição for verdadeira. Aqui está a sintaxe básica:

```perl
while ($condicao) {
    # código a ser executado enquanto $condicao for verdadeira
}
```

Aqui está um exemplo:

```perl
my $contador = 0;
while ($contador < 5) {
    print "Contador: $contador\n";
    $contador++;
}
```

Este loop executará o bloco de código enquanto a variável `$contador` for menor que 5.

#### O Loop `for`

O loop `for` permite iterar sobre uma lista de valores ou uma faixa de números. Aqui está a sintaxe básica:

```perl
for (my $i = 0; $i < $limite; $i++) {
    # código a ser executado em cada iteração
}
```

Aqui está um exemplo:

```perl
for (my $i = 1; $i <= 5; $i++) {
    print "Número: $i\n";
}
```

Este loop irá iterar de 1 a 5 e imprimir o número atual em cada iteração.

#### O Loop `foreach`

O loop `foreach` é usado para iterar sobre cada elemento de uma lista ou um array. Ele atribui automaticamente cada elemento a uma variável para processamento. Aqui está a sintaxe básica:

```perl
foreach my $elemento (@lista) {
    # código a ser executado para cada $elemento
}
```

Aqui está um exemplo:

```perl
my @frutas = ("maçã", "banana", "laranja");
foreach my $fruta (@frutas) {
    print "Fruta: $fruta\n";
}
```

Este loop irá iterar sobre cada elemento no array `@frutas` e imprimir o nome da fruta.

Essas estruturas de loop fornecem flexibilidade e controle ao lidar com tarefas repetitivas e iterar sobre coleções de dados.

Lembre-se de usar recuo adequado e chaves para definir o escopo dos blocos de código dentro das estruturas de controle.

## Mais Estruturas de Controle

Em Perl, existem várias estruturas de controle que permitem modificar o fluxo do seu programa com base em condições e loops. Essas estruturas de controle fornecem flexibilidade e permitem escrever código mais expressivo e poderoso. Neste documento, vamos explorar as seguintes estruturas de controle:

### A Estrutura de Controle `unless`

A estrutura de controle `unless` é semelhante à estrutura `if`, mas com uma condição invertida. Ela permite executar um bloco de código se uma condição for falsa. Aqui está um exemplo:

```perl
my $idade = 17;
unless ($idade >= 18) {
    print "Você não tem idade suficiente para votar.\n";
}
```

Neste exemplo, o bloco de código será executado somente se a condição `$idade >= 18` for falsa.

#### A Cláusula `else` com `unless`

Você também pode usar a cláusula `else` com `unless` para especificar um bloco de código alternativo a ser executado quando a condição for verdadeira. Aqui está um exemplo:

```perl
my $idade = 20;
unless ($idade >= 18) {
    print "Você não tem idade suficiente para votar.\n";
} else {
    print "Você pode votar na próxima eleição.\n";
}
```

Neste caso, se a condição `$idade >= 18` for falsa, o primeiro bloco de código será executado. Caso contrário, se a condição for verdadeira, o bloco `else` será executado.

### A Estrutura de Controle `until`

A estrutura de controle `until` é usada para executar repetidamente um bloco de código até que uma condição se torne verdadeira. Ela é o oposto da estrutura `while`. Aqui está um exemplo:

```perl
my $contagem_regressiva = 10;
until ($contagem_regressiva == 0) {
    print "Contagem regressiva: $contagem_regressiva\n";
    $contagem_regressiva--;
}
```

Neste exemplo, o bloco de código será executado até que a condição `$contagem_regressiva == 0` se torne verdadeira. O valor de `$contagem_regressiva` é impresso e decrementado a cada iteração.

### Modificadores de Expressão

Perl fornece modificadores de expressão que permitem escrever estruturas de controle mais concisas. Esses modificadores vêm após a instrução que eles modificam e eliminam a necessidade de chaves explícitas. Aqui estão alguns exemplos:

```perl
my $flag = 1;
print "Olá, Mundo!\n" if $flag == 1;
```

Neste exemplo, a instrução `print` é executada apenas se a condição `$flag == 1` for verdadeira.

```perl
my $num = 10;
$num *= 2 while $num < 100;
```

Neste exemplo, o valor de `$num` é multiplicado por 2 repetidamente enquanto a condição `$num < 100` permanecer verdadeira.

### A Estrutura de Controle de Bloco Nu

Às vezes, você pode querer agrupar um conjunto de declarações em um bloco sem qualquer estrutura de controle associada. Isso é conhecido como uma estrutura de controle de bloco nu. Ela permite que você defina um escopo para variáveis ou organize seu código. Aqui está um exemplo:

```perl
{
    my $nome = "João";
    print "Olá, $nome!\n";
}
```

Neste exemplo, o bloco de código cria uma variável lexical `$nome` e imprime uma saudação. O bloco define seu próprio escopo, e quaisquer variáveis declaradas dentro dele são locais a esse bloco.

### A Cláusula elsif

A cláusula `elsif` é usada para verificar múltiplas condições após uma declaração `if` inicial. Ela permite fornecer condições alternativas a serem avaliadas se a condição inicial for falsa. Aqui está um exemplo:

```perl
my $nota = 85;

if ($nota >= 90) {
    print "Excelente!\n";
} elsif ($nota >= 80) {
    print "Bom trabalho!\n";
} elsif ($nota >= 70) {
    print "Não está mal.\n";
} else {
    print "Você precisa estudar mais.\n";
}
```

Neste exemplo, múltiplas condições são verificadas usando cláusulas `elsif`. Dependendo do valor de `$nota`, diferentes mensagens são impressas.

### Autoincremento e Autodecremento

Perl fornece os operadores de autoincremento (`++`) e autodecremento (`--`), que permitem incrementar ou decrementar o valor de uma variável em um. Esses operadores podem ser usados em várias estruturas de controle. Aqui está um exemplo:

```perl
my $contador = 1;

while ($contador <= 5) {
    print "Contador: $contador\n";
    $contador++;
}
```

Neste exemplo, o operador `++` é usado para incrementar o valor de `$contador` em um a cada iteração do loop `while`.

#### O Valor do Autoincremento

O operador de autoincremento `++` retorna o valor da variável antes de ser incrementada. No entanto, se você colocar o operador após a variável (`$contador++`), ele retorna o valor após o incremento. Aqui está um exemplo:

```perl
my $contador = 1;
my $resultado = $contador++;

print "Resultado: $resultado\n";  # Saída: Resultado: 1
print "Contador: $contador\n";    # Saída: Contador: 2
```

Neste exemplo, o valor de `$contador` é primeiro atribuído a `$resultado` e, em seguida, `$contador` é incrementado em um.

### A Estrutura de Controle for

A estrutura de controle `for` é usada para iterar sobre uma coleção de valores ou um intervalo de valores. Ela permite executar um bloco de código para cada valor na coleção ou intervalo. Aqui está um exemplo:

```perl
for my $num (1..5) {
    print "Número: $num\n";
}
```

Neste exemplo, o bloco de código é executado cinco vezes, com a variável `$num` assumindo os valores de 1 a 5.

#### A Conexão Secreta Entre foreach e for

Em Perl, `foreach` e `for` são equivalentes, e você pode usá-los indistintamente. A palavra-chave `foreach` é comumente usada para iterar sobre uma coleção, enquanto `for` é usada para iterar sobre um intervalo. No entanto, ambas as estruturas de controle funcionam da mesma maneira. Aqui está um exemplo:

```perl
my @frutas = ("maçã", "banana", "cereja");

foreach my $fruta (@frutas) {
    print "Fruta: $fruta\n";
}

# Código equivalente usando for
for my $fruta (@frutas) {
    print "Fruta: $fruta\n";
}
```

Neste exemplo, tanto `foreach` quanto `for` são usados para iterar sobre o array `@frutas`, imprimindo cada fruta.

### Controles de Loop

Os controles de loop em Perl permitem que você altere o fluxo normal dos loops e blocos. Eles permitem sair de um loop prematuramente, pular a iteração atual ou repetir uma iteração de loop. Vamos explorar essas estruturas de controle de loop:

#### O Operador `last`

O operador `last` é usado para sair de um loop prematuramente. Quando encontrado, ele termina imediatamente o loop e retoma a execução após o loop. Aqui está um exemplo:

```perl
for my $i (1..10) {
    last if $i == 5;
    print "$i ";
}
```

Neste exemplo, o loop itera de 1 a 10, mas quando `$i` se torna 5, o operador `last` é acionado e o loop termina.

#### O Operador `next`

O operador `next` é usado para pular a iteração atual de um loop e passar para a próxima iteração. Quando encontrado, ele pula imediatamente para a próxima iteração sem executar o código restante dentro da iteração atual. Aqui está um exemplo:

```perl
for my $i (1..5) {
    next if $i == 3;
    print "$i ";
}
```

Neste exemplo, o loop itera de 1 a 5, mas quando `$i` se torna 3, o operador `next` é acionado e o código dentro dessa iteração é pulado.

#### O Operador `redo`

O operador `redo` é usado para repetir a iteração atual de um loop. Quando encontrado, ele reavalia a condição do loop e reinicia a iteração atual sem avançar para a próxima iteração. Aqui está um exemplo:

```perl
my $count = 0;

while ($count < 5) {
    $count++;
    redo if $count == 3;
    print "$count ";
}
```

Neste exemplo, o loop incrementa `$count` e imprime seu valor. Quando `$count` se torna 3, o operador `redo` é acionado e a iteração reinicia sem incrementar `$count`.

#### Blocos com Rótulos

Perl permite rotular blocos de código usando a sintaxe `RÓTULO:`. Os blocos com rótulos fornecem uma maneira de se referir a blocos específicos dentro de loops ou condicionais aninhados. Aqui está um exemplo:

```perl
EXTERNO: for my $i (1..3) {
    INTERNO: for my $j (1..3) {
        last EXTERNO if $i == 2;
        print "$i-$j ";
    }
}
```

Neste exemplo, temos um loop externo e um loop interno. Os rótulos `EXTERNO:` e `INTERNO:` são usados para marcar os blocos. Quando a condição `$i == 2` é atendida, a instrução `last EXTERNO` sai de ambos os loops.

Essas estruturas de controle de loop oferecem mais flexibilidade e controle sobre o fluxo de execução dentro de loops e blocos de código. Elas permitem sair de loops prematuramente, pular iterações, repetir iterações e lidar com estruturas aninhadas complexas usando blocos rotulados.

### O Operador Condicional `?:`

O operador condicional, também conhecido como operador ternário, permite tomar decisões com base em uma condição. Ele possui a seguinte sintaxe:

```perl
CONDIÇÃO ? EXPRESSÃO_SE_VERDADEIRO : EXPRESSÃO_SE_FALSO;
```

Aqui está um exemplo:

```perl
my $idade = 25;
my $é_adulto = $idade >= 18 ? 1 : 0;
```

Neste exemplo, o valor de `$é_adulto` será 1 se `$idade` for maior ou igual a 18; caso contrário, será 0.

### Operadores Lógicos

Operadores lógicos permitem combinar condições e realizar operações lógicas. Vamos explorar alguns operadores lógicos comumente usados no Perl:

#### O Valor de um Operador de Curto-Circuito

Operadores lógicos no Perl, como `&&` (E lógico) e `||` (OU lógico), exibem um comportamento de curto-circuito. Isso significa que eles avaliam apenas o necessário da expressão para determinar o resultado final. Aqui está um exemplo:

```perl
my $valor = 0;
my $resultado = $valor && 10;  # $resultado será 0
```

Neste exemplo, como `$valor` é falso, o operador E lógico `&&` para de avaliar a expressão após encontrar o valor falso e atribui o resultado como 0.

#### O Operador definido-ou

O operador definido-ou (`//`) oferece uma maneira conveniente de atribuir um valor padrão se uma variável não estiver definida ou for falsa. Aqui está um exemplo:

```perl
my $nome = $nome_input // "Desconhecido";
```

Neste exemplo, se `$nome_input` estiver definido e for verdadeiro, `$nome` receberá o seu valor. Caso contrário, `$nome` receberá o valor padrão "Desconhecido".

#### Estruturas de Controle Utilizando Operadores de Avaliação Parcial

Operadores de avaliação parcial, como `and`, `or` e `xor`, permitem combinar condições e realizar estruturas de controle de maneira concisa. Aqui está um exemplo:

```perl
my $valor = 5;

$valor > 0 and print "Positivo";
$valor < 0 or print "Negativo";
$valor == 0 xor print "Zero";
```

Neste exemplo, o operador `and` verifica se `$valor` é maior que 0 e, em seguida, executa o comando `print` se a condição for verdadeira. Da mesma forma, o operador `or` verifica se `$valor` é menor que 0 e executa o comando `print` se a condição for verdadeira. O operador `xor` verifica se `$valor` é igual a 0 e executa o comando `print` se a condição for verdadeira, mas não executa se ambas as condições forem verdadeiras.

Essas estruturas de controle fornecem ferramentas poderosas para lidar com condições, combinar operações lógicas e controlar o fluxo do seu código Perl. Elas permitem tomar decisões com base em condições, atribuir valores padrão e criar estruturas de controle concisas usando operadores de avaliação parcial.
