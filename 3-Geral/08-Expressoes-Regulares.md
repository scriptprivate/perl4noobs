## Expressões Regulares

Expressões regulares, frequentemente chamadas de padrões em Perl, são modelos poderosos usados para corresponder ou não corresponder a strings. Elas dividem um conjunto infinito de strings de texto possíveis em dois grupos: aquelas que correspondem ao padrão e aquelas que não correspondem.

### Quantificadores

Os quantificadores em expressões regulares especificam quantas vezes um item pode corresponder em um padrão. Aqui estão alguns quantificadores comuns:
- `+`: Corresponde a uma ou mais ocorrências.
Exemplo:
```perl
if ($texto =~ /Perl.+/) {
    print "Encontrado texto relacionado ao Perl.\n";
}
```

- `*`: Corresponde a zero ou mais ocorrências.
Exemplo:
```perl
if ($texto =~ /maçã*/) {
    print "Encontrado 'maçã' ou 'maçãa', etc.\n";
}
```

- `?`: Corresponde a zero ou uma ocorrência (opcional).
Exemplo:
```perl
if ($texto =~ /cor?/) {
    print "Encontrado 'cor' ou 'corre'.\n";
}
```

### Correspondência Mínima

Para realizar correspondência não gananciosa, você pode usar `*?` ou `+?` após um quantificador. Isso faz com que o padrão corresponda o mínimo possível.
Exemplo:
```perl
if ($texto =~ /<.*?>/) {
    print "Encontrada tag HTML mínima.\n";
}
```

### Fixando as Coisas

Âncoras em expressões regulares restringem onde um padrão pode corresponder em uma string.
- `\b`: Corresponde a uma fronteira de palavra.
Exemplo:
```perl
if ($texto =~ /\bPerl\b/) {
    print "Encontrada a palavra 'Perl'.\n";
}
```

- `^`: Corresponde ao início de uma linha/string.
Exemplo:
```perl
if ($texto =~ /^Começo/) {
    print "A string começa com 'Começo'.\n";
}
```

- `$`: Corresponde ao final de uma linha/string.
Exemplo:
```perl
if ($texto =~ /Fim$/) {
    print "A string termina com 'Fim'.\n";
}
```

### Retroreferências

Retroreferências são usadas para capturar e lembrar partes de um padrão de regex para uso posterior. Elas são representadas por `\1`, `\2`, etc., no padrão e podem ser acessadas como `$1`, `$2`, etc., no código Perl.
Exemplo:
```perl
if ($texto =~ /(\d+)-(\d+)/) {
    my $inicio = $1;
    my $fim = $2;
    print "Intervalo: $inicio a $fim\n";
}
```

### Processamento de Listas

O Perl permite um processamento de listas versátil com operadores como `sort`, `print` e `map`. Esses operadores fornecem contexto de lista e funcionam em arrays e listas de forma eficiente.
Exemplo:
```perl
my @numeros = (4, 2, 7, 1, 9);
my @numeros_ordenados = sort @numeros;
print "Números ordenados: @numeros_ordenados\n";
```

### Usando Padrões Simples

Para corresponder a um padrão em uma string no Perl, coloque o padrão entre barras (/). Padrões simples são sequências de caracteres literais. Exemplo:

```perl
$_ = "yabba dabba doo";
if (/abba/) {
    print "Correspondeu!\n";
}
```

#### Propriedades Unicode

Caracteres Unicode têm propriedades, e você pode corresponder a caracteres com base nessas propriedades. Use `\p{PROPRIEDADE}` para corresponder a caracteres com uma propriedade específica. Exemplo:

```perl
if (/\p{Espaço}/) {
    print "A string tem algum espaço em branco.\n";
}
```

#### Sobre Metacaracteres

Metacaracteres são caracteres especiais em expressões regulares. O ponto (.) é um caractere curinga que corresponde a qualquer caractere, exceto uma quebra de linha. Você pode escapar metacaracteres com uma barra invertida para correspondê-los literalmente. Exemplo:

