# Atributos

- Informações extras e configurações para as tags

```html
<img src="" alt="" />
```

- o 'src' e 'alt' são atributos da tag 'img';
- cada atributo tem um valor que 'modifica' a tag de alguma forma, traz características diferentes, etc
- os valores dos atributos sempre ser inseridos entre "aspas duplas"

- Estudo constante sobre os atributos, é impossível saber tudo sobre; geralmente envolver estudo e pesquisa de acordo com a necessidade.
  -- atributos globais (para todas as tags)
  -- atributos específicos para cada tag

# Atributos booleanos

- Não precisam de conteúdo (booleano = verdadeiro ou falso)

```html
<h1 hidden>Título</h1>
```

- o atributo 'hidden' não precisa de valor por ser booleano

# Atributos globais

**Documentação**
https://developer.mozilla.org/pt-BR/docs/Web/HTML/Global_attributes

- atributo que pode ser usado em qualquer elemento (tag) do html
- entender os fundamentais e básicos inicialmente
- se for necessário, procurar em documentação específica

# Id

- atributo: id
- uso: identificar único para um elemento, para ser usado depois pelo CSS, JavaScript
- não repetir o Id para os demais elementos (tags)
- não iniciar o 'id' com número, não usar caracteres especiais, não usar espaços, ...

```html
<h1 id="titulo1">Título</h1>
```

# Class

- atributo: Class
- uso: classificação de elementos (elementos 'semelhantes') que compartilham propriedades semelhantes
- posso inserir mais de uma 'class' para cada elemento, conforme necessidade
- regras de escrita igual do id: não iniciar com números, sem espaços, sem caracteres especiais

```html
<h1 class="heading text-bold">Título</h1>
```

- nesse cenário, temos 2 classes: 'heading' e 'text-bold'

# Data-

- atributo: data-\*
- uso: também para utilização posterior
- no lugar do '\*' inserir o nome desejado para criação do atributo

```html
<h1 data-id="1258">Título</h1>
```

# Style

- atributo: style
- o que for colocado de estilo na tag é mais forte do que existir no CSS
- ideal evitar colocar os estilos na tag

```html
<h1 style="color: blue;">Título</h1>
```
