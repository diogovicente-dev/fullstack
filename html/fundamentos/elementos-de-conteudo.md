# Semântica

**Tags Semânticas**

- dar significado
- perguntar: o que eu preciso fazer? existe uma tag para isso?
  -- botão, título, lista, parágrafo, imagem, vídeo, ...
- elementos tem em si uma semântica
- mais de 100 elementos semânticos - html5 -, não necessário 'decorar'
- serve para SEO => _Search Engine Optimization_

# Títulos e Parágrafos

- tags relacionadas a textos no geral

**Título**

- tags <h1> até <h6>
- dica: geralmente 1 <h1> por página
- <p> - parágrafos
- <h2> a <h6> => subtítulos da página

# Formatação básica de textos

- <strong> => importância em algo do texto - funciona como negrito
- <em> => ênfase no texto - funciona como itálico
- <mark> => relevância no texto - funciona como um "marca texto" na página
- <s> => riscado => risca o texto 'no meio' - funciona para algo que 'não faz mais sentido' no texto (mudança de versão de documentação, por exemplo)

# Listas

**Não ordenada**

<ul> => lista não ordenada
<li> => item da lista
-- esta lista irá exibir uma lista com "pontinhos" - bulleted list

```html
<ul>
  <li>Item 1</li>
  <li>Item 2</li>
  <li>Item 3</li>
</ul>
```

**Ordenada**

<ol> => lista ordenada
<li> => uso a mesma tag ()
-- esta lista irá exibir uma lista numerada - numbered list

```html
<ol>
  <li>Passo 1</li>
  <li>Passo 2</li>
  <li>Passo 3</li>
</ol>
```

# Representação de código de computador

Como representar códigos de computador em htmml

- <code>
- <pre>
- caracteres especiais
- &lt; - lower than
- &gt; - greather than
- &amp; - "E" comercial => &
  Geralmente é incluída a tag <code> dentro da tag <pre>, pois esta última permite algumas formatações que o html normal não permite (espaços, quebras de linha)

```html
<pre>
  <code>Texto</code>
</pre>
```

# Hiperlink

- tag <a>
- atributos
  -- href="" => colocar uma url ou fragmento nesse atributo
  -- url = site normal
  -- fragmento = quando queremos levar para a mesma página, em um local específico (rolar a página, por exemplo)
  -- target="" => colocar "\_blank" para que abra uma nova janela/guia para não fechar o site atual

```html
<a href="https://rocketseat.com.br" target="_blank"> Link </a>

<a href="#fragmento"> Link </a>
```

# Imagens

- tag <img>
- atributos:
  -- src => imagem que será utilizada
  -- alt => alternative - se a imagem não puder ser carregada, ou para acessibilidade para pessoas que não enxergam
  -- width
  -- height

```html
<img
  src="https://source.unsplash.com/random"
  alt="descrever a imagem"
  width=""
  height=""
/>
```