```perl
$_ = 'uma barra invertida real \\';
if (/\\/) {
    print "Correspondeu!\n";
}
```

#### Quantificadores Simples

Quantificadores especificam quantas vezes o item precedente deve se repetir. O asterisco (*) corresponde a zero ou mais vezes, o mais (+) corresponde a uma ou mais vezes, e o ponto de interrogação (?) corresponde a zero ou uma vez. Exemplos:

```perl
if (/fred\t*barney/) {
    print "Corresponde a uma ou mais guias entre fred e barney.\n";
}
```

#### Agrupamento em Padrões

Use parênteses para agrupar partes de um padrão. Isso permite que você repita ou se refira a partes específicas da string correspondida. Exemplos:

```perl
if (/y(.)(.)\2\1/) {
    print "Correspondeu a um palíndromo após o 'y'!\n";
}
```

#### Alternativas

A barra vertical (|) em um padrão representa um operador OU, permitindo que o lado esquerdo ou direito corresponda. Exemplo:

```perl
if (/fred|barney|betty/) {
    print "Corresponde a strings contendo fred, barney ou betty.\n";
}
```

### Classes de Caracteres

Em expressões regulares Perl, classes de caracteres permitem especificar um conjunto de caracteres que você deseja corresponder. Elas são colocadas entre colchetes `[]`. Uma classe de caracteres corresponde a qualquer caractere único do conjunto definido dentro dos colchetes.

#### Atalhos para Classes de Caracteres

O Perl fornece atalhos para definir classes de caracteres comuns:

- `\d`: Corresponde a qualquer dígito (equivalente a `[0-9]`).
- `\D`: Corresponde a qualquer caractere não dígito (equivalente a `[^0-9]`).
- `\w`: Corresponde a qualquer caractere de palavra (alfanumérico e sublinhado, equivalente a `[a-zA-Z0-9_]`).
- `\W`: Corresponde a qualquer caractere que não seja de palavra (equivalente a `[^a-zA-Z0-9_]`).
- `\s`: Corresponde a qualquer caractere de espaço em branco (espaços, guias, quebras de linha).


- `\S`: Corresponde a qualquer caractere que não seja de espaço em branco.

Exemplos:

```perl
if ("123" =~ /\d{3}/) {
    print "Correspondeu a três dígitos.\n";
}

if ("Olá Mundo" =~ /\w{5}/) {
    print "Correspondeu a cinco caracteres de palavra.\n";
}
```

#### Negando os Atalhos

Você pode negar os atalhos de classes de caracteres capitalizando o atalho. Por exemplo, `\D` corresponde a qualquer caractere não dígito.

Exemplos:

```perl
if ("abc" =~ /\D/) {
    print "Correspondeu a um caractere não dígito.\n";
}

if ("123" =~ /\D/) {
    print "Isso não corresponderá porque não há caracteres não dígitos.\n";
}
```

## Correspondência com Expressões Regulares

### Correspondências com m//

Expressões regulares, frequentemente referidas como regex ou regexp, fornecem uma ferramenta poderosa para corresponder a padrões no Perl. A maneira mais comum de usar expressões regulares no Perl é com o operador `m//`. Isso permite que você pesquise padrões dentro de strings.

```perl
if ($texto =~ m/padrão/) {
    # Correspondeu a 'padrão' em $texto
}
```

### Modificadores de Correspondência

Expressões regulares no Perl podem ser aprimoradas com vários modificadores para alterar seu comportamento. Esses modificadores são colocados após o operador `m//`.

#### Correspondência Insensível a Maiúsculas e Minúsculas com /i

O modificador `/i` torna a correspondência de padrões insensível a maiúsculas e minúsculas. Isso permite corresponder a caracteres maiúsculos e minúsculos de forma intercambiável.

```perl
if ($texto =~ m/padrão/i) {
    # Correspondeu a 'padrão' (insensível a maiúsculas e minúsculas) em $texto
}
```

