# Cores e Fundos

- `<color>`
  -- named
  -- hexadecimal
- background
  -- color, image, repeat, position, sizing, ...

## Nomes de cores e hexadecimal

```css
p {
  /*named color - no editor aparecem várias cores 'named'*/
  color: blue;
  color: black;
  /*rgb = red, green, blue*/
  /*exemplos de hexadecimal*/
  color: #ff0000;
  color: #ff000055; /*mais granularidade para as cores*/
  color: #f00;
  color: #f00a; /*nesse caso, o último dígito é referente ao alfa - transparência*/
}
```

- cor hexadecimal: sempre iniciada por "#", com caracteres de '0' a '9' e 'a' até 'f'
- tudo 'fff' é o branco; tudo '000' é o preto

## Background

- propriedade `background` pode ser aplicada em qualquer elemento html
  -- background-color: aplica uma cor ao fundo da 'caixa'
  -- background-image: aplica uma imagem ao fundo da 'caixa' `url()`
  -- background-repeat: por padrão, ao adicionar uma imagem, ele é repetida; colocar o valor 'no-repeat' para não repetir
  -- background-position: shorhand para =>
  --- background-position-x : position no eixo 'x'
  --- background-position-y : position no eixo 'y'
  --- background-position: center (aplica para todos os eixos); se usar 2 valores, o primeiro é para o eixo 'x' e o segundo é eixo 'y'
  -- background-sizing: tamanho
  --- pode ser tamanhos fixos, relativos, percentuais, ...
  --- contain, cover,

- Background é um estudo grande, tem bastante coisa na documentação
- o shorthand `background` é mais forte do que todos os outros

```css
/*shorthand*/
body {
  background: #eeeeee url(../assets/fullstac-img.png) no-repeat center/1rem;
}
```
