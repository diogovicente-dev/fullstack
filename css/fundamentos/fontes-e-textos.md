# Fontes e Textos

## Fundamentos

- Propriedades principais: estilos de fontes e layout dos textos
- estilos:
  -- font-family, font-size, bold, ...
- layout
  -- text-align, line height, ...

## Font family

<https://devdocs.io>

- procurar font-family
- `font-family` mais genéricas para buscar demais em caso de não encontar

```css
p {
  font-family: Arial, "Lucida Sans", sans-serif;
  /*aqui faz um fallback: se não encontrar arial, tenta encontar a Lucida Sans, se não encontrar, pega uma sans-serif*/
}
```

## Font size

- mudar o tamanho da fonte
- aceita algumas `keywords`
  -- small, large, ...
- melhor usar unidades de medidas
- font-size padrão do root: 16px
- unidade `1rem` => uma medida do `root element`

## Font style, Font weight

- `style` é simples: adicionando o itálico o não
- `weight` é a questão do bold - negrito:
  -- bold, semibold, extrabold,
  -- ou pode ser com valores => 100, 200, 300, 400
- vai depender da fonte que está sendo utilizada, umas podem ter bold, outras até não terão bold

## Color, Text-transform, Text-decoration

- `color`: adicionar uma cor ao texto
- `text-transform`:
  -- lowercase, uppercase, capitalize, none (padrão)
- `text-decoration`:
  -- `shortand` de
  -- text-decoration-color
  -- text-decoration-line
  -- text-decoration-style
  -- text-decoration-thickness
  -- valor: none (remove) o padrão do elemento (link, mark, etc)

## Text Align, Line height

- `text-align`
  -- center, right, justify
- `line-height`
  -- valores em `lenght`
  -- sugestão de uso: valor multiplicador
  -- ao colocar, por exemplo, o valor 1.2, 1.5, baseado no tamanho do `root element`
  -- ou pode ser fixo, mas se mudar o tamanho da fonte o cálculo já é feito automático

## Letter spacing, Word spacing

- `letter-spacing`
- `word-spacing`
- valores em length, geralmente usado valores pequenos, principalemente o letter-spacing, pois é bem agressivo
- não aplicar sem consentimento,

## Web fonts

- importar fontes (serviço online)
  -- fonts.google.com
- importar fontes (locais)