#### Correspondência de Qualquer Caractere com /s

O modificador `/s`, também conhecido como modificador "dot-all", permite que o ponto `.` corresponda a qualquer caractere, incluindo caracteres de quebra de linha (`\n`).

```perl
if ($texto =~ m/.+/s) {
    # Correspondeu a um ou mais caracteres (incluindo quebras de linha) em $texto
}
```

#### Adicionando Espaços em Branco com /x

O modificador `/x` permite que você adicione espaços em branco e comentários ao seu padrão de regex para melhor legibilidade. Ele ignora espaços em branco dentro do padrão.

```perl
if ($texto =~ m/  padrão  /x) {
    # Correspondeu a 'padrão' com espaços extras em $texto
}
```

#### Combinando Modificadores de Opção

Você pode combinar vários modificadores para criar comportamentos de correspondência complexos. Por exemplo, `/is` permite a correspondência insensível a maiúsculas e minúsculas e a correspondência de qualquer caractere.

```perl
if ($texto =~ m/padrão/is) {
    # Correspondeu a 'padrão' (insensível a maiúsculas e minúsculas e qualquer caractere) em $texto
}
```

#### Escolhendo uma Interpretação de Caractere

O Perl permite que você escolha a interpretação de caractere com modificadores como `/a`, `/l`, `/u`, `/d`, `/w` e `/p`, dependendo de seus requisitos específicos.

```perl
if ($texto =~ m/\p{Grego}/u) {
    # Correspondeu a caracteres gregos em $texto (modo Unicode)
}
```

### Outras Opções

As expressões regulares no Perl oferecem opções e recursos adicionais, como:
- **Grupos de Captura:** Use parênteses para capturar partes de uma string correspondida.
- **Capturas Nomeadas:** Rotule grupos de captura para melhor legibilidade e recuperação mais fácil.
- **Parênteses Não Capturadores:** Use `(?: ... )` para agrupar sem capturar.
- **Quantificadores Gerais:** Especifique o número de repetições com `{n,m}` ou `{n,}`.

### Âncoras

Âncoras em expressões regulares são usadas para especificar a posição dentro de uma string onde uma correspondência deve ocorrer. Elas ajudam a definir os limites de um padrão.

#### Âncoras de Palavra

Âncoras de palavra `\b` e `\B` são usadas para corresponder aos limites de palavras em uma string. `\b` corresponde à posição entre um caractere de palavra (alfanumérico ou sublinhado) e um caractere que não é de palavra, enquanto `\B` corresponde ao oposto.

```perl
if ($texto =~ m/\bpalavra\b/) {
    # Correspondeu a 'palavra' como uma palavra completa em $texto
}
```

### O Operador de Ligação =~

O operador `=~` no Perl é usado para aplicar um padrão de expressão regular a uma string. Ele vincula o padrão à string e permite realizar operações de correspondência.

```perl
if ($texto =~ m/padrão/) {
    # Correspondeu a 'padrão' em $texto
}
```

### Interpolação em Padrões

Você pode interpolar variáveis e expressões em padrões de expressão regular, permitindo criar padrões dinâmicos com base em valores em tempo de execução.

```perl
my $padrão = "dinâmico";
if ($texto =~ m/$padrão/) {
    # Correspondeu ao padrão gerado dinamicamente em $texto
}
```

A interpolação também funciona com outros recursos, como grupos de captura e modificadores, proporcionando flexibilidade na criação de padrões.

```perl
my $palavra_de_pesquisa = "maçã";
if ($texto =~ m/\b($palavra_de_pesquisa)\b/i) {
    # Correspondeu a 'maçã' como uma palavra completa (insensível a maiúsculas e minúsculas) em $texto
}
```

### As Variáveis de Correspondência

As variáveis de correspondência nas expressões regulares do Perl contêm partes de uma string correspondida e desempenham um papel crucial na extração de informações específicas de dados de texto.

