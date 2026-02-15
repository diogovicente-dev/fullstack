# Declaração CSS Moderna

**Nesting CSS**

No CSS, quanto utilizázamos dois ou mais seletores para estilizar um elemento específico era feito da seguinte forma:

```css
section {
  font-family: sans-serif;
}

section div {
  color: blue;
}
```

Com o avanço do css, podemos utilizar de forma diferente:

```css
section {
  font-family: sans-serif

  div {
    color: blue;
  }
}
```

No exemplo, o seletor `div` está dentro da declaração do seletor `section`

## Utilizando '&' - pseudo-elements

Para criação de `pseudo-elements`, por exemplo, com a declaração moderna de css, utiliza-se o '&':

- este & é como se fizesse a referência para ele mesmo

```css
/* CSS antes */

.card {
  font-family: sans-serif;
  position: relative;
}

.card::before {
  content: "";
  position: absolute;
}

/* CSS moderno */

.card {
  font-family: sans-serif;
  position: relative;

  &::before {
    content: "";
    position: absolute;
  }
}
```
