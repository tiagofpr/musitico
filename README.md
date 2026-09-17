# MusiTico

Editor de partituras em português que funciona no navegador. Permite escrever notas, organizar instrumentos, ouvir a composição e importar ou exportar partituras em MusicXML.

O projeto é uma aplicação estática: HTML, CSS e JavaScript estão reunidos no arquivo [`index.html`](index.html). Não há backend, instalação de pacotes ou etapa de build.

## Como executar

Abra o arquivo `index.html` em um navegador moderno. É necessário acesso à internet para carregar o VexFlow e as fontes externas.

Para servir o projeto localmente, caso tenha Python 3 instalado, execute na pasta do projeto:

```sh
python3 -m http.server 8000
```

Depois, acesse <http://localhost:8000>. Para encerrar o servidor, pressione `Ctrl+C` no terminal.

## Publicar no GitHub Pages

O MusiTico pode ser publicado diretamente pelo GitHub Pages, pois seu ponto de entrada é o `index.html` na raiz do repositório.

### 1. Enviar os arquivos para o GitHub

Este projeto já tem o remoto `origin` configurado para `https://github.com/tiagofpr/musitico.git` e utiliza a branch `master`. Na pasta do projeto, confira as alterações e envie os arquivos:

```sh
git status
git add index.html README.md
git commit -m "Documenta o MusiTico e a publicação no GitHub Pages"
git push origin master
```

Se os arquivos já estiverem commitados, execute apenas o `git push origin master`. Caso o Git solicite autenticação, use suas credenciais de acesso ao GitHub pelo método configurado no seu ambiente.

### 2. Habilitar a publicação

