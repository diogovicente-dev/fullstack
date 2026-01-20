# O que é HTML ?

**Hypertext Markup Language**

- 'tags' (marcação)
- não é uma 'linguagem de programação'
- links para outros textos / páginas
- imagens, sons, vídeos
- arquivos com extensão '.html'

# Comentários

- ignorar parte do texto do código

```html
<!-- Aqui é um comentário no html -->
```

# Anatomia das Tags

- 'tag' é a marcação do html
- abertura de tag
- fechamento de tag
- conteúdo
- elementos
- atributos

```html
<!-- o h1, img e br são alementos como um todo -->
<h1 id="title">Título 1</h1>
<img src="" alt="" />
<br />
```

- 'tags' sem conteúdo
- 'tags' apenas com atributos

# Espaços e quebras de linha

- 'tag' <br> para quebras de linha
- &nbsp => espaço no html
- prórprio elemento 'quebra' a linha
- com CSS é mas fácil do que fazer através do HTML

```html
<br />
&nbsp;
<!-- espaço -->
```

# Fluxo HTML

- um 'elemento' abaixo do outro
- block
  -- 'block' - ocupa todo o espaço da 'tela' e o próximo elemento será colocado abaixo
- inline
  -- elementos inline, um ao 'lado' do outro
  -- html já entende assim

# Aninhamento de Tags

- comportamento padrão do html é inserir tags dentro de tags
- tag 'pai' e tag 'filho'
- cuidar da abertura e fechamento de tags

```html
<p>Texto aqui <strong>dentro</strong>. <em> Texto aqui em ênfase</em></p>
```

# Caracteres reservados

- as próprias 'tags' são caracteres reservados da linguagem
- para 'aparecer', por exemplo, o sinal de mais e menos é necessário a utilização de forma alternativa
- difícil utilizar, mas se precisar é necessário entender que tem essas possibilidades

```html
<p>
  <code> &lt;p&gt; </code>
  <code> &amp;gt</code>
</p>
```
