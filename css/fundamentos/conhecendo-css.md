# CSS

O que é CSS? => Cascading Stylesheet

- folha de estilo em cascata
- propriedade e valor
- estilos para o HMTL
- arquivo '.css'

```css
/*assim é comentário no css*/
.class
```

## Anatomia

Como se conecta com o HTML?

- Declaration
- Selector
- {} - Context
- Properties
- Property value

```css
/*abaixo é uma declaração*/

h1 {
  color: blue;
  font-size: 60px;
}
```

- h1 => é o seletor (Selector) - seletor de _tag_
- {} => todas as propriedades dentro é o contexto
- "color" => é uma propriedade (property)
- "blue" => é um valor (property value)
- cada propriedade vai ter valores específicos (numéricos, nomeados, boolean)
- seletor: qual elemento do html será 'alterado'

## Cascading

- Ideia cascading: hieraraquia de 'linhas' do código do css
  -- vai pegar o 'último' para aplicar
- Hierarquia de Regras Aplicadas
  -- seletor de tag, classe, id, entre demais

```css
/*nesse caso hipotético, tudo o que for 'tag' <p> ficará verde */

p {
  color: blue;
}

p {
  color: green;
}
```

## Especificidade

- Cada seletor utilizado (tag, class, id) tem um peso
  -- "Peso" de cada seletor
  -- #id = 100
  -- .class = 10
  -- element (tag) = 1

- A especificidade sobrepõe a ideia do cascading inicial
- Sempre vai olhar a especificidade

```css
/*considerando que tenhos os selecotes aplicados para uma mesma tag <p>, no exemplo
o texto pegaria o valor 'blue' do selecotr de 'id' */
#id {
  color: blue;
}

.class {
  color: red;
}

p /*element-tag*/ {
  color: black;
}
```

- é possível 'juntar' os seletores para que fiquem 'mais fortes'

```css
/*juntando*/

p#id.class {
  /*tem que ser juntos pra funcionar - p#id.class*/
  color: yellow;
}
```

## Mais específico

- style: colocar direto na tag, fica mais específico do que colocar no CSS
- !important: valor para colocar como valor do atributo, esse fica o mais forte e específico para todas as configurações

- sugestão: não usar o !important e o style, a não ser que seja extremamente necessário

```html
<div style="font-size: 32px"></div>
```

```css
#title: {
  font-size: 12px !important;
}
```

## Valores e unidades de medida

- cada propriedade possui valores
  'property': 'value'
  'data-type'
- estudo constante a fim de entender as propriedades e seus valores

- sempre observar o ```html <data-type>```
- ao descansar o mouse no editor de código, atentar ao "syntax", procurar no MDN
- procurar "mdn text-transform" por exemplo
- o atributo, dependendo do caso, pode ter valores diferentes
- por exemplo o font-size, ele tem:
  -- absolute, relative, percentage

<https://developer.mozilla.org/en-US/docs/Web/CSS/Reference/Properties/text-transform>

```css
h1: {
  color: blue; /*color*/
  font-size: 32px; /*length*/
  letter-spacing: 2; /*number*/
  text-transform: uppercase; /*keyword*/
}
```

## Seletores

- id
- class
- type | element | tag
- atributo
- universal

```css
p,
div,
header,
main {
} /*seletor de tag*/
#id {
} /*seletor de id */
.class {
} /*seletor de classe*/
[atributo] {
} /*seletor de um atributo*/
* {
} /*seletor universal*/
```

## Combinators

- descendent
  -- article a {}
- list
  -- mark, span {}
- next sibling
  -- h2 + p {}
- child
  -- aside > ul {}

```css
/*descendent: escolho uma tag dentro de outra tag, sendo mais específico*/
/*um espaço em branço entre eles*/
article p {
  color: blue;
}

/*list: vou colocando os seletores separados por vírgulas*/
mark,
span {
  color: red;
}

/*next sibling: ''irmão próximo''*/
/*leitura: basicamente => coloque a cor amarela na tag "p" cujo 'irmão' anterior é um "h2"*/
h2 + p {
  color: yellow;
}

/*child: determina o nível que quer aplicar as modificações*/
/*exemplo pega o primeiro nível ul abaixo do seletor aside*/
/*alguns atributos não funcionam - exemplo 'color'*/
aside > ul {
  margin-top: 60px;
}
```

## Adicionando CSS no HTML

- link:css
  -- tag link no head do html
