# Layouts

_Flexbox_
_Grid_
_Position_
_Variáveis_
_Pseudo-classes_
_Pseudo-elements_

## Layouts e Evolução

- `block` e `inline` - padrão
- `table`

```html
<table>
  <tr>
    <!-- tr insere uma nova linha na tabela -->
    <td>conteúdo</td>
    <!-- td insere um elemento, quase uma coluna -->
  </tr>
</table>
```

- `tableless`
- não cria tabela, mas sim um conceito de 'float'

```html
<div style="float: left">conteudo</div>
<div style="float: right">conteudo</div>

<!-- pra continuar sem quebrar a página ajustar o próximo elemento -->
<div style="clear: both">mais conteudo</div>
```

- `flexbox`
  -- .container
  -- ideia de um container que possui vários itens internos
  -- `display: flex` => quebra o padrão, deixando todos em 'linha' ou 'coluna'
  -- libera outros atributos: ao aplicar ao container o `display: flex`, os elementos internos podem ser alinhados de forma flexível e mais prática

- `grid`
  -- espécie de 'grade' = colunas e linhas

_Uso_ => `flexbox` e `grid`; table e tableless não são muito utilizados atualmente

## Position

- `static`
  -- por padrão o elemento já possui um posicionamento automático
  -- já é o padrão 'static'
- `relative`
  -- apenas inserir `position: relative` não muda nada no elemento, porém destrava as propriedades para deslocamento do elemento
  -- offset relativo a si mesmo => o elemento se desloca em relação à posição em que ele estava inicialmente, como se ele ficasse com uma sobra no lugar em que ele estava
  -- normal flow => respeita o normal flow, considerando a posição inicial que ele estava
  -- stacking context => `z-index` => como se fosse o 'nível' dos elementos na página (para frente e para trás da página)
  ```css
  .position {
    position: relative;
    bottom: 20px;
    right: 20px;
    z-index: -1; /* aqui o elemento de classe 'position' está indo 'para trás' dos demais elementos de 'z-index:0' */
  }
  ```
- `absolute`
  -- um pouco diferente do relative
  -- fica em um determinado local da tela relativo ao containing block próximo ou initial, ou seja, tudo o que é 'visível' da página, por exemplo
  -- o containing block próximo é o 'pai' do elemento que estou aplicando o `absolute`
  -- no `pai` colocar um `position: relative`; no filho `position: absolute` (em relação ao pai)
  -- ! normal flow => não respeita o normal flow => ao aplicar `position: absolute` o elemento já é 'movido' para um novo contexto e posicionamento (um novo stacking context, por exemplo, mesmo aplicando 'z-index: auto')
  -- stacking context

```css
section {
  position: relative;
}
/* no exemplo, o elemento de classe position está dentro do elemento section */
.position {
  position: absolute;
  bottom: 20px;
  right: 20px;
}
```

- `fixed`
  -- fixo na tela => relativo ao initial containing block
  -- !normal flow => não respeita o normal flow, fica por cima de todos por padrão

- `sticky`
  -- relativo e fixo
  -- relativo ao elemento pai que tenha mecanismo de scroll (`overflow: scroll`)
  -- normal flow
  -- stacking context

```css
/* inset */
.position {
  inset: 10px 20px 30px 40px; /* top, bottom, left, right */
}
```

## Variáveis

- local para guardar uma informação para utilização posterior
- colocar qualquer valor

- criação:
  -- qualquer nome => sempre com dois trações iniciais
  -- exemplo: `--bg-color: #fff`
- uso:
  -- ao fazer a declaração, utilizar `var()`
  -- exemplo: `color: var(--bg-color)`

Escopo

- a variável pode ser criada no `:root` do html para toda a aplicação, mas a variável pode ser reescrita também em outro elemento
- nesse cenário, os filhos irão 'pegar' o valor definido nesse novo escopo, não do escopo global

## Pseudo-classes e pseudo-elements

- Seletores CSS II
- documentação possuui muito mais pseudo-classes e pseudo-elements para utilização no css

### pseudo-classes

-- `hover`: ao passar o mouse sobre seletor selecionado o estilo muda (cor, tamanho, etc..) a depepnder do que precisa ser feito

```css
/*exemplo*/
/*coloca-se o seletor e digita os dois pontos*/
div:hover {
  color: blue;
}
```

-- functional - existem várias, mas as duas principais/mais usadas são:
--- `not()`:

```css
/*nesse caso, esse pseudo-class aplica o estilo a todas as 'divs' exceto para a que tenha classe `.classe`*/
div:not(.classe) {
  color: blue;
}
```

--- `has()`:

```css
/*nesse caso, esse pseudo-class aplica o estilo a todas as 'divs' que seja div:hover*/
div:has(div:hover) {
  color: blue;
}
```

-- structural
--- `root`: tag raíz (:root), que usamos em muitas vezes

```css
:root {
  color: blue;
}
```

--- `nth-child(n)` : utilizado para selecionar um elemento (id, class) específico de um seletor 'pai'

```css
/*aqui estou selecionando o filho número "3" da elemento pai 'section', independente do tipo de tag, classe ou id */
section:nth-child(3) {
  color: blue;
}
```

### pseudo-elements

- declaração semelhante, mas os dois pontos são repetidos

```css
div::first-letter {
  font-size: 40px;
}

div::before {
  content: "";
  height: 10px;
  weight: 10px;
}
```

-- `first-letter`: altera o estilo de todas as primeiras letras de um texto
-- `before/after`: criação de um elemento antes ou depois de um 'conteúdo', por exemplo
