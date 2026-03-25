# Responsividade

## CSS Media Queries

- 'qual a tela que está sendo usada'
- 'media queries' condicional para verificar se o usuário esta:
  - desktop
  - mobile
  - largura / altura
  - landscape / portrait

- de acordo com essas condicionais o 'css' pode ser alterado na minha página

- `<meta name="viewport">`
  - criado pela Apple para Iphones
    - sem ela, os sites eram abertos sempre em 980px, e o usuário precisava dar zoom sempre
  - `content` = adaptar para cada device
    - `width` = largura do dispositivo
    - `initial scale` = escala inicial

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0" />
```

esse 'media' pode ser adicionado de algumas maneiras:

- na tag <link>

```html
<link media="screen and (orientation:portrait)" />
```

- através do `@import`

```css
@import url(screen.css) screen and (orientation: portrait);
```

- adicionando direto no css (mais comum) -
- `@media`

```css
@media screen and (min-width: 640px) {
  /* declaration here */
}
```

## Entendendo a sintaxe

`@media`

```css
@media (min-width: 640px) {
  /* code here */
}
```

- optionally: screen, print => são opcionais em serem inseridos (geralmente não tem)
  - print = estilos para impressão
- breakpoints - pontos de quebra
  - a partir de qual momento que a regra vai ser 'interpretada' =>
    - `@media (min-width: 640px)` = a partir que a tela tiver no mínimo 640px a regra vai ser interpretada (conforme exemplo)
    - pixel, rem, named (portrait, landscape)
    - encontrar breakpoints: ferramenta de desenvolvedor
- rules
  - min-width / max-width
  - orientation = portrait / landscape
  - prefers-color-scheme: dark (olha para as configurações de sistema do usuário e aplica a regra)
- and
  - 'combo' de regras, operador lógico 'E' padrão
  - define alguns limites, se necessário
- range (novo no css)
  - em vez de usar o min / max, usa-se os sinais 'maior, menor, maior igual, menor igual' da matemática
  - `>, >= <, <=`
  - `width > 600px`, `600px < width < 800px`
- not
  - interver a lógica

## Evolução dos Media Queries

- link que vai atualizando ao longo do tempo (já está no level 5)
- sempre observar no caniuse coisas novas
- https://www.w3.org/TR/mediaqueries-5/
- https://caniuse.com

## Dicas

- Estratégias - Mobile First / Desktop First
  - antes, fazia o mobile first, agora faz os 2 ao mesmo tempo
  - dica: https://responsively.app/ - baixar este app que ajuda a ter as telas em uma só
- Unidade de medida relativa
  - no @media tomar cuidado com medidas relativas (em, rem) pois eles sempre irão pegar o initial value (16px)
- Arquivos separados?
  - arquivos separados afeta o carregamento da página
  - bundler (empacotador) = 
