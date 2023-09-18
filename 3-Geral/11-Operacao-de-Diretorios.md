## Operações de Diretório

As operações de diretório em Perl são essenciais para trabalhar com arquivos e diretórios de forma eficiente. Esta seção explora vários aspectos das operações de diretório, incluindo a navegação na árvore de diretórios, a busca por padrões, uma sintaxe alternativa para busca por padrões e identificadores de diretório.

### Navegando pela Árvore de Diretórios

Em Perl, você pode facilmente navegar pela árvore de diretórios usando funções embutidas como `chdir` para alterar o diretório de trabalho atual. Aqui está um exemplo de como mudar o diretório de trabalho para uma localização específica:

```perl
use Cwd;

# Obtenha o diretório de trabalho atual
my $diretorio_atual = getcwd();

# Altere o diretório de trabalho
chdir('/caminho/para/o/diretorio/desejado') or die "Não é possível alterar o diretório: $!";

# Verifique o novo diretório de trabalho
my $novo_diretorio = getcwd();
```

### Busca por Padrões

A busca por padrões permite que você encontre arquivos e diretórios com base em padrões de caracteres curinga. A função `glob` do Perl é usada para esse fim. Aqui está um exemplo de busca por padrões para listar todos os arquivos `.txt` no diretório atual:

```perl
my @arquivos_txt = glob('*.txt');

foreach my $arquivo (@arquivos_txt) {
    print "Encontrado arquivo: $arquivo\n";
}
```

### Uma Sintaxe Alternativa para Busca por Padrões

Uma alternativa ao uso de `glob` com padrões de caracteres curinga é usar o operador `<>`, que fornece uma maneira concisa de realizar a busca por padrões. Aqui está um exemplo usando o operador `<>` para obter o mesmo resultado do exemplo anterior:

```perl
my @arquivos_txt = <*.txt>;

foreach my $arquivo (@arquivos_txt) {
    print "Encontrado arquivo: $arquivo\n";
}
```

### Identificadores de Diretório

Perl fornece identificadores de diretório que permitem trabalhar com diretórios de forma mais eficaz. Você pode usar funções como `opendir` e `readdir` para abrir um diretório e ler seu conteúdo. Aqui está um exemplo de uso de identificadores de diretório para listar arquivos em um diretório:

```perl
my $caminho_do_diretorio = '/caminho/para/o/diretorio';

# Abra o diretório
opendir(my $identificador_diretorio, $caminho_do_diretorio) or die "Não é possível abrir o diretório: $!";

# Leia e imprima o conteúdo do diretório
while (my $entrada = readdir($identificador_diretorio)) {
    next if $entrada =~ /^\./;  # Pule arquivos/diretórios ocultos
    print "Encontrado: $entrada\n";
}

# Feche o identificador do diretório
closedir($identificador_diretorio);
```

### Listagem Recursiva de Diretórios

A listagem recursiva de diretórios é uma tarefa comum em Perl quando você precisa listar todos os arquivos e subdiretórios dentro de um diretório e seus subdiretórios. Isso pode ser feito usando funções recursivas. Aqui está um exemplo de listagem recursiva de todos os arquivos e diretórios dentro de um diretório especificado:

```perl
sub listar_arquivos_recursivamente {
    my ($diretorio) = @_;

    opendir(my $identificador, $diretorio) or die "Não é possível abrir o diretório $diretorio: $!";
    while (my $entrada = readdir($identificador)) {
        next if $entrada =~ /^\.\.?$/;  # Pule . e ..
        my $caminho = "$diretorio/$entrada";
        if (-d $caminho) {
            listar_arquivos_recursivamente($caminho);  # Recursão em subdiretórios
        } else {
            print "Arquivo: $caminho\n";
        }
    }
    closedir($identificador);
}

# Chame a função para listar arquivos recursivamente
listar_arquivos_recursivamente('/caminho/para/o/diretorio');
```

### Manipulando Arquivos e Diretórios