#### A Persistência das Capturas

Variáveis de captura no Perl, representadas como $1, $2, etc., persistem após uma correspond

ência bem-sucedida do padrão. Elas mantêm partes da string original correspondida pelos grupos de captura correspondentes dentro dos parênteses.

Exemplo:
```perl
my $texto = "Tenho 3 maçãs e 2 laranjas.";
if ($texto =~ /(\d+) maçãs? e (\d+) laranjas?/) {
    print "Eu tenho $1 maçãs e $2 laranjas.\n"; # Extrai as quantidades capturadas
}
```

#### Parênteses Não Capturadores

Parênteses não capturadores, representados como `(?:...)`, são usados para agrupar elementos em um padrão sem criar variáveis de captura. Eles evitam mudanças não intencionais na numeração das variáveis de captura ao adicionar agrupamento.

Exemplo:
```perl
if ($texto =~ /(?:Sr\.|Sra\.) (\w+)/) {
    print "Nome: $1\n"; # Extrai o nome sem criar uma captura desnecessária
}
```

#### Capturas Nomeadas

Capturas nomeadas em expressões regulares permitem que você rotule grupos de captura para facilitar a referência e a clareza. Use a sintaxe `(?<RÓTULO>...)` para nomear as capturas.

Exemplo:
```perl
if ($texto =~ /(?<quantidade>\d+) (?<item>\w+)/) {
    print "Você tem $+{quantidade} $+{item}s.\n"; # Acesse os valores capturados pelo nome
}
```

#### As Variáveis de Combinação Automáticas

O Perl fornece três variáveis automáticas de combinação: ```$&, $`, e $'```. Elas contêm partes da string correspondida por um padrão de expressão regular.

Exemplo:
```perl
if ($texto =~ /padrão/) {
    print "Correspondido: $&\n";
    print "Antes: $`\n";
    print "Depois: $'\n";
}
```

### Quantificadores Gerais

Quantificadores em expressões regulares especificam quantas vezes o item precedente deve ser repetido. Eles incluem *, +, ?, e {n,m}, permitindo correspondência de padrões flexíveis.

Exemplo:
```perl
if ($texto =~ /a{2,4}/) {
    print "Correspondido 'aa', 'aaa', ou 'aaaa'.\n"; # Corresponde de 2 a 4 'a's consecutivos
}
```

### Precedência

A precedência em expressões regulares refere-se à hierarquia de operadores e construções, determinando como eles interagem dentro de um padrão. Compreender a precedência ajuda a esclarecer como padrões complexos são avaliados.

#### Exemplos de Precedência

A precedência desempenha um papel vital na definição de como os padrões de expressão regular são interpretados. Vamos explorar alguns exemplos para entender como diferentes elementos de um padrão interagem:

##### Parênteses (Agrupamento e Captura)

```perl
if ($texto =~ /(abc)+/) {
    print "Correspondido: $&\n"; # Corresponde a 'abcabc' ou mais repetições
}
```

##### Quantificadores

```perl
if ($texto =~ /a{2,4}/) {
    print "Correspondido 'aa', 'aaa', ou 'aaaa'.\n"; # Corresponde de 2 a 4 'a's consecutivos
}
```

##### Âncoras e Sequência

```perl
if ($texto =~ /^\w+$/) {
    print "Correspondido uma palavra ancorada em ambas as extremidades.\n";
}
```

##### Alternância

```perl
if ($texto =~ /maçã|banana/) {
    print "Correspondido 'maçã' ou 'banana'.\n"; # A alternância divide o padrão
}
```

#### E Tem Mais

Embora tenhamos abordado tópicos essenciais em expressões regulares, existem recursos e opções avançadas adicionais para explorar. Isso inclui visualizações antecipadas (look-aheads), visualizações retrospectivas (look-behinds) e muito mais, permitindo correspondência e manipulação de padrões complexos. Consulte a documentação para obter detalhes completos.

### Um Programa de Teste de Padrões

Um programa de teste de padrões ajuda os desenvolvedores a experimentar com expressões regulares para entender melhor o seu comportamento. Este script Perl lê linhas de entrada, testa-as contra um padrão especificado e fornece feedback visual sobre correspondências.

```perl
#!/usr/bin/perl
while (<>) {
    chomp;
    if (/SEU_PADRÃO_AQUI/) {
        print "Correspondido: |$`<$&>$'|\n"; # Mostra as partes correspondidas no contexto
    } else {
        print "Sem correspondência: |$_|\n";
    }
}
```

## Processamento de Texto com Expressões Regulares

### Substituições com s///

No Perl, o operador `s///` é usado para substituições de strings. Ele permite encontrar e substituir padrões de texto em uma string.

