# CSS Functions

- não são as pseudo-functions, como `:not()`, `:is()`, `:where()`, etc.
- CSS values functions

## Funções de Transformação

- `transform`
  - movimentação, rotação e tamanho (existem mais, mas essas seriam as principais)
  - `translate()` - movimenta nos eixos
  - `rotate()` - gira o elemento
  - `scale()` - escala do elemento

```css
div {
  transform: translate(
    1px 1px
  ); /* aplica nos eixos X e Y, sendo o primeiro argumento para o X e o segundo para Y*/
  transform: translateX(1px); /* aplica apenas no X */
  transform: translateY(1px); /* aplica apenas no Y */
}

p {
  transform: rotate(50deg); /* rotaciona em graus */
  /* posso fazer junto, por exemplo */
  transform: translateX(1px) rotate(40deg);
  /* a ordem influencia no comportamento, se colocar o rotate antes */
}

a {
  transform: scale(2); /* escala, no caso '2' está 'dobrando o valor */
}
```

## Funções matemáticas

**Operações Básicas**

- `calc()` - cálculo básico (soma, subtração, divisão, multiplicação)
  - posso usar diferentes unidades (% e rem, ... )
  - analisar cada caso pois as operações podem não funcionar corretamente

```css
div {
  width: calc(100% - 0.5rem);
  height: calc(1vh - 2rem);
}
```

**Comparações**

- `min()` - identifica qual é o menor valor conforme argumentos informados

```css
div {
  width: min(50%, 2vh);
  height: min(calc(50% + 2rem), 85%);
}
```

- `max()` - mesma ideia do `min`, ou seja, identifica o maior valor entre os elementos

```css
div {
  height: max(calc(50% + 2rem), 85%);
}
```

- `clamp()` - funciona com 3 valores
  - utilizado bastante em font-size
  - valor mínimo e máximo desejável

```css
p {
  font-size: clamp(1rem, 8vw, 4rem);
  /* aqui o mínimo do font-size é 1rem e o máximo é 4rem, o 8vw é como se fosse uma divisão da página para ir aumentando ou diminuindo a fonte*/
}
```

**Outras**

- `sin()` - seno
- `cos()` - cosseno
- `tan()` - tangente
- `pow()` - exponenciação
- `sqrt()` - radiciação (raiz)

## Funções de filtro para cores e imagens

- `filter`
  - `blur()` - borrar, desfocar
  - `brightness()` - brilho
  - `constrast()` - contraste (vai ficando mais tom 'pastel', opaco)
  - `drop-shadow()` - sombra do elemento (eixo x, eixo y, tamanho, cor)
  - `opacity()` - opacidade (0) fica oculto (mas o elemento está lá ainda)
  - `invert()` - inverte as cores
  - `hue-rotate()` - ideia da 'roda' de cores - hue - valor em 'degrees'
  - `saturate()` - saturação
  - `gryscale()` - preto e branco
  - `sepia()` - sepia

```css
div {
  filter: blur(2px);
  filter: brightness(1) contrast(0.2);
  filter: drop-shadow(1rem 1rem 1rem gray);
  filter: opacity(0.2);
  filter: invert();
  filter: hue-rotate(200deg);
}
```

## Função de Cores

- `color`
  - `rgb()` - red, green, blue: 3 argumentos na função, por padrão,
  - `hsl()` - cor, percentual de saturação (0 a 100) e percentual de luminosidade (0 a 100)
    - `rgba()` e `hsla()` => adiciona um 'alfa' na cor, que é a opacidade (transperência)
  - `color-mix()` - mistura de cores, tem 2 argumentos, a cor e o percentual da mistura

```css
div {
  color: rgb(97, 218, 27); /* os 3 argumentos definem uma cor */
  color: hsl(205, 50%, 50%); /* cor(hue), saturação*/
  color: hsla(205, 50%, 50%, 0.39); /* com alpha */
  color: rgba(64, 138, 191, 0.39); /* com alpha */
}

div {
  color: color-mix(in hsl, hsl(10 100% 50%), hsl(60 100% 50%));
}
```

## Funções degradê

- trabalhado na propriedade `background`
  - interpretado como uma imagem
  - `linear-gradient()` => 3 argumentos = angulação 'degrees' ou 'to right', cor inicial e cor final
  - `radial-gradient()` => 2 argumentos (cores) - degradê 'radio'

```css
div {
  background: linear-gradient(90deg, red, blue);
  background: radial-gradient(red, blue);
}
```

## Funções de formas

- propriedade `clip-path`
- https://bennettfeely.com/clippy/
  - `circle()` - faz um círculo padrão
  - `polygon()` - formar variadas - acessar o clippy pra fazer a forma

```css
div {
  clip-path: polygon(
    0% 0%,
    100% 0%,
    100% 75%,
    75% 75%,
    75% 100%,
    50% 75%,
    0% 75%
  );
}
```

## Funções que referenciam outros valores

- `var()` - variável padrão no css
- `url()` - referenciando
- `attr()` - só aplicado ao 'content', referencia um atributo específico do html

```css
div::after {
  content: attr(aria-label);
}
```

## Outros

- grid
- animation
- contador
- devdocs.io (muito mais funções css)
