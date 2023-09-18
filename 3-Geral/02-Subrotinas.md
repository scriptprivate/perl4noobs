## Subrotinas

Subrotinas em Perl são usadas para agrupar blocos de código que podem ser reutilizados e chamados de diferentes partes de um programa. Elas permitem uma melhor organização de código, modularidade e reutilização.

### Definindo uma Subrotina

Em Perl, as subrotinas são definidas usando a palavra-chave `sub`, seguida pelo nome da subrotina e um bloco de código entre chaves. Parâmetros podem ser definidos entre parênteses após o nome da subrotina.

Exemplo:
```perl
sub cumprimentar {
    my ($nome) = @_;
    print "Olá, $nome!\n";
}
```

### Invocando uma Subrotina

Para invocar ou chamar uma subrotina, você pode simplesmente usar seu nome seguido de parênteses. Argumentos podem ser passados dentro dos parênteses se a subrotina esperar parâmetros.

Exemplo:
```perl
cumprimentar("João");
```

### Valores de Retorno

Subrotinas em Perl podem retornar valores usando a instrução `return`. O valor retornado pode ser atribuído a uma variável ou usado diretamente em uma expressão.

Exemplo:
```perl
sub somar_numeros {
    my ($a, $b) = @_;
    return $a + $b;
}

my $soma = somar_numeros(5, 3);
print "Soma: $soma\n";
```

### Argumentos

Subrotinas em Perl podem aceitar argumentos passados pelo código que as chama. Esses argumentos são acessíveis dentro da subrotina usando variáveis especiais como `@_`.

Exemplo:
```perl
sub cumprimentar {
    my ($nome) = @_;
    print "Olá, $nome!\n";
}

cumprimentar("João");
```

No exemplo acima, a subrotina `cumprimentar` recebe um parâmetro `$nome` e imprime uma mensagem de cumprimento usando esse parâmetro.

### Variáveis Privadas em Subrotinas

Em Perl, você pode criar variáveis privadas dentro de subrotinas usando a palavra-chave `my`. Essas variáveis são locais à subrotina e mantêm seus valores entre as chamadas da subrotina.

Exemplo:
```perl
sub contador {
    my $contagem = 0;
    $contagem++;
    print "Contagem: $contagem\n";
}

contador();
contador();
```

No exemplo acima, a subrotina `contador` usa uma variável privada `$contagem` para acompanhar a contagem. A variável é inicializada com 0 na primeira chamada e incrementada em 1 a cada chamada subsequente.

### Listas de Parâmetros de Comprimento Variável

Subrotinas em Perl podem aceitar listas de parâmetros de comprimento variável, permitindo flexibilidade no número de argumentos passados.

#### Uma Melhor Rotina &max
Exemplo:
```perl
sub max {
    my $valor_maximo = shift @_;
    foreach my $numero (@_) {
        $valor_maximo = $numero if $numero > $valor_maximo;
    }
    return $valor_maximo;
}

my $maximo = max(10, 5, 8, 15, 3);
print "Máximo: $maximo\n";
```

A subrotina `max` recebe um número variável de argumentos e retorna o valor máximo entre eles.

#### Listas de Parâmetros Vazias

Subrotinas em Perl também podem lidar com listas de parâmetros vazias, permitindo comportamentos diferentes com base na presença ou ausência de argumentos.

Exemplo:
```perl
sub cumprimentar {
    my ($nome) = @_;
    if ($nome) {
        print "Olá, $nome!\n";
    } else {
        print "Olá, anônimo!\n";
    }
}

cumprimentar("João");
cumprimentar();
```

No exemplo acima, a subrotina `cumprimentar` verifica se o parâmetro `$nome` está definido. Se estiver, ela cumprimenta a pessoa pelo nome. Caso contrário, ela cumprimenta como "anônimo" quando nenhum argumento é fornecido.

### Observações sobre Variáveis Léxicas (my)

Variáveis léxicas, declaradas usando a palavra-chave `my`, possuem um escopo restrito e são acessíveis apenas dentro do bloco de código onde são definidas.

Exemplo:
```perl
sub calcular_media {
    my $soma = 0;
    my $contagem = 0;
    foreach my $numero (@_) {
        $soma += $numero;
        $contagem++;
    }
    my $media = $soma / $contagem;
    return $media;
}

my $media = calcular_media(5, 10, 15);
print "Média: $media\n";
```

No exemplo acima, as variáveis `$soma`, `$contagem` e `$media` são variáveis léxicas definidas dentro da subrotina `calcular_media`. Elas não são acessíveis fora da subrotina.

### O pragma use strict

O pragma `use strict` é usado para impor regras de escopo de variáveis mais rigorosas em programas Perl. Ele ajuda a identificar possíveis erros e incentiva boas práticas de programação.

Exemplo:
```perl
use strict;

sub multiplicar {
    my ($a, $b) = @_;
    return $a * $b;
}

my $resultado = multiplicar(2, 3);
print "Resultado: $resultado\n";
```

No exemplo acima, o pragma `use strict` é habilitado no início do script, garantindo que as variáveis sejam declaradas antes de serem usadas. Isso ajuda a identificar problemas potenciais, como o uso de variáveis não declaradas.

### O operador return

O operador `return` é usado para retornar explicitamente um valor de uma subrotina. Ele pode ser usado com ou sem parênteses para retornar um único valor ou uma lista de valores, respectivamente.

Exemplo:
```perl
sub obter_nome {
    my $nome = "João";
    return $nome;
}

my $nome = obter_nome();
print "Nome: $nome\n";
```

No exemplo acima, a subrotina `obter_nome` retorna o valor da variável `$nome` usando a instrução `return`. O valor retornado é então atribuído à variável `$nome` fora da subrotina.

#### Omitindo o Ampersand

Em Perl, é comum omitir o ampersand (`&`) ao chamar subrotinas, especialmente quando não há ambiguidade. Essa convenção melhora a legibilidade do código.

Exemplo:
```perl
sub cumprimentar {
    my ($nome) = @_;
    print "Olá, $nome!\n";
}

cumprimentar("João");
```

No exemplo acima, a subrotina `cumprimentar` é chamada sem usar o ampersand (`&`) antes do seu nome. Essa é a abordagem recomendada e mais comumente usada na programação Perl moderna.

### Valores de Retorno Não Escalares

Subrotinas em Perl podem retornar valores não escalares, como listas ou referências.

Exemplo:
```perl
sub obter_nomes {
    my @nomes = ("João", "Maria", "Alice");
    return @nomes;
}

my @pessoas = obter_nomes();
foreach my $pessoa (@pessoas) {
    print "Pessoa: $pessoa\n";
}
```

No exemplo acima, a subrotina `obter_nomes` retorna um array de nomes. O array retornado é atribuído a `@pessoas`, que é então iterado para imprimir o nome de cada pessoa.

### Variáveis Persistentes e Privadas

Em Perl, é possível criar variáveis persistentes e privadas dentro de subrotinas usando a palavra-chave `state` do módulo `state`. Essas variáveis mantêm seus valores entre chamadas subsequentes da subrotina, assim como as variáveis privadas, mas seus valores persistem em múltiplas invocações da subrotina.

Exemplo:
```perl
use state;

sub contador {
    state $contagem = 0;
    $contagem++;
    print "Contagem: $contagem\n";
}

contador();
contador();
```

No exemplo acima, a variável `state` `$contagem` mantém seu valor entre chamadas subsequentes da subrotina `contador`.