#### Substituições Globais com /g

O modificador `/g` é usado com `s///` para realizar uma substituição global, o que significa que ele substitui todas as ocorrências do padrão na string.

```perl
my $texto = "Isto é um teste. É um teste simples.";
$texto =~ s/é/foi/g;
# Resultado: "Isto foi um teste. Foi um teste simples."
```

#### Delimitadores Diferentes

Você pode usar delimitadores diferentes de barras (/) com `s///`, o que é especialmente útil quando seu padrão ou string de substituição contém barras.

```perl
my $texto = "Substitua este texto.";
$texto =~ s|este|aquele|;
# Resultado: "Substitua aquele texto."
```

#### Modificadores de Substituição

O Perl fornece vários modificadores de substituição para controlar o comportamento de `s///`.

- **`i`**: Realiza uma substituição sem diferenciação entre maiúsculas e minúsculas.
- **`m`**: Permite o uso de correspondência em várias linhas.
- **`s`**: Trata a string como uma única linha (padrão).
- **`g`**: Realiza uma substituição global.
- **`e`**: Avalia a substituição como código.

```perl
my $texto = "Substitua Este Texto.";
$texto =~ s/este/esse/i;
# Resultado: "Substitua esse Texto."
```

#### O Operador de Vinculação

O operador de vinculação (`=~`) é usado para aplicar uma substituição a uma string específica. Ele vincula a operação de substituição a uma variável.

```perl
my $texto = "Substitua este texto.";
$texto =~ s/este/esse/;
# Resultado: "Substitua esse texto."
```

#### Substituições Não Destrutivas

Para realizar substituições não destrutivas sem modificar a string original, você pode usar o modificador `/r` junto

 com `s///`. Ele retorna a string modificada em vez de modificá-la no local.

```perl
my $original = "Substitua este texto.";
my $modificado = $original =~ s/este/esse/r;
# $original ainda é "Substitua este texto."
# $modificado contém "Substitua esse texto."
```

#### Mudança de Caixa

Você pode alterar a caixa dos caracteres usando expressões regulares. Por exemplo, para converter texto em minúsculas ou maiúsculas:

```perl
my $texto = "Converter Para Minúsculas.";
$texto =~ s/(\w+)/\L$1/g;
# Resultado: "converter para minúsculas."

$texto =~ s/(\w+)/\U$1/g;
# Resultado: "CONVERTER PARA MAIÚSCULAS."
```

### O Operador `split`

O operador `split` em Perl é usado para dividir uma string em um array de substrings com base em um padrão ou delimitador especificado.

#### Uso Básico

Você pode dividir uma string usando um delimitador simples, como um espaço ou vírgula:

```perl
my $texto = "maçã,banana,laranja";
my @frutas = split /,/, $texto;
# @frutas agora contém ("maçã", "banana", "laranja")
```

#### Lidando com Campos Vazios

O `split` também pode lidar com campos vazios quando os delimitadores estão adjacentes:

```perl
my $texto = "um,,três";
my @campos = split /,/, $texto;
# @campos agora contém ("um", "", "três")
```

#### Usando Espaço em Branco como Delimitador