1. Abra o repositório [tiagofpr/musitico](https://github.com/tiagofpr/musitico).
2. Clique em **Settings** (Configurações).
3. No menu lateral, entre em **Pages**, na seção **Code and automation**.
4. Em **Build and deployment**, selecione **Deploy from a branch** no campo **Source**.
5. Em **Branch**, escolha **master** e a pasta **/ (root)**.
6. Clique em **Save**.

Se você usar outra branch no futuro, escolha a branch que contém o `index.html` na raiz. Consulte a [documentação oficial sobre a fonte de publicação](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site).

### 3. Acompanhar e abrir o site

Na aba **Actions** do repositório, acompanhe a execução de publicação do Pages. Quando terminar com sucesso, volte a **Settings → Pages** e abra o endereço exibido pelo GitHub.

Com o nome atual do usuário e do repositório, e sem domínio personalizado, o endereço esperado é:

**[https://tiagofpr.github.io/musitico/](https://tiagofpr.github.io/musitico/)**

A publicação pode levar alguns minutos. O link só funcionará depois que o Pages estiver configurado e a publicação terminar. Veja também o [guia oficial de criação de um site GitHub Pages](https://docs.github.com/en/pages/getting-started-with-github-pages/creating-a-github-pages-site).

### 4. Atualizar o site

Depois de alterar o editor, envie um novo commit para a branch de publicação:

```sh
git add index.html README.md
git commit -m "Atualiza o MusiTico"
git push origin master
```

O GitHub Pages publicará a nova versão automaticamente. Aguarde a execução na aba **Actions** antes de conferir a atualização.

### Se algo não funcionar

- **Erro 404:** confira se a publicação terminou e se a fonte está configurada como `master` e `/ (root)`, com o `index.html` nessa pasta.
- **Publicação falhou:** abra a execução na aba **Actions** para consultar a mensagem de erro.
- **Pages indisponível:** confira suas permissões no repositório e a disponibilidade do recurso para a visibilidade e o plano da conta.
- **Biblioteca de notação não carregou:** verifique a conexão e o acesso ao jsDelivr, de onde o editor carrega o VexFlow.

Os projetos salvos localmente não são transferidos automaticamente para o site publicado. Para levar uma partitura ao Pages, exporte o MusicXML na versão local e importe o arquivo na versão publicada.

## Funcionalidades

- Inserção de notas pela altura do clique na pauta ou pelo teclado.
- Figuras de semibreve a semifusa, pausas, notas pontuadas e acordes.
- Sustenidos, bemóis, bequadros, ligaduras de valor e de expressão e tercinas.
- Articulações: staccato, acento, tenuto e fermata; dinâmicas de `pp` a `ff`.
- Configuração de andamento, fórmula de compasso, tonalidade soante e anacruse.
- Adição e remoção de instrumentos e compassos, com modelos para solo, melodia e baixo, quarteto de sopros e banda.
- Armaduras adaptadas aos instrumentos transpositores e reprodução em altura soante.
- Reprodução sintetizada com destaque das notas e suporte a ritornelos.
- Paginação em folhas A4 e ajuste de compassos por linha.
- Salvamento de projetos no navegador, importação e exportação MusicXML e impressão.

Os instrumentos disponíveis são flauta, oboé, clarinete em Si♭, saxofones soprano, alto, tenor e barítono, trompete em Si♭, trompa em Fá, trombone, tuba, violino, viola, violoncelo, contrabaixo, piano e voz.

## Uso básico

1. Ao abrir, o editor apresenta uma frase de exemplo para sax alto. Use **Limpar tudo** para remover as notas ou escolha um modelo em **Novo a partir de…**.
2. Configure andamento, compasso e tonalidade. Edite o título e o compositor diretamente no cabeçalho da partitura.
3. Escolha uma figura e clique em uma área livre da pauta para inserir uma nota. Clique em uma nota existente para selecioná-la e editar suas propriedades.
4. Use **Acorde** para adicionar alturas à nota selecionada e **+ Compasso** para ampliar a composição.
5. Clique em **Tocar** para ouvir e em **Salvar** para registrar o projeto no navegador. Abra projetos pela lista **Projetos salvos**.
6. Use **MusicXML ⓘ** para baixar um arquivo `.xml`, **Importar XML** para carregar uma partitura e **Imprimir** para abrir o diálogo de impressão. Se disponível no navegador, escolha salvar como PDF.

Criar uma partitura a partir de um modelo ou importar XML substitui a partitura atual após confirmação. Salve seu trabalho antes de continuar.

## Atalhos de teclado

Os atalhos funcionam quando o foco está fora dos campos de texto e seletores.

| Tecla | Ação |
| --- | --- |
| `A`–`G` | Inserir lá, si, dó, ré, mi, fá ou sol, respectivamente |
| `Shift` + `A`–`G` | Adicionar uma altura ao acorde selecionado |
| `1`–`7` | Escolher semibreve, mínima, semínima, colcheia, semicolcheia, fusa ou semifusa |
| `.` | Alternar ponto de aumento |
| `R` | Alternar modo de pausa |
| `↑` / `↓` | Subir ou descer a altura diatônica da nota selecionada |
| `←` / `→` | Navegar entre notas |
| `T` | Alternar ligadura de valor |
| `S` | Marcar início e fim de ligadura de expressão |
| `Y` | Criar ou remover tercina a partir da nota selecionada |
| `Delete` / `Backspace` | Apagar a nota selecionada |
| `Espaço` | Iniciar ou parar a reprodução |

## Salvamento e formatos

O botão **Salvar** grava os projetos em `localStorage`, na chave `musitico:projetos`. O salvamento é manual e fica vinculado ao navegador e à origem utilizada; mudar de endereço ou porta pode apresentar uma lista diferente. Limpar os dados do navegador pode apagar os projetos. Exporte em MusicXML para manter uma cópia fora do navegador.

A exportação gera MusicXML 3.1 no formato `score-partwise`. A importação aceita arquivos não compactados `.xml` e `.musicxml` com essa estrutura; arquivos `.mxl` e o formato `score-timewise` não são suportados. A implementação cobre um subconjunto do MusicXML, portanto partituras complexas podem perder detalhes na conversão.

## Tecnologias e organização

| Recurso | Implementação |
| --- | --- |
| Interface e estilos | HTML5 e CSS no `index.html` |
| Edição e estado da partitura | JavaScript sem framework |
| Renderização da notação | VexFlow 4.2.3, carregado via jsDelivr, com saída SVG |
| Reprodução | Web Audio API, com osciladores sintetizados |
| Persistência | `localStorage` |
| Leitura de arquivos e XML | `FileReader` e `DOMParser` |
| Tipografia | Inter e Spectral, carregadas pelo Google Fonts |

O JavaScript está organizado em seções de dados musicais, desenho paginado, edição, ferramentas, instrumentos, reprodução, salvamento, MusicXML e diálogos. Para modificar o projeto, edite o `index.html` e recarregue a página.

## Limitações atuais

- Os timbres são sintetizados e não usam amostras reais dos instrumentos.
- Cada instrumento utiliza uma pauta e uma sequência de notas/acordes por compasso; não há um modelo completo de múltiplas vozes ou pauta dupla para piano.
- A barra lateral de instrumentos e projetos salvos fica oculta em telas de até 900 px de largura.
- Muitos instrumentos no mesmo sistema podem ultrapassar o espaço disponível na folha A4; o editor exibe um aviso nessa situação.
- O repositório não contém configuração de testes automatizados. Alterações podem ser verificadas no navegador, exercitando edição, reprodução, salvamento, importação/exportação e impressão.
