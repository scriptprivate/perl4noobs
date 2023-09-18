## Hashes

Hashes são estruturas de dados fundamentais em Perl que armazenam dados como pares de chave-valor. Eles fornecem maneiras eficientes e flexíveis de organizar e acessar dados.

### O que é um Hash?

Um hash é uma coleção não ordenada de pares de chave-valor. As chaves são únicas e usadas para recuperar os valores correspondentes de forma eficiente. Em Perl, hashes são representados pelo símbolo `%`.

#### Por que usar um Hash?

- Hashes permitem uma busca rápida e recuperação de dados usando chaves.
- Eles fornecem uma maneira conveniente de representar informações estruturadas e relacionamentos.
- Hashes são adequados para cenários onde os dados precisam ser acessados e atualizados com frequência.

### Acesso aos Elementos de um Hash

Hashes em Perl oferecem vários métodos para acessar e manipular seus elementos.

#### O Hash como um Todo

Para acessar o hash inteiro, você pode usar a variável do hash precedida pelo símbolo `%`. Isso permite iterar sobre todos os pares de chave-valor ou realizar operações no hash como um todo.

```perl
foreach my $chave (keys %hash) {
    my $valor = $hash{$chave};
    # Realizar operações com $chave e $valor
}
```

#### Atribuição de Hash

Para atribuir valores a chaves específicas em um hash, você usa a variável do hash seguida da chave entre chaves `{}`. O operador de atribuição `=` é usado para definir o valor para a chave correspondente.

```perl
$hash{"chave"} = "valor";
```

#### A "Seta Grande"

A "seta grande" ou operador `=>` é um açúcar sintático comumente usado para atribuir valores às chaves em um hash. Ele fornece uma maneira visualmente clara de associar chaves aos seus valores.

```perl
my %hash = (
    chave1 => "valor1",
    chave2 => "valor2",
);
```

O operador `=>` é equivalente ao uso de uma vírgula `,` entre a chave e o valor na atribuição do hash.

```perl
my %hash = (
    "chave1", "valor1",
    "chave2", "valor2",
);
```

Ao usar a seta grande, o código fica mais legível e se assemelha a um relacionamento de chave-valor.

O entendimento do acesso e manipulação de elementos de um hash em Perl permite o armazenamento e a recuperação eficientes de dados usando pares de chave-valor. Utilizar o hash como um todo, atribuir valores usando a seta grande e acessar elementos individuais fornecem as habilidades necessárias para trabalhar com hashes de forma eficaz.

### Funções de Hash

Em Perl, as funções de hash fornecem maneiras convenientes de interagir e manipular dados em um hash.

#### As funções `keys` e `values`

As funções `keys` e `values` permitem extrair as chaves e os valores de um hash, respectivamente.

```perl
my %hash = (
    chave1 => "valor1",
    chave2 => "valor2",
);

# Extraindo as chaves usando a função keys
my

 @chaves = keys %hash;

# Extraindo os valores usando a função values
my @valores = values %hash;
```

A função `keys` retorna um array contendo todas as chaves do hash, enquanto a função `values` retorna um array contendo todos os valores correspondentes.

#### A função `each`

A função `each` facilita a iteração sobre um hash, retornando pares de chave-valor como uma lista de dois elementos.

```perl
my %hash = (
    chave1 => "valor1",
    chave2 => "valor2",
);

while (my ($chave, $valor) = each %hash) {
    print "$chave => $valor\n";
}
```

A função `each` retorna o próximo par de chave-valor em cada iteração até que todos os elementos tenham sido acessados.

### Uso Típico de um Hash

Hashes são comumente usados para diversos fins devido à sua versatilidade e eficiência.

#### A função `exists`

A função `exists` verifica se uma chave específica existe em um hash.

```perl
my %hash = (
    chave1 => "valor1",
    chave2 => "valor2",
);

if (exists $hash{"chave1"}) {
    print "A chave 'chave1' existe no hash.\n";
}
```

A função `exists` retorna um valor verdadeiro se a chave especificada estiver presente no hash.

#### A função `delete`

A função `delete` remove um par de chave-valor de um hash.

```perl
my %hash = (
    chave1 => "valor1",
    chave2 => "valor2",
);

delete $hash{"chave1"};
```

A função `delete` elimina o par de chave-valor associado à chave especificada do hash.

#### Interpolação de Elementos de Hash

Elementos de um hash podem ser interpolados em strings usando a sintaxe apropriada.

```perl
my %hash = (
    nome => "Fulano de Tal",
    idade => 30,
);

print "Nome: $hash{nome}\n";
print "Idade: $hash{idade}\n";
```

Ao envolver o elemento do hash em chaves dentro de uma string, o valor correspondente pode ser interpolado.

### O Hash `%ENV`

Perl fornece o hash `%ENV` para acessar e manipular variáveis de ambiente.

```perl
print "O PATH é $ENV{PATH}\n";
```

O hash `%ENV` contém os nomes das variáveis de ambiente como chaves e seus valores correspondentes.