Comumente, você pode dividir uma string com base em espaços em branco usando o padrão `\s+`:

```perl
my $frase = "Isso é uma frase de exemplo.";
my @palavras = split /\s+/, $frase;
# @palavras agora contém ("Isso", "é", "uma", "frase", "de", "exemplo.")
```

### A Função `join`

A função `join` em Perl é usada para concatenar um array de strings em uma única string usando uma sequência de colagem especificada.

#### Uso Básico

Você pode unir elementos de um array usando uma sequência de colagem:

```perl
my @frutas = ("maçã", "banana", "laranja");
my $texto = join ", ", @frutas;
# $texto agora é "maçã, banana, laranja"
```

#### Sequência de Colagem Personalizada

Você pode especificar qualquer string como sequência de colagem:

```perl
my @números = (1, 2, 3, 4, 5);
my $resultado = join " - ", @números;
# $resultado agora é "1 - 2 - 3 - 4 - 5"
```

### `m//` em Contexto de Lista

Em Perl, o operador `m//` é usado para correspondência de padrões. Em contexto de lista, ele retorna uma lista de valores capturados da correspondência.

#### Grupos de Captura

Você pode usar grupos de captura para extrair partes específicas de uma string:

```perl
my $texto = "Olá, mundo!";
my ($saudacao, $nome) = $texto =~ /(Olá), (mundo)/;
# $saudacao é "Olá" e $nome é "mundo"
```

#### Correspondendo Múltiplas Vezes

Usando o modificador `/g` com `m//`, você pode corresponder um padrão várias vezes em uma string e capturar todas as ocorrências:

```perl
my $texto = "maçã,banana,maçã,cereja";
my @correspondencias = $texto =~ /(\w+)/g;
# @correspondencias agora contém ("maçã", "banana", "maçã", "cereja")
```

### Expressões Regulares Mais Poderosas

As expressões regulares em Perl oferecem recursos avançados que aprimoram as capacidades de processamento de texto.

#### Quantificadores Não Gananciosos

Quantificadores não gananciosos permitem que expressões regulares correspondam o mínimo possível, fornecendo um controle mais preciso sobre a correspondência de padrões.

##### Quantificador Ganancioso (Corresponder o máximo possível)

```perl
my $texto = "Isso é uma <tag>exemplo</tag> de string.";
$texto =~ /<.*>/;  # Correspondência gananciosa
# Corresponde "<tag>exemplo</tag>"
```

##### Quantificador Não Ganancioso (Corresponder o mínimo possível)

```perl
my $texto = "Isso é uma <tag>exemplo</tag> de string.";
$texto =~ /<.*?>/;  # Correspondência não gananciosa
# Corresponde "<tag>" e "</tag>"
```

#### Correspondência de Texto em Múltiplas Linhas

O mecanismo de regex do Perl pode facilmente corresponder padrões em texto de várias linhas usando o modificador `/m`.

```perl
my $texto_multilinha = "Linha 1\nLinha 2\nLinha 3\n";
if ($texto_multilinha =~ /^Linha 2$/m) {
    print "Correspondência com 'Linha 2' no início de uma linha.\n";
}
```

#### Atualizando Vários Arquivos

Perl permite que você atualize programaticamente vários arquivos com conteúdo semelhante usando a edição em locais específicos.

```perl
#!/usr/bin/perl -w
use strict;

$^I = ".bak";  # Criar arquivos de backup

while (<>) {
    s/padrão_antigo/novo_padrão/g;  # Realiza substituições
    print;
}
```

#### Edição em Locais Específicos a partir da Linha de Comando

O Perl oferece opções convenientes para realizar edição em locais específicos diretamente da linha de comando.

```shell
$ perl -p -i.bak -w -e 's/padrão_antigo/novo_padrão/g' arquivos*.txt
```

Este comando substitui `padrão_antigo` por `novo_padrão` em todos os arquivos que correspondem a `arquivos*.txt` e cria arquivos de backup com a extensão `.bak`.
