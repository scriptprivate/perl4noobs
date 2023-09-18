## Entrada e Saída

### Entrada a partir da Entrada Padrão

Em Perl, você pode ler a entrada padrão (geralmente o teclado) usando o manipulador de arquivo `<STDIN>`. Aqui está um exemplo que lê uma linha de entrada do usuário:

```perl
print "Digite seu nome: ";
my $nome = <STDIN>;
chomp($nome); # Remove o caractere de nova linha
print "Olá, $nome!\n";
```

### Entrada a partir do Operador Diamante

O Operador Diamante (`<>`) é uma maneira conveniente de ler a entrada de arquivos especificados como argumentos da linha de comando ou da entrada padrão se nenhum arquivo for fornecido. Ele lê linhas de arquivos uma a uma. Aqui está um exemplo:

```perl
while (<>) {
    chomp; # Remove o caractere de nova linha
    print "Linha: $_\n";
}
```

Você pode executar este script com `perl script.pl arquivo.txt` para ler de um arquivo ou apenas `perl script.pl` para ler da entrada padrão.

### Os Argumentos de Invocação

Para acessar os argumentos da linha de comando passados para o seu script Perl, você pode usar o array `@ARGV`. Aqui está um exemplo que imprime todos os argumentos da linha de comando:

```perl
foreach my $arg (@ARGV) {
    print "Argumento: $arg\n";
}
```

Execute o script com `perl script.pl arg1 arg2 arg3`.

### Saída para a Saída Padrão

Você pode imprimir a saída na saída padrão (geralmente o terminal) usando a função `print`. Aqui está um exemplo simples:

```perl
print "Olá, mundo!\n";
```

### Saída Formatada com `printf`

A função `printf` permite formatar a saída usando espaços reservados. Você fornece uma string de formato com espaços reservados e valores a serem inseridos. Aqui está um exemplo:

```perl
my $nome = "Alice";
my $idade = 30;
printf("Nome: %s, Idade: %d\n", $nome, $idade);
```

#### Arrays e `printf`

`printf` pode formatar a saída para arrays, tornando-o útil para dados tabulares. Aqui está um exemplo que formata um array de nomes e idades:

```perl
my @nomes = ("Alice", "Bob", "Charlie");
my @idades = (30, 25, 35);

for my $i (0 .. $#nomes) {
    printf("Nome: %-10s Idade: %2d\n", $nomes[$i], $idades[$i]);
}
```

Neste exemplo, espaços reservados como `%s` e `%2d` controlam a formatação dos elementos do array.

### Manipuladores de Arquivo

Os manipuladores de arquivo em Perl são usados para operações de entrada e saída, permitindo que você leia e escreva em arquivos, bem como interaja com a entrada e saída padrão.

### Abrindo um Manipulador de Arquivo

Para abrir um arquivo para leitura ou escrita, você pode usar a função `open`. Aqui está um exemplo de abrir um arquivo para leitura:

```perl
open my $manipulador_arquivo, '<', 'exemplo.txt' or die "Não foi possível abrir o arquivo: $!";
```

#### Binmoding de Manipuladores de Arquivo

Binmoding de um manipulador de arquivo é importante ao trabalhar com dados binários. Você pode usar a função `binmode` para definir um manipulador de arquivo como modo binário:

```perl
binmode $manipulador_arquivo;
```

#### Manipuladores de Arquivo Inválidos

Manipuladores de arquivo inválidos podem ocorrer se a função `open` falhar ao abrir um arquivo. Você pode verificar o valor de retorno de `open` para lidar com manipuladores de arquivo inválidos adequadamente.

```perl
if (!open my $manipulador_arquivo, '<', 'inexistente.txt') {
    warn "Falha ao abrir o arquivo: $!";
}
```

#### Fechando um Manipulador de Arquivo

É essencial fechar um manipulador de arquivo quando você terminar de usá-lo para liberar recursos do sistema e garantir que os dados sejam gravados no arquivo. Use a função `close`:

```perl
close $manipulador_arquivo or die "Erro ao fechar o arquivo: $!";
```

### Erros Fatais com `die`

