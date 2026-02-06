# CSS Flexbox

_Flex_
_Justify-content_
_Align-items_
_Gap e Margin_
_Multi Line_
_Flex Basis_
_Flex Grow e Flex Shrink_
_Shorthand Flex_
_Order_

## Container, itens, eixo

Conceitos

- sempre vou ter um `flex` e significa que tenho um `container` e `itens` dentro dele
  -- ao aplicar o `flex` os itens ficam um ao lado do outro, quebrando o `flow` normal do html
- `axis` é o eixo, e teremos o `main` e o `cross`
  -- obs.: `main` (eixo x) e `cross` (eixo y)
  -- ao aplicar o `flex` no container, os itens ficam alinhados no eixo `main`
- `sizing`
  -- ao aplicar o `flex` no container os itens modificam o seu tamanho, quebrando também o padrão (principalmente para elementos do tipo `block`)
- umas das propriedades que podemos utilizar é a `flex-direction` onde é possível modificar a direção (modificar o eixo principal)
  -- inversão de eixo: ao aplicar `column`, o eixo principal `main` será colocado direção vertical (eixo y), e o eixo `cross` será colocado na horizontal (eixo x)
  -- valores: `row`, `column`, `reverse`
  -- `row-reverse`, `column-reverse`: invertem o `start` / `end` do eixo (invertido)

```css
.container {
  display: flex;
  flex-direction: column;
}

.divider {
  display: flex;
  flex-direction: row-reverse;
}
```

## Justify-content

- alinhamento dentro do `container`
- distribuição dos itens no eixo principal `main`
- valores
  -- `flex-start`=> padrão do flex quando aplicado
  -- `flex-end`
  -- `center`
  -- `space-evenly`
  -- `space-around`
  -- `space-between`
- geralmente quando temos mudança do eixo principal `main` para `flex-direction: column`, é necessário aplicar um valor de `height` para que os alinhamentos sejam observados

```css
.container {
  display: flex;
  justify-content: space-evenly;
}
```

## Align-Items

- alinhamento dos itens no eixo cruzado (cross = eixo "y" se `display flex:row;`)
- se o eixo cruzado for o eixo "x" (`display flex:column`) não aplica o 'stretch'
- por padrão começa com o valor "stretch"
- valores
  -- `stretch`: padrão (esticado)
  -- `flex-start`
  -- `flex-end`
  -- `center`
  -- `baseline`: alinhamento na 'base do texto'

```css
.container {
  display: flex;
  align-items: stretch;
}
```

## Gap e Margin

- `gap` = espaço entre os elementos
  -- pode ser um 'length' fixa, relativo ou flexível
- `margin`
  -- alinhamento automático de margem

```css
.container {
  display: flex;
  gap: 1rem;
  gap: 16px;
}
```

## Multi Line

- `flex-wrap`
  -- tamanho do container
  --- quando os elementos ultrapassam o tamanho do container, o wrap 'quebra' a linha;
  --- por padrão o flex vai 'tentar' encaixar todos os elementos no tamanho do container;
  --- se, por exemplo, todos os elementos possuírem um `width` maior do que o tamanho da caixa, o `flex` ajusta
  -- nova linha = novo container
  --- quando faz o `wrap`, o 'eixo principal' `main` é duplicado para cada 'linha', no caso de `flex-direction: row`
  -- valores
  --- `nowrap`: padrão sem a quebra
  --- `wrap`: quebra
  --- `wrap-reverse`: inverte a quebra, jogando para cima (`flex-direction: row`)

```css
.container {
  display: flex;
  flex-wrap: wrap;

  /*align*/
  align-content: center;
}
```

- `align-content`
  - o 'align-items' vai funcionar como se fosse '2 containers' distintos para os valores;
  - o 'align-conten' vai trabalhar os '2 containers' de forma igual;
    -- deve-se aplicar o `flex-wrap` para habilitar o `align-content`
    -- dependendo do que precisa ser feito, usa-se um ou outro
  - valores (mesmos valores do 'align-items'):
    -- `flex-start`
    -- `flex-end`
    -- `center`
    -- `space-around`
    -- `space-between`
    -- `space-evenly`

## Flex Basis

