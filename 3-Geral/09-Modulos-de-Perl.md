## Módulos Perl

Os módulos Perl são um aspecto fundamental da linguagem, fornecendo funcionalidades e recursos adicionais para aprimorar programas Perl.

### Encontrando Módulos

Para encontrar módulos Perl, a Rede Abrangente de Arquivos Perl (CPAN) é o recurso principal. O CPAN oferece uma vasta coleção de módulos que podem ser facilmente pesquisados e acessados. Você pode pesquisar por módulos no CPAN usando o seguinte comando em um shell ou PowerShell:

```shell
cpan Nome::Do::Módulo
```

### Instalando Módulos

A instalação de módulos do CPAN pode ser feita usando ferramentas como `cpan` ou `cpanm`. Essas ferramentas automatizam o processo de instalação, resolvendo dependências e buscando os módulos necessários. Aqui está um exemplo de instalação de um módulo usando o `cpan` em um shell ou PowerShell:

```shell
cpan Nome::Do::Módulo
```

#### Usando Seus Próprios Diretórios

Para usar seus próprios diretórios para instalar módulos Perl, você pode modificar o array `@INC` no Perl. Isso permite que você especifique diretórios personalizados onde o Perl deve procurar por módulos. Por exemplo, em um shell ou PowerShell, você pode definir a variável de ambiente `PERL5LIB` para incluir seus diretórios desejados:

```shell
export PERL5LIB=/caminho/para/meus/modulos:$PERL5LIB
```

### Usando Módulos Simples

O Perl fornece vários módulos simples que oferecem funcionalidades convenientes para tarefas específicas.

#### O Módulo File::Basename

O módulo `File::Basename` permite extrair o nome base e o caminho do diretório de um caminho de arquivo. Ele fornece funções como `basename()` e `dirname()` para esse propósito. Aqui está um exemplo de uso do `File::Basename` em Perl:

```perl
use File::Basename;

my $caminho = "/caminho/para/arquivo.txt";
my ($nome_arquivo, $diretorio) = fileparse($caminho);
print "Nome do Arquivo: $nome_arquivo\n";
print "Diretório: $diretorio\n";
```

#### Usando Apenas Algumas Funções de um Módulo

Você pode importar seletivamente funções específicas de um módulo usando a declaração `use`. Essa abordagem ajuda a reduzir a poluição do namespace e otimizar o código. Por exemplo, para importar apenas a função `basename()` do `File::Basename`, você pode usar o seguinte código:

```perl
use File::Basename qw(basename);

my $caminho = "/caminho/para/arquivo.txt";
my $nome_arquivo = basename($caminho);
print "Nome do Arquivo: $nome_arquivo\n";
```

#### O Módulo File::Spec

O módulo `File::Spec` fornece uma interface independente de plataforma para trabalhar com caminhos de arquivos. Ele permite manipular caminhos de arquivos usando funções como `catfile()`, `catdir

()` e `splitpath()`. Aqui está um exemplo de uso do `File::Spec` para juntar nomes de diretório e arquivo:

```perl
use File::Spec;

my $diretorio = "/caminho/para/diretorio";
my $arquivo = "arquivo.txt";
my $caminho = File::Spec->catfile($diretorio, $arquivo);
print "Caminho: $caminho\n";
```

#### Path::Class

O módulo `Path::Class` oferece uma interface aprimorada para trabalhar com caminhos de arquivos. Ele fornece métodos intuitivos como `dir()`, `subdir()` e `as_foreign()` para manipulação eficiente de caminhos de arquivos. Aqui está um exemplo de uso do `Path::Class` para criar caminhos de diretório e arquivo:

```perl
use Path::Class;

my $diretorio = dir("caminho", "para", "diretorio");
my $arquivo = $diretorio->file("arquivo.txt");
print "Diretório: $diretorio\n";
print "Arquivo: $arquivo\n";
```

#### CGI.pm

O módulo `CGI.pm` simplifica o processo de criação de programas CGI, fornecendo uma interface fácil de usar para lidar com a entrada CGI e gerar HTML. Ele oferece funções como `param()`, `header()` e `start_html()`. Aqui está um exemplo de uso do `CGI.pm` para recuperar parâmetros CGI:

```perl
use CGI;

my $cgi = CGI->new();
my @params = $cgi->param();
foreach my $param (@params) {
    my $value = $cgi->param($param);
    print "$param: $value\n";
}
```

#### Bancos de Dados e DBI

O módulo `DBI` (Interface de Banco de Dados) é amplamente usado para se conectar a vários servidores de banco de dados. Ele permite o uso de uma interface consistente, independentemente do tipo de banco de dados. Os módulos `DBD` (Drivers de Banco de Dados) fornecem suporte para bancos de dados específicos. Aqui está um exemplo de conexão a um banco de dados usando o `DBI`:

```perl
use DBI;

my $dbh = DBI->connect("dbi:mysql:database=nomedobanco;host=localhost", "usuario", "senha");
```

#### Datas e Horários

Para lidar com datas e horários, o módulo `DateTime` é uma solução abrangente em Perl. Ele lida com fusos horários, cálculos de datas e formatação. Você pode criar objetos `DateTime`, realizar cálculos de datas e formatar datas usando métodos como `from_epoch()`, `ymd()` e operadores aritméticos. Aqui está um exemplo de criação de um objeto `DateTime` e formatação da data:

```perl
use DateTime;

my $dt = DateTime->from_epoch(epoch => time);
print $dt->ymd('-'); # Saída: 2023-05-24
```

Se você preferir uma abordagem mais simples, o módulo `Time::Piece` oferece métodos convenientes para representar o tempo como objetos. Ele fornece métodos para acessar partes da data e formatar strings de tempo. Aqui está um exemplo de acesso ao mês usando `Time::

Piece`:

```perl
use Time::Piece;

my $t = localtime;
print "O mês é " . $t->month . "\n"; # Saída: O mês é Maio
```
