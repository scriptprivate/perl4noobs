# Cheatsheet

## Sumário

1. [Comentários](#comentários)
2. [Variáveis](#variáveis)
3. [Tipos de Dados](#tipos-de-dados)
4. [Operadores](#operadores)
5. [Estruturas de Controle](#estruturas-de-controle)
6. [Sub-rotinas](#sub-rotinas)
7. [Arrays](#arrays)
8. [Hashes](#hashes)
9. [Manipulação de Arquivos](#manipulação-de-arquivos)
10. [Expressões Regulares](#expressões-regulares)
11. [Módulos](#módulos)
12. [Tratamento de Erros](#tratamento-de-erros)
13. [Diversos](#diversos)

---

## 1. Comentários

```perl
# Este é um comentário de uma linha

=begin
Este é um
comentário de
múltiplas linhas
=cut
```

## 2. Variáveis

### Variáveis Escalares

```perl
my $variavel_escalar = "Olá, Perl!";
```

### Variáveis de Array

```perl
my @variavel_array = (1, 2, 3);
```

### Variáveis de Hash

```perl
my %variavel_hash = ('chave1' => 'valor1', 'chave2' => 'valor2');
```

## 3. Tipos de Dados

- Escalar: `$`, por exemplo, `$nome`
- Array: `@`, por exemplo, `@números`
- Hash: `%`, por exemplo, `%dados`
- String: Entre aspas simples ou duplas
- Numérico: Números inteiros e de ponto flutuante

## 4. Operadores

- Aritméticos: `+`, `-`, `*`, `/`, `%`
- Comparação: `==`, `!=`, `<`, `>`, `<=`, `>=`
- Lógicos: `&&`, `||`, `!`
- Concatenação de Strings: `.`

## 5. Estruturas de Controle

### Declarações Condicionais

```perl
if (condição) {
    # bloco de código
} elsif (outra_condição) {
    # bloco de código
} else {
    # bloco de código
}
```

### Loops

- Loop `for`:

```perl
for (my $i = 0; $i < 5; $i++) {
    # bloco de código
}
```

- Loop `foreach` (Array):

```perl
foreach my $elemento (@array) {
    # bloco de código
}
```

- Loop `while`:

```perl
while (condição) {
    # bloco de código
}
```

- Loop `until`:

```perl
until (condição) {
    # bloco de código
}
```

## 6. Sub-rotinas

```perl
sub saudacao {
    my ($nome) = @_;
    print "Olá, $nome!\n";
}

saudacao("Alice");
```

## 7. Arrays

### Operações Básicas com Arrays

- Acessando Elementos: `$array[0]`
- Tamanho: `scalar @array`
- Adicionando Elementos: `push @array, $elemento`
- Removendo Elementos: `pop @array`
- Fatiando: `@slice = @array[1..3]`

## 8. Hashes

### Operações Básicas com Hashes

- Acessando Elementos: `$hash{'chave'}`
- Chaves: `keys %hash`
- Valores: `values %hash`
- Verificando Existência: `exists $hash{'chave'}`
- Deletando Elementos: `delete $hash{'chave'}`

## 9. Manipulação de Arquivos

```perl
# Abrindo um Arquivo
open(my $handle_arquivo, '<', 'nome_arquivo.txt') or die "Erro: $!";

# Lendo de um Arquivo
while (my $linha = <$handle_arquivo>) {
    # processar $linha
}

# Escrevendo em um Arquivo
open(my $arquivo_saida, '>', 'saida.txt') or die "Erro: $!";
print $arquivo_saida "Olá, Arquivo!\n";
close($arquivo_saida);
```

## 10. Expressões Regulares

```perl
my $texto = "Olá, Perl!";
if ($texto =~ /Perl/) {
    print "Correspondência encontrada!\n";
}

# Grupos de Captura
if ($texto =~ /(\w+), (\w+)/) {
    my $primeiro_nome = $1;
    my $último_nome = $2;
    print "Primeiro Nome: $primeiro_nome, Último Nome: $último_nome\n";
}
```

## 11. Módulos

```perl
use Nome::Módulo;

# Usando funções do módulo
Nome::Módulo::nome_função();
```

## 12. Tratamento de Erros

```perl
eval {
    # código que pode lançar uma exceção
    die "Erro!";
};
if ($@) {
    # lidar com a exceção
    print "Ocorreu um erro: $@\n";
}
```

## 13. Diversos

- Variáveis Especiais: `$_`, `@ARGV`, `$0`, `$$/`, `$|`, `$!`
- Classificando Arrays: `sort @array`
- Comandos de Sistema: `system`, `qx//`

---

Este resumo fornece uma referência rápida aos conceitos essenciais de programação em Perl e à sua sintaxe. Utilize-o como guia para suas tarefas de script e programação em Perl.