- `flex-basis`
  -- semelhante ao 'width', aplicado aos itens
  -- relacionado ao eixo principal, se inverter o eixo, é aplicado na 'vertical'
  -- tamanho do item em relação ao eixo principal - main
  -- se o container possuir alguma limitação de tamanho, o 'basis' se encaixa caso ultrapasse o tamanho total
  -- `basis` é como se fosse um valor 'desejável'
  -- valores:
  --- `auto`
  --- `0`
  --- `relativa, fixa ou flexível`

```css
.container {
  display: flex;
}

.item {
  flex-basis: 120px;
}
```

## Flex Grow e Flex Shrink

- `flex-grow`
  -- crescimento automático do item
  -- distribuição conforme os espaços vazios
  -- valor: 0 para 'desativar'

- `flex-shrink`
  -- encolhimento automático do item
  -- valor: 0 para 'desativar, 1 para ativar;
  -- por padrão, ele está ativado (valor 1)
  -- aceita valores 'quebrados' => 0.6, 0.2,

```css
.container {
  display: flex;
}

.item {
  flex-grow: 1;
  /*aqui estou informando que eu quero que este item 'creça' e 'ocupe os espaços'*/
  flex-basis: 120px;
  flex-shrink: 0;
  /*nesse caso com o basis e shrink, os itens irão receber os 120px, pois estou 'desativando' o encolhimento automático,
  o 'encaixe' dos itens dentro do container*/
  flex-shrink: 2;
  /* esse caso, os itens estão encolhendo em uma proporção '2', quanto maior o número, maior o encolhimento */
}

.item:nth-child(2) {
  flex-grow: 2;
  /*nesse caso, um dos itens vai ficar com '2 porções', ou seja, o 'dobro' do tamanho dos demais itens,
  e irão continuar encaixados e ocupando os espaços*/
  flex-shrink: 1;
  /*nesse cenário, o item 2 está com o encolhimento ativado, enquando os demais não
  se comparar com o ecolhimento '2' dos demais itens, quando aplicado,
  esse item encolhe menos od que os demais*/
}
```

## Shorthand Flex

- para basis, grow e shrink
- possibilidades de valores
  -- `initial`
  --- aplica os valores '0' para <grow>; '1' para <shrink> e 'auto' para <basis>
  -- `auto`
  --- aplica os valores '1' para <grow>; '1' para <shrink> e 'auto' para <basis>
  -- `none`
  --- aplica os valores '0' para <grow>; '0' para <shrink> e 'auto' para <basis>
  -- `um valor`
  --- se for um valor numérico, então aplica o valor inserido no <grow>, aplica o valor '1' para <shrink> e '0' para <basis> (desativa basis)
  --- se for um valor unitário (unidade), então aplica o valor inserido no <basis>, aplica o valor '1' para <shrink> e '1' para <grow>
  -- `dois valores`
  --- com dois valores, o primeiro sempre será o <grow>
  --- se o segundo valor for numérico, o valor inserido será aplicado ao <shrink> e aplica o valor '0' para <basis>
  --- se o segundo valor for unitário, o valor inserido será aplicado ao <basis> e aplica o valor '1' para <shrink>
  -- `três valores`
  --- ordem => <grow>, <shrink> e <basis>, sempre nessa ordem

```css
.item {
  flex: initial;
  flex: 0 1 auto; /*esse é o initial*/

  flex: auto;
  flex: 1 1 auto; /*esse é o auto */

  flex: none;
  flex: 0 0 auto; /*esse seria o none*/

  flex: 1;
  flex: 1 1 0; /*assim é como fica quando coloca-se apenas um valor numérico*/

  flex: 120px;
  flex: 1 1 120px; /*assim é como fica quando coloca-se apenas um valor de unidade*/

  flex: 0 1;
  flex: 0 1 0; /*assim é como fica quando coloca-se dois valores numéricos*/

  flex: 0 10%;
  flex: 0 1 10%; /*assim é como fica quando coloca-se dois valores, sendo o primeiro numérico e o segundo unitário*/

  flex: 1 1 100%; /*aplicação dos três valores*/
}
```

## Order

- padrão: 0
- valor numérico, positivo ou negativo;
- se negativo, joga no início, se positivo, vai para o final
- order é apenas visual, não estrutural, pois não muda a ordem do html
- não recomendado por questões de acessibilidade

```css
.item {
  order: 0; /*padrão*/
  order: -1;
  order: 1;
}
```
