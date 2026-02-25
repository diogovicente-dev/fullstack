# HTML Forms

Por que?

- capturar dados (_input_)
- interação com os usuários
- controle

## <form>

- <form> é um elemento HTML
- atributos:
  - `action` > para onde os dados serão enviados
  - `method` > método para enviar os dados
    - `GET` > as informações são enviadas na url do navegador
      - exemplo: `{url}/user?id=20&nome=diogo`
    - `POST` > as informações ficam ocultas, não são expostas na URL (são enviadas pelo backend)

- por padrão, o formulário usa a `action` enviar para a mesma página e o método `get`

```html
<form action="" method="get">
  <button>submit</button>
</form>
```

## <button>

- tag vem com o padrão do **User Agent**
- atributos:
  - `type`
    - `submit`
      - uma tag <button> dentro de um <form>, por padrão, sempre será utilizado para enviar o formulário; por padrão do tipo _submit_;
      - envia os dados do formulário
    - `reset`
      - limpa o conteúdo do form
    - `button`
      - simplesmente um button, não faz as demais ações
  - `autofocus`
    - foca automaticamente no botão ao abrir a página (nem todos os navegadores aplicam corretamente)
  - `disabled`
    - tipo booleano: desativa o botão.
    - exemplo: enquanto estiver digitando o formulário, não pode enviar os dados (precisa de JavaScript para aplicar)
  - `name` e `value`
    - atributos que enviam as informações do botão na requisição (indicar para a aplicação que foi clicado no botão A ou botão BN)

```html
<button type="submit"></button>
<button type="reset"></button>
<button type="button"></button>
<button autofocus></button>
<button disabled></button>
<button name="botao1" value="valor_do_botao_1"></button>
```

## <input>

- umas das tags mais poderosas, muitas combinações, aceita uma variedade de dados
- estilos definidos pelo **user agent**

### <input> text

- **atributos fundamentais**
  - `name` => valor do input ao enviar o formulário, caso seja necessário obter os dados do formulário
  - `type` => define o tipo de dado do input

```html
<form>
  <input type="text" name="nome" />
</form>
```

- **atributos gerais**
  - `value` => valor por padrão
  - `autocomplete` => dependendo o navegador traz opções pra completar
  - `size`! => tamanho (não recomendado, usar no css)
  - `autofocus` => abre o formulário, o campo fica 'focado'
  - `disabled` => campo fica desabilitado
  - `readonly`! => apenas 'leitura', o valor não pode ser alterado
  - `form`! => link com outro formulário (`id` do formulário)
  - `required`! => campo obrigatório
  - `placeholder`! => uso comum => um 'valor' (não o value) para informar o usuário ao que fazer

### <input> number

- apenas números
  - `type`: number
- atributos
  - `min` => valor mínimo
  - `max` => valor máximo
  - `step` => quanto a numeração 'pula', 2 em 2, 3 em 3

```html
<form>
  <input type="number" min="2" max="20" step="2" />
</form>
```

- testar **atributos gerais** para verificar se funciona: `required`, `placeholder`, ...

### <input> e-mail

- validar um e-mail (formato 'padrão')
- `type="email"`

- atributos
  - `name` => nome obrigatório
  - `multiple` => permite mais de um email (separado por vírgulas)
  - `minlength` => tamanho mínimo
  - `maxlength` => tamanho máximo
  - `pattern` => expressão regular para validar o campo
  - `title` => se der algum erro mostra a mensagem para o user

```html
<form>
  <input
    type="email"
    name="mail"
    multiple
    minlength="5"
    maxlength="10"
    pattern=".+@rocketseat\.com\.br"
  />
</form>
```

- existem maneiras mais avançadas com JS para validação de emails

### <input> password

- senhas
- `type="password"`
- atributos
  - `minlength` => tamanho mínimo
  - `maxlength` => tamanho máximo
  - `pattern` => expressão regular para validar o campo
  - `inputmode` => "_numeric_" no celular vai liberar apenas o 'teclado numérico' para inserção da senha
  - `title` =>

```html
<form>
  <input
    type="password"
    name="senha"
    pattern="[#0-9a-fA-F]{4,8}"
    title="apenas hexadecimal"
  />
  <!-- input mode numeric no celular -->
</form
```

- método post para não passar a senha pelo frontend!!

### <input> file

