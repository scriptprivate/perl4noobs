## Dados Escalares

Dados escalares referem-se a valores individuais na programação Perl. Eles podem representar números, strings ou valores especiais como `undef`.

### Números

Perl suporta tipos de dados numéricos, incluindo inteiros e números de ponto flutuante. Valores numéricos podem ser usados para várias operações e cálculos.

```perl
my $numero = 42;
```

### Todos os Números Possuem o Mesmo Formato Internamente

Internamente, Perl trata todos os números em um formato semelhante. Ele não diferencia entre inteiros e números de ponto flutuante ao realizar cálculos.

```perl
my $resultado = 10 / 3;
```

### Literais de Ponto Flutuante

Literais de ponto flutuante em Perl são valores numéricos com um componente fracionário. Eles podem ser escritos em notação decimal, como `3.14`, e são úteis para representar valores fracionários precisos.

```perl
my $pi = 3.14;
```

### Literais de Inteiro

Literais de inteiro representam números inteiros em Perl. Eles podem ser escritos sem um componente fracionário, como `42`, e são usados para tarefas que envolvem contagem ou quantidades discretas.

```perl
my $count = 42;
```

### Literais de Inteiro Não Decimal

Perl permite o uso de literais de inteiro não decimais. Esses literais representam números em outros sistemas numéricos, como octal (base 8) ou hexadecimal (base 16). Números octais começam com um `0` à esquerda (por exemplo, `0377`), enquanto números hexadecimais começam com `0x` ou `0X` (por exemplo, `0xFF`).

```perl
my $octal = 0377;
my $hexadecimal = 0xFF;
```

### Operadores Numéricos

Perl oferece vários operadores para realizar operações aritméticas em valores numéricos. Esses operadores incluem adição (`+`), subtração (`-`), multiplicação (`*`), divisão (`/`) e outros. Eles permitem manipular dados numéricos e realizar cálculos dentro de programas Perl.

```perl
my $soma = 10 + 5;
my $diferenca = 10 - 5;
my $produto = 10 * 5;
my $quociente = 10 / 5;
```

### Strings

Strings são sequências de caracteres entre aspas. Perl oferece diferentes maneiras de representar e manipular strings.

#### Literais de String com Aspas Simples

Literais de string com aspas simples em Perl são delimitados por aspas simples (`'`). O conteúdo da string é tratado como caracteres literais, e variáveis e sequências de escape não são interpoladas.

```perl
my $nome = 'Fulano de Tal';
```

#### Literais de String com Aspas Duplas

Literais de string com aspas duplas em Perl são delimitados por aspas duplas (`"`). Eles permitem a interpolação de variáveis e a interpretação de sequências de escape, facilitando a inclusão de variáveis e caracteres especiais dentro da string.

```perl
my $idade = 25;
my $mensagem = "Minha idade é $idade anos.";
```

#### Operadores de Strings

O Perl oferece diversos operadores para manipular e combinar strings. Esses operadores incluem concatenação (`.`), repetição (`x`) e comparação de strings (`eq`, `ne`, etc.).

```perl
my $saudacao = "Olá" . ", " . "Mundo!";
my $repetido = "abc" x 3;
my $comparacao = "maçã" eq "laranja";
```

#### Conversão Automática entre Números e Strings

O Perl realiza automaticamente a conversão entre números e strings quando necessário. Se você usar um valor numérico em um contexto de string, ele será tratado como uma string. Da mesma forma, se você usar um valor de string em um contexto numérico, o Perl tentará convertê-lo em um número.

```perl
my $numérico = 42 + "10";   # $numérico é 52
my $string = "A resposta é " . 42;   # $string é "A resposta é 42"
```

### Avisos Incorporados do Perl

O Perl fornece avisos incorporados que podem ajudar a identificar possíveis problemas em seu código. Ao habilitar os avisos, o Perl alertará sobre erros comuns e práticas questionáveis, permitindo que você os identifique e resolva antecipadamente.

```perl
use warnings;

# Seu código aqui
```

#### Escolhendo Bons Nomes de Variáveis

Escolher nomes de variáveis significativos e descritivos é importante para escrever um código de fácil manutenção. Bons nomes de variáveis melhoram a legibilidade do código e facilitam para os outros (incluindo você mesmo) entenderem o propósito das variáveis.

```perl
my $nome = "João";
my $idade = 25;
```

#### Atribuição Escalar

A atribuição escalar é usada para atribuir um valor a uma variável escalar usando o operador de atribuição (`=`). O valor do lado direito do operador é atribuído à variável do lado esquerdo.

