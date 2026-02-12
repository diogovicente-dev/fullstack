# CSS Grid

**Grid Template**
**Grid Column / Row**
**Grid Template Areas**
**Alinhamento GRID**
**Grid Auto**

## Explicando GRID

- como se fosse criado uma 'tabela' do excel dentro de um .container
- colunas x linhas
- consigo posicionar os elementos dentro deste 'grid' (container) de acordo com a necessidade
- colocar o elemento na posição desejada

## Propriedades Fundamentais

- composto por dois principais grupos: `container: o pai` e os `itens (os filhos)`
- `container` tem que ter o `display: grid`
  -- `grid`: a primeira coisa que cria são as 'linhas' `rows`
  -- ao aplicar o `grid`, todos os elementos se tornam `block`
  -- `inline-grid`: cria as linhas, mas os elementos 'não ocupam' o block inteiro
- mais usado `grid`

## grid-template

- shorthand de:
  -- grid-template-columns
  -- grid-template-rows
  -- grid-template-areas

### grid-template-columns

- 'separa' os itens em colunas, de acordo com os valores atribuídos e quantidade de colunas
- os valores podem ser vários tipos: `fr, px, %, rem, vw, ...`
- o grid-template-columns cria colunas; se em seus valores eu inserir apenas 2 valores (exemplo: `2fr 1fr`), significa que eu quero fazer 2 colunas;
  -- se o container possuir 3 elementos, o 'terceiro' elemento vai para a 'segunda linha'
  - aplicado no `container`

```css
.container {
  display: grid;
  /*exemplo se quiser colocar os itens em 3 colunas*/
  grid-template-columns: 1fr 1fr 1fr; /*pode ser tipo 200px 200px 100px*/
  grid-template-columns: repeat (3, 1fr); /* estou repetindo 3 vezes uma 'fração' */
}
```

### grid-template-rows

- por padrão, ao aplicar o 'grid' já fica em linhas
- diferente das colunas, se eu aplicar 2 valores e existir 4 itens dentro do container, aplica-se apenas para as duas primeiras linhas; as demais ficam sem a formatação
- aplicado no `container`

```css
.container {
  display: grid;
  grid-template-rows: 200px 50%; /*assim, apenas os itens 1 e 2 'pegam' essas configurações*/
}
```

**usar columns e rows para criar o grid completo**

## grid-column

- colocando os elementos no lugar
- aplicado nos filhos
- `grid-column` como shorthand de:
  -- `grid-column-start`
  -- `grid-column-end`
- indico qual coluna começa e qual coluna termina o 'elemento'
- considerar as 'linhas' virtuais
  -- imaginar que numa 'caixa' com 3 colunas existem '4 linhas virtuais'
  -- `| | | |` => 4 linhas para 3 colunas criadas

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
}

.child {
  /*esse elemento está 'ocupando' três colunas, ou seja, vai da linha virtual 1 até a linha virtual 4*/
  grid-column-start: 1;
  grid-column-end: 4;

  grid-column: 1/4; /* shorthand */
}
```

## grid-row

- `grid-row` como shorthand de:
  -- `grid-row-start`
  -- `grid-row-end`
- mesma ideia das linhas virtuais do `grid-column`, mas aplicado ao 'row'
- também aplicado nos filhos

```css
.container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(3, 1fr);
}

.child {
  /*esse elemento está 'ocupando' três linhas, ou seja, vai da linha virtual 1 até a linha virtual 4*/
  grid-row-start: 1;
  grid-row-end: 4;

  grid-row: 1/4; /* shorthand */
}
```

**GRID**
ao aplicar o grid, muitas vezes não é necessário configurar todos os elementos, pois o próprio grid 'encaixa' os restantes

## grid-template-areas

- criação das áreas que eu quero no css;
- `grid-template-areas` aplicado no 'pai' - container

```css
.container {
  display: grid;
  grid-template-areas:
    "A B B"
    "A B B"
    "A C D";
  /*criando áreas para o grid, uma 'caixa 3x3'*/
  grid-template-areas:
    "header header header"
    "main main aside"
    "footer footer footer";
}

.child {
  grid-area: A;
  grid-area: header;
  /*coloco o valor definido no template areas nos filhos para definir o posicionamento*/
}
```

## gap

- `gap`: shorhand de:
  -- `row-gap`
  -- `column-gap`
- aplicado no container
- não existe gap 'dentro' do espaço que um elemento está funcionando

```css
.container {
  display: grid;
  grid-template-areas:
    "A B B"
    "A B B"
    "A C D";
  gap: 20px;
}
```

## shorthand grid template

- primero valor é `grid-template-areas`
- segundo valor `grid-template-rows`
- após a `/`são os valores do `grid-template-columns`

```css
.container {
  grid-template: /* verão curta de todos, raramente utilizamos */
    "A B B" 80px
    "A B B" 40px
    "A C D" 50px / 80px 1fr 2fr;
}
```

## Alinhamentos do GRID

- existem 9 propriedades fundamentais
- 6 aplicadas no `container`

-- `align-content`
-- `justify-content`
-- `place-content`

-- `align-items`
-- `justify-items`
-- `place-items`

- 3 aplicadas no `item`

-- `align-self`
-- `justify-self`
-- `place-self`

### Content

- alinhamentos do conteúdo do grid
  -- o conteúdo é 'todo o grid', alinhando nos 'espaços' que sobra

- `align-content`
  -- alinhamento no eixo 'y', ou seja, no eixo vertical

- `justify-content`
  -- alinhamento no eixo 'x', ou seja, no eixo vertical

- `place-content`
  -- aplica 'align' e 'justify' ao mesmo tempo

### Items

- alinhamento do item (aplicado a todos os itens se for o caso)

- `align-item`
  -- alinhamento no eixo 'y', ou seja, no eixo vertical

- `justify-item`
  -- alinhamento no eixo 'x', ou seja, no eixo vertical

- `place-item`
  -- aplica 'align' e 'justify' ao mesmo tempo

### Self

- alinhamento específico de um item (ele mesmo)

- `align-self`
  -- alinhamento no eixo 'y', ou seja, no eixo vertical

- `justify-self`
  -- alinhamento no eixo 'x', ou seja, no eixo vertical

- `place-self`
  -- aplica 'align' e 'justify' ao mesmo tempo

## Propriedades AUTO Grid

- `grid-auto-flow`
  -- padrão: row; pode alterar para column
- `grid-auto-rows` e `grid-auto-columns`
  -- insere os valores nos astributos 'auto' fica repetindo os valores (loop)
  -- se tem 10 colunas, mas tem 2 valores no `grid-auto-columns`, fica em loop colocando os valores (tamanhos)

```css
.container {
  display: grid;

  grid-auto-flow: column;
  grid-auto-columns: 1fr 2fr;
  /*se a tabela tiver 3 colunas, a terceiro vai pegar 1fr; a quarta 2fr,; a quinta 1fr, e assim sucessivamente*/
}
```

## GRID ou FLEX

- usar o que eu domino mais e o que vou atingir o resultado
- observar a complexidade e escolher
- com o tempo teremos o entendimento de qual usar