- vai enviar um ou mais arquivos pelo formulário
- `type="file"`
- para funcionar corretamente, no <form> deve existir o atributo `enctype="multipart/form-data"`
- atributos
  - `value` (backend)
  - `files` (backend)
  - `multiple` => para enviar múltiplos arquivos
  - `accept` => tipos de arquivos aceitos
    - ".doc" | "image/\*" | audio/mp3

- deve usar o método post para envio dos arquivos

```html
<form enctype="multipart/form-data">
  <input type="file" name="foto-perfil" accept="audio/*" />
</form>
```

### <input> range

- controle para selecionar um valor numérico
- slider, dial control
- padrão de 0 a 100
- `type="range"`
- atributos
  - `min` => mínimo
  - `max` => máximo
  - `step` => quanto pula
  - `name`
  - `value` => valor quando é 'resetado'

```html
<form>
  <input type="range" min="0" max="200" step="10" />
</form>
```

### <input> color

- `type="color"`
- interface para selecionar 'cor' - colorpicker
- atributos
  - `value` => valor padrão
  - `list` => <datalist> => <option>

```html
<form>
  <datalist id="colorpicker">
    <option value="#7cb8b7"></option>
    <option value="#c5dfde"></option>
  </datalist>
  <input type="color" name="color" value="#0facaa" list="colorpicker" />
  <!-- vinculando o input com o datalist pelo 'id' colorpicker -->
</form>
```

### <input> checkbox, radio e hidden

- `type="checkbox"`
- seleção de valor, é enviado `on` se a caixinha for selecionada
- atributos
  - `value` => se colocar o valor, em vez de enviar 'on' envia 'o value'
  - `checked` => coloca por padrão 'selecionado'

- `type="radio"`
- projetado para selecionar apenas uma opção de um grupo de opções
- atributos
  - `value` => se colocar o valor, em vez de enviar 'on' envia 'o value'
  - `checked` => coloca por padrão 'selecionado'

- `type="hidden"`
- deixar o campo 'escondido' no frontend, passar um 'id' fixo, por exemplo, de um formulário

### Novos inputs

- documentação sempre
- https://caniuse.com
- https://devdocs.io
- exemplos: date, date-time, ...

## <label>

- os leitores de tela não conseguem 'ler' o atributo `placeholder` nos inputs
- por padrão, vincular um <label> a um <input>, por questão de acessbilidade
- vincular de 2 maneiras:
  - adicionando o atributo `for` à tag <label> e `id` à tag <input> com o mesmo valor
  - colocar a tag <input> como filha da tag <label>
- como atualmente os campos usam mais o 'placeholder' para descrever o que deve ser preechido, o 'label' é escondido através do css.

```html
<form>
  <!-- caso 1 - uso preferencial pelo Mayk - adotar como padrão então -->
  <label for="nome">Nome</label>
  <input type="text" name="nome" id="nome" placeholder="Coloque o seu nome" />

  <!-- caso 2 -->
  <label>
    Nome
    <input type="text" name="nome" placeholder="Coloque o seu nome" />
  </label>
</form>
```

## <textarea>

- tag <textarea>
- textos grandes
- atributos
  - `name`
  - `rows` => ajustar via css
  - `cols` => ajustar via css
  - `maxlength`
  - `minlength`
  - `wrap` => quebra a linha (off para não quebrar)
- outros atributos do input são usados aqui = required, placeholder, ...

## <select>

- precisa de opções
- atributos
  - `multiple` => seleciona mais de uma opção
  - `size` => como quero exibir
  - `optgroup` => agrupa opções

```html
<form>
  <select name="car">
    <optgroup label="esportivo">
      <option label="BWM" value="bwm"></option>
      <option label="Audi" value="audi"></option>
    </optgroup>
    <optgroup label="nacional">
      <option label="Fiat" value="fiat"></option>
    </optgroup>
  </select>
</form>
```

## <fieldset>

- agrupamentos de campos
- campos com o mesmo propósito
- atributos
  - `legend` => nome do agrupamento
- bom para acessibilidade e leitores

```html
<form>
  <fieldset>
    <legend>Contato</legend>
    <input type="text" name="nome" />
    <input type="email" name="mail" />
  </fieldset>
</form>
```

## Revisão

- Validações: JavaScript
- Aparência dos Campos: CSS/Javascript
