# Box Model

- Todos os elementos HTML são considerados como uma caixa pelo CSS
- Caixa:
  -- conteúdo, altura, largura, preenchimento interno, espaçamento externo, bordas ...

## Display

- Apresentação
- block: caixa block
  -- padrão do html: ter uma tag abaixo da outra;
  -- quando a tag é block ela ocupa 'uma linha'
- inline: caixa inline
  -- padrão do html: tag uma ao lado da outra

## Display block

Características:

1. Ocupa toda a linha como um `bloco`
2. `width` e `height` são aplicados
3. `padding`, `margin` e `border` funcionam por completo

- Exemplos de elementos: `div`, `main`, `header`, `section`, ...

## Display inline

Características:

1. ocupa apenas o espaço do conteúdo do elemento
2. elementos poderão ficar 'em linha'
3. `width` e `height` não se aplicam
4. aplicamos apenas os valores horizontais de `margin`, `padding` e `border`

- Exemplos de elementos: `a`, `span`, `strong`, `em`, ...

## Border

- é possível aplicar `style`, `width` e `color`
  <https://devdocs.io>

- `border` é uma shorthand de:
  -- border-color
  -- border-style
  -- border-width

- aplicar o `style` para aplicar o resto

```css
.border {
  border: solid red 1px; /*exemplo*/
}
```

## Width e Height

- aplicação em elementos `block`, não aplicar em elementos `inline`
- geralmente não definimos largura/altura das 'caixa', depende do contexto, para não ter o chamado 'overflow'
- é possível aplicar mínimos e máximos de largura e altura

## Margin

- `shorthand` de:
  -- margin-top
  -- margin-right
  -- margin-bottom
  -- margin-left

- valores a serem aplicados ao `margin`
  -- length (diversas possibilidades) - vh, vw, px, em, entre outros..
  -- percentage

- `margin-top` e `margin-bottom` não são aplicados para elementos `inline`
- na `syntax` tem a informação '1,4', que significa que podem ser utilizados 4 valores para o 'margin' - shorthand

- `margin: auto` = não funciona na vertical para elementos 'block'; não funciona para elementos inline

- margin colappsing; conceito onde a margem inferior de um elemento e a margem superior do outro elemento de tocam, para que não 'some' as margens e fique 'correto'

## Padding

- preenchimento interno da caixa
- `padding` é o shorthand de:
  -- padding-top
  -- padding-right
  -- padding-bottom
  -- padding-left
- não aplicar em elementos `inline`

## Box Sizing

- por padrão, o `padding` aumenta o tamanho da caixa;
- para remover o padrão, aplicar no elemento:

```css
/*zerando para todo o projeto o padrão*/
* {
  box-sizing: border-box;
}
```