A função `die` em Perl é usada para gerar erros fatais e encerrar o programa. É comumente usada para tratamento de erros. Aqui está um exemplo de uso do `die` quando a abertura de um arquivo falha:

```perl
if (!open my $manipulador_arquivo, '<', 'exemplo.txt') {
    die "Não foi possível abrir o arquivo: $!";
}
```

#### Mensagens de Aviso com `warn`

Semelhante ao `die`, a função `warn` gera mensagens de aviso, mas não encerra o programa. É útil para erros não fatais ou problemas que você deseja relatar.

```perl
if (!open my $manipulador_arquivo, '<', 'inexistente.txt') {
    warn "Falha ao abrir o arquivo: $!";
}
```

#### `die` Automático

A praga `autodie`, disponível no Perl, permite que você invoque automaticamente `die` quando certas chamadas de sistema (por exemplo, `open`, `close`) falham. Simplifica o tratamento de erros:

```perl
use autodie;

open my $manipulador_arquivo, '<', 'exemplo.txt'; # Morre automaticamente em caso de falha
```

### Usando Manipuladores de Arquivo

Uma vez que um manipulador de arquivo está aberto, você pode ler e gravar dados usando várias funções e operadores Perl.

#### Alterando o Manipulador de Arquivo de Saída Padrão

Você pode alterar o manipulador de arquivo de saída padrão usando o operador `select`. Isso é útil quando você deseja direcionar a saída para um arquivo ou fluxo específico.

```perl
select $manipulador_arquivo; # Define $manipulador_arquivo como o manipulador de saída padrão
print "Isso vai para o manipulador de arquivo selecionado.\n";
select STDOUT;     # Retorna à saída padrão
print "Isso vai para a saída padrão.\n";
```

### Reabrindo um Manipulador de Arquivo Padrão

No Perl, é possível reabrir manipuladores de arquivo padrão (STDIN, STDOUT, STDERR) para red

irecionar sua entrada ou saída. Reabrir um manipulador de arquivo padrão pode ser útil para personalizar o comportamento de Entrada/Saída.

Para reabrir um manipulador de arquivo padrão, você pode usar a função `open`, especificando o manipulador de arquivo que deseja reabrir e o modo desejado. Por exemplo, para reabrir STDERR para anexar:

```perl
open STDERR, '>>', 'erros.log' or die "Não foi possível abrir o arquivo de erros: $!";
```

É importante observar que reabrir um manipulador de arquivo padrão fechará a conexão original com o fluxo padrão (por exemplo, STDERR) e a substituirá pela nova.

### Saída com `say`

A partir do Perl 5.10, a função `say` está disponível para simplificar as operações de saída. `say` é semelhante ao `print`, mas anexa automaticamente um caractere de nova linha ao final da saída.

Aqui está um exemplo de uso do `say` para imprimir uma saudação:

```perl
use 5.010; # Garanta Perl 5.10 ou superior

say "Olá, Mundo!";
```

A função `say` é especialmente conveniente quando você deseja produzir linhas de texto com uma nova linha sem adicionar explicitamente `"\n"`.

### Manipuladores de Arquivo em um Escalar

O Perl permite que você armazene manipuladores de arquivo em variáveis escalares, facilitando o gerenciamento e a passagem deles como argumentos para funções ou armazenamento em estruturas de dados. Isso é particularmente útil para controlar o escopo dos manipuladores de arquivo.

Aqui está um exemplo de abrir um arquivo e armazenar o manipulador de arquivo em uma variável escalar:

```perl
my $manipulador_arquivo;
open $manipulador_arquivo, '<', 'dados.txt' or die "Não foi possível abrir o arquivo de dados: $!";
```

Em seguida, você pode usar a variável escalar `$manipulador_arquivo` para operações de entrada ou saída subsequentes, assim como faria com um manipulador de arquivo de palavra-simbólica.

```perl
while (<$manipulador_arquivo>) {
    chomp;
    # Processar cada linha do arquivo
}
```

Manipuladores de arquivo em variáveis escalares fornecem uma melhor encapsulação e controle sobre operações de Entrada/Saída de arquivo, especialmente em programas Perl maiores.