Perl fornece várias funções para manipular arquivos e diretórios, incluindo a criação, cópia e movimentação deles. Você pode usar `mkdir` para criar diretórios, `copy` do módulo `File::Copy` para copiar arquivos e `move` do módulo `File::Copy` para mover arquivos.

### Removendo Arquivos

A remoção de arquivos em Perl é feita usando a função `unlink`. Aqui está um exemplo de remoção de um arquivo:

```perl
my $arquivo_a_remover = 'exemplo.txt';

unlink $arquivo_a_remover or die "Não é possível remover $arquivo_a_remover: $!";
```

### Renomeando Arquivos

Para renomear arquivos em Perl, você pode usar a função `rename`. Aqui está um exemplo de renomeação de um arquivo:

```perl
my $nome_antigo = 'antigo_arquivo.txt';
my $nome_novo = 'novo_arquivo.txt';

rename $nome_antigo, $nome_novo or die "Não é possível renomear $nome_antigo para $nome_novo: $!";
```

### Links e Arquivos

Em Perl, você pode criar links simbólicos e links rígidos para arquivos usando as funções `symlink` e `link`, respectivamente. Aqui está um exemplo de criação de um link simbólico:

```perl
my $arquivo_alvo = 'original.txt';
my $nome_link = 'link_simbolico.txt';

symlink $arquivo_alvo, $nome_link or die "Não é possível criar o link simbólico: $!";
```

### Criando e Removendo Diretórios

Em Perl, você pode criar e remover diretórios usando as funções `mkdir` e `rmdir`, respectivamente. A função `mkdir` permite especificar o nome do diretório e as permissões iniciais. Aqui está um exemplo de criação de um diretório:

```perl
my $nome_do_diretorio = 'novo_diretorio';
my $permissoes =

 0755;  # Permissões iniciais em formato octal (por exemplo, 0755 para leitura/gravação/execução para o proprietário e leitura/execução para outros)

mkdir $nome_do_diretorio, $permissoes or die "Não é possível criar $nome_do_diretorio: $!";
```

Para remover diretórios vazios, você pode usar a função `rmdir`:

```perl
my $diretorio_a_remover = 'diretorio_a_remover';

rmdir $diretorio_a_remover or die "Não é possível remover $diretorio_a_remover: $!";
```

### Modificando Permissões

Você pode alterar as permissões de arquivos ou diretórios usando a função `chmod` em Perl. As permissões são especificadas no formato octal. Aqui está um exemplo de alteração de permissões:

```perl
my $novas_permissoes = 0644;  # Novas permissões em formato octal (por exemplo, 0644 para leitura/gravação para o proprietário e leitura para outros)
my @arquivos_a_modificar = ('arquivo1.txt', 'arquivo2.txt');

chmod $novas_permissoes, @arquivos_a_modificar or die "Não é possível alterar as permissões: $!";
```

### Alterando a Propriedade

Perl fornece a função `chown` para alterar a propriedade e a associação a grupos de arquivos ou diretórios. Você pode usar as funções `getpwnam` e `getgrnam` para converter nomes de usuários e nomes de grupos em IDs de usuário e IDs de grupo numéricos. Aqui está um exemplo:

```perl
my $novo_proprietario = getpwnam 'novo_nome_do_proprietario';
my $novo_grupo = getgrnam 'novo_nome_do_grupo';
my @arquivos_a_modificar = ('arquivo1.txt', 'arquivo2.txt');

chown $novo_proprietario, $novo_grupo, @arquivos_a_modificar or die "Não é possível alterar a propriedade: $!";
```

### Alterando Registros de Data e Hora

Para modificar os registros de data e hora de arquivos em Perl, você pode usar a função `utime`. Ela permite definir novos tempos de acesso e modificação para arquivos. Aqui está um exemplo de atualização de registros de data e hora:

```perl
my $agora = time;
my $novo_tempo_de_modificacao = $agora - 3600;  # Defina o tempo de modificação para uma hora atrás
my @arquivos_a_modificar = ('arquivo1.txt', 'arquivo2.txt');

utime $agora, $novo_tempo_de_modificacao, @arquivos_a_modificar or die "Não é possível alterar os registros de data e hora: $!";
```