```perl
my $nome = "João";
my $idade = 25;
```

#### Operadores de Atribuição Binária

O Perl fornece operadores de atribuição binária para realizar uma operação no valor atual de uma variável e atribuir o resultado de volta à variável. Esses operadores combinam uma operação aritmética ou de string com atribuição.

```perl
my $count = 10;
$count += 5;     # Equivalente a: $count = $count + 5

my $message = "Olá";
$message .= " Mundo!";   # Equivalente a: $message = $message . " Mundo!"
```

### Saída com print

A instrução `print` é usada para exibir texto ou valores no console ou em um arquivo. Ela permite mostrar informações ao usuário ou salvá-las para uso posterior.

#### Interpolação de Variáveis Escalares em Strings

Você pode interpolar variáveis escalares diretamente em strings entre aspas duplas, o que permite incluir seus valores dentro da string.

```perl
my $name = "João";
my $age = 25;
print "Meu nome é $name e tenho $age anos.";
```

#### Criação de Caracteres por Ponto de Código

Você pode criar caracteres pelos seus pontos de código Unicode usando a sequência de escape `\N{}` dentro de strings entre aspas duplas.

```perl
print "O símbolo do Euro é \N{U+20AC}.";
```

#### Precedência e Associatividade dos Operadores

Os operadores no Perl têm diferentes níveis de precedência, o que determina a ordem em que eles são avaliados. Você pode usar parênteses para substituir a precedência padrão e controlar a ordem das operações.

```perl
my $resultado = 2 + 3 * 4;    # Resultado: 14
my $resultado2 = (2 + 3) * 4; # Resultado: 20
```

#### Operadores de Comparação

Os operadores de comparação são usados para comparar valores e retornar um resultado booleano (`1` para verdadeiro, `0` para falso).

```perl
my $num1 = 10;
my $num2 = 5;

print $num1 > $num2;  # Saída: 1 (verdadeiro)
print $num1 == $num2; # Saída: 0 (falso)
```

### A Estrutura de Controle if

A estrutura de controle `if` é usada para executar código condicionalmente com base em uma expressão booleana. Ela permite tomar decisões e executar ações diferentes dependendo do resultado da condição.

```perl
my $num = 10;
if ($num > 5) {
    print "O número é maior que 5.";
} else {
    print "O número é menor ou igual a 5.";
}
```

#### Valores Booleanos

Em Perl, valores booleanos são representados por `1` para verdadeiro e `0` para falso. Operadores de comparação e lógicos retornam valores booleanos que podem ser usados em instruções condicionais.

```perl
my $num1 = 10;
my $num2 = 5;
my $is_greater = $num1 > $num2;  # $is_greater é 1 (verdadeiro)
```

### Obtendo Entrada do Usuário

Para obter entrada do usuário, você pode usar o operador de leitura de linha `<STDIN>`. Ele lê uma linha completa da entrada padrão (geralmente o teclado) e a atribui a uma variável.

```perl
print "Digite seu nome: ";
my $nome = <STDIN>;
chomp($nome);  # Remove o caractere de nova linha
print "Olá, $nome!";
```

### O Operador chomp

A função `chomp()` é usada para remover o caractere de nova linha do final de uma string. É comumente usada após a leitura de entrada do usuário para eliminar o caractere de nova linha.

```perl
print "Digite um valor: ";
my $valor = <STDIN>;
chomp($valor);  # Remove o caractere de nova linha
print "O valor que você digitou é: $valor";
```

### A Estrutura de Controle while

O loop `while` repete um bloco de código enquanto uma determinada condição for verdadeira. Ele permite que você execute tarefas iterativas e continue a execução até que a condição se torne falsa.

```perl
my $contador = 0;
while ($contador < 10) {
    $contador += 2;
    print "O contador agora é $contador\n";
}
```

### O Valor undef

Antes de atribuir um valor, as variáveis em Perl têm o valor especial `undef`, que indica a ausência de um valor. Ele pode agir como zero quando usado como número ou como uma string vazia quando usado como string.

```perl
my $num;
print $num;  # Saída: (nada)
$num = undef;
print $num;  # Saída: (nada)
```

### A Função defined

A função `defined()` é usada para determinar se uma variável possui um valor definido. Ela retorna verdadeiro se o valor estiver definido (não `undef`), e falso caso contrário.

```perl
my $valor;
if (defined($valor)) {
    print "A variável possui um valor definido.";
} else {
    print "A variável está indefinida.";
}
```
