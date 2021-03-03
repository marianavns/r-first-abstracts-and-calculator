# Primeiro Pacote em R

Este repositório contem o projeto de uma calculadora simples feita em R. Abaixo, o passo a passo para construir este pacote do zero.

## Sumário

- [Passo a passo](#Passo-a-Passo)
  - [Pré-requisitos](#Pré-requisitos)
  - [Criando o repositório para guardar os arquivos do projeto](#Criando-o-repositório-para-guardar-os-arquivos-do-projeto)
  - [Preparando o ambiente com os pacotes necessários](#Preparando-o-ambiente-com-os-pacotes-necessários)
  - [Criando a primeira função da calculadora](#Criando-a-primeira-função-da-calculadora)
    - [Renomeando o arquivo principal](#Renomeando-o-arquivo-principal);
    - [Digitando e rodando a primeira função da calculadora](#Digitando-e-rodando-a-primeira-função-da-calculadora);
  - [Criando a documentação das funções com o Roxygen](#Criando-a-documentação-das-funçoes-com-o-Roxygen)
  - [Criando a documentação do projeto todo com o RMarkdown](#Criando-a-documentação-do-projeto-todo-com-o-RMarkdown)

 ![:octocat:](https://github.githubassets.com/images/icons/emoji/octocat.png) Este é meu primeiro projeto em R. Se tiver alguma sugestão ou correção, clica [AQUI](https://github.com/marianavns/r-simple-calculator/issues) e seleciona _New Issue_. Obrigada!

## Passo a passo

<img src="./assets/step-by-step.gif" width="40%">



### Pré-requisitos

Para seguir este tutorial do primeiro projeto em R, independente do que ele faça, é necessário já ter estes programas instalados e configurados:

- R;
- RStudio;
- Git.

Vamos lá!



### Criando o repositório para guardar os arquivos do projeto

1. Abra o RStudio e selecione a opção: `File -> New Project -> New Directory -> R package`;
2. Escolha o nome para o seu pacote. O meu é `simpleCalculator`;
3. Marque a opção `create a git repository`e, em seguida, `Create Project`.

*Pronto, a pasta com os arquivos do seu pacote R foi criada!*

### Preparando o ambiente com os pacotes necessários

4. No console, digite estes comandos, um por vez. Quando o download do primeiro acabar, você digita no console o segundo:

   ​	1º `install.packages("roxygen2")`;

   ​	2º `install.packages("devtools")`;

   ​	3° `install.packages("Rtools")`

### Criando a primeira função da calculadora

#### Renomeando o arquivo principal

5. No seu RStudio há uma área de navegação de pastas com as abas _Files, Plots, Packages, Help, Viewer_ . Clique na aba _Files_;
6. Entre na pasta R;
7. Marque a caixa de seleção do arquivo `hello.R` , clique em _Rename_ e troque o nome do arquivo para qualquer um de sua preferência;

#### Digitando e rodando a primeira função da calculadora

8. Abra este arquivo que você acabou de renomear e apague tudo dentro dele;

9. Crie a função de teste:

   ```R
   somar <- function(a,b) {
     a + b
    }
   ```

10. Salve (Ctrl + S);

11. "Construa" a função na sua máquina com o comando Ctrl + Shift + B. É como se você estivesse mandando o RStudio "ligar os pontos";

12. Faça o teste no console para ver se deu certo, digitando `somar(100,50)`. O resultado deve ser 150.

<img src="./assets/instruction-manual.gif" width="40%">

### Criando a documentação com o Roxygen

> Fazer as funções é muito legal, mas melhor ainda é compartilhar e explicar para outros usuários o que você está fazendo! Para isso, existe a possibilidade de exportar suas funções e adicionar uma documentação a cada uma delas. Vamos criar a documentação da função `somar`:

13. Escreva detalhes da sua função acima dela. Cada linha precisa ser precedida por `#'`. Assim, o R identifica estas linhas como documentação. 
14. No fim da documentação e **logo acima da função**, digite `@export`. Este é o resultado final:

```R
#' Function somar
#'
#' This function is used to add two values.
#'
#' @param a first number.
#' @param b another number.
#'
#' @examples
#' sum(100, 50)
#'
#' Console response: 150
#' @export
somar <- function(a,b) {
  a + b
  # Could be sum(a,b) too. sum is a R native function.
}
```

15. Existe um arquivo na sua área de navegação chamado `NAMESPACE`. Ele guarda todas as funções que você está exportando. **Delete, pois vamos fazer um novo** no passo abaixo.

16. Na barra de navegação do RStudio, selecione as opção `Tools -> Project Options -> Build Tools`

17. Marque a caixa _Generate documentation with Roxygen_;

18. Abrirá uma nova janela. Certifique-se que todas as caixas estão marcadas, exceto _Vignettes_. Ela não será importante agora. Selecione OK.

19. No console, digite `??somar` e confira se aquele texto que escrevemos no passo 13 aparece na aba "Help".

    *Pronto, a documentação foi criada!*

20. Clique na aba `Build -> Check Package`

**Parabéns, seu primeiro pacote está pronto e disponível!**

<img src="./assets/celebration.gif" width="40%">

### Criando a documentação do projeto todo com o RMarkdown

Uma outra funcionalidade que o RStudio oferece é a possibilidade de criar um "documento de apresentação" do projeto todo. Para fazer isso, usaremos uma linguagem chamada _markdown_. Ela permite que criemos um texto adicionando títulos, sumário, imagens e (quase) todo o resto que permitir em termos de edição de texto.

Para começar, selecione no RStudio:
`File -> New File -> R Markdown`

Verifique se está na aba "Document". Adicione o título e os autores e selecione o tipo de arquivo que será criado em segundo plano, além do arquivo markdown. É possível que seja HTML (caso queira visualizar posteriormente num navegador), PDF ou Word. Acredito que a opção mais utilizada seja HTML.

Feito isto, seu RStudio vai criar um arquivo chamado "Untitled". Ele ainda não está salvo no seu projeto. Para que isso aconteça, clique em 'Knit'. Agora sim seu projeto tem um arquivo com extensão ".Rmd", para suas edições, e ".html", para ver o resultado final.

#### Tornando esta documentação visível para o GitHUB

Se o projeto for colocado do jeito que está no github, o site entenderá que deve ler apenas o arquivo HTML e apresentar a quem está visitando seu repositório. Mas temos um problema aí: o Github não renderiza (não mostra da forma certa) os arquivos .html. Ele precisa estar em formato .md.

Para configurar isto, vamos no cabeçalho do arquivo da documentação, o ".Rmd", e façamos a seguinte alteração:

`output: html_document` vai virar:

```
output:
  github_document:
    fig_width: 9
    fig_height: 5
```

Feito isso e selecionando "Knit" de novo, o RStudio vai criar um arquivo no formato .md, que é aquilo que o GitHUB entende! ;)
