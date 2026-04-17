# CSS Animations and Transitions

- antigamente não tinha como usar CSS, era com FLASH ou apenas com JS (2008, 2009)
- site de animações
  - https://animista.net

## CSS Transition

- suavidade ao mudar o valor de uma propriedade
- faz a transição a partir de um 'disparo' = `trigger`
- por exemplo o `hover` de um elemento em css
- posso colocar a `transition` tanto no elemento quanto no `trigger`, só tomar cuidado como vai ficar a transição
  -- pode acontecer de não funcionar conforme esperado

**transition-property**: escolho qual a propriedade eu quero transicionar;
-- é possivel utilizar `transition-property: all`, porém não recomendado, usar propriedade específica
**transition-duration**: escolho quanto tempo a transição irá durar (em segundos ou milissegundos);
**transition-delay**: tempo de espera para antes de iniciar e finalizar a transição (em segundos ou milissegundos);
**transition-timing-function**: curva de aceleração para a transição ir do início ao fim
-- valores:
--- `linear`
--- `ease`
--- `ease-in`
--- `ease-out`
--- `ease-in-out`
--- `steps()`: transição em 'passos'
--- `cubic-bezier()`: x1, y1, x2, y2
-- https://cubic-bezier.com

```css
div {
  opacity: 0.6;

  transition-property:
    opacity, transform; /* coloco quais propriedades quero transicionar */
  transition-duration:
    1s, 200ms; /* o tempo de cada um pode ser separado, se um só aplicada para tudo */
  transition-delay: 1s, 10ms; /* mesmo cenário de tempo para as propriedades */
  transition-timing-function: linear; /* linear - padrão */
  transition-timing-function: ease-in; /* ease e linear são 'atalhos' para o cubic-bezier */
  transition-timing-function: cubic-bezier(0.7, 0.08, 0.85, 1.37);
  transition-timing-function: steps(5);
}

div:hover {
  opacity: 1;
  transform: translateX(20px);
}
```

**transition** - shorthand

```css
div {
  transition: all 400ms 2s ease;
  /* primeiro valor o atributo */
  /* segundo valor a duração da transição */
  /* terceiro valor (se numérico) é o delay */
  /* quarto valor o tempo de duração */

  transition:
    opacity 1s ease,
    transform 400ms linear;
}
```

- Se o usuário optar por não ver transições ou animações, como fazer?
- `prefers-reduced-motion`
- aplicar no @media no css
- simular na ferramente de desenvolvedor
  - `CRTL + P` > digitar `reduced` > emulate reduced-preferes-motion

```css
@media (prefers-reduced-motion) {
  div {
    transiton: none;
  }
}
```

## CSS Animation

- mudança de propriedade baseado numa linha do tempo - início e fim
- como fazer?
- criar a linha do tempo - `@keyframes`
  -- valores: usar `from - to` (usar 1 ou 2 valores), `0% a 100%` (usar mais de dois valores)
- usar a linha do tempo - `properties`
  -- precisa de no mínimo 2: `animation-name` e `animation-duration`
  --- **animation-name**: nome da keyframe criada
  --- **animation-duration**: tempo de duração da animação (timeline)
  --- **animation-delay**: tempo que irá esperar antes de iniciar a animação
  --- **animation-fill-mode**: uso das propriedades iniciais e finais
  ---- `backwards` => mantém as propriedades iniciais: antes de iniciar a animação, as propriedades que estiverem no início da animação (0%, ou from), serão 'puxadas' para o elemento
  ---- `forwards` => mantés as propriedades finais: pega a última configuração do `@keyframes` e mantém no elemento
  ---- `both` => puxa propriedades iniciais e mantém as propriedades finais: backwads e forwards simultaneamente
  --- **animation-direciton**: altera a direção da linha do tempo
  ---- `alternate`: alterna a linha do tempo (vai de um jeito ou de outro) - faz mais sentido usando junto com o _iteration-count_ => quantas vezes executa a animação
  ---- `reverse`: reverte a linha do tempo
  ---- `alternate-reverse`:
  --- **animation-iteration-count**: quantas vezes irá executar a animação (pode ser numérico ou `infinite`)
  --- **animation-play-state**: ativa ou desativa a animação
  ---- `running`: padrão (animação ativa)
  ---- `paused`: interrompe a animação quando existir algum disparo - `trigger`
  --- **animation-timing-function**: curva de aceleração da animação (semelhante à transição)
  ---- `linear`, `ease(in, out, in-out)`, `steps()`, `cubic-bezier()`

  -- shorthand: animation: _name_ _duration_ _delay_ _fill-mode_ _direction_ _iteration-count_ _timing-function_
  --- _play-state_ fica em outro elemento

  -- comportamento padrão: ao iniciar a aplicação, a animação roda e, ao terminar, volta para o estado inicial

```css
button {
  animation-name: move;
  animation-duration: 1s;
  animation-delay: 5s;
  animation-fill-mode: forwards;
  animation-direction: reverse;
  animation-iteration-count: 3;
  animation-timing-function: ease-in;

  /* shorthand */
  animation: move 1s 5s both alternate infinite ease-out;
}

button:hover {
  animation-play-state: paused; /* mudar o estado da animação */
}

/* colocar um nome para o keyframe */
@keyframes move {
  /* propriedades de saída - from */
  from {
    transform: translateY(
      0
    ); /* nesse caso, a posição inicial já existe, não precisa ter o from, só o 'to' é suficiente*/
  }
  /* propriedades de chagada - to */
  to {
    transform: translateY(300px);
  }
}

@keyframes moving {
  /* em %, significa o % do tempo da animação que vai executar */
  25%,
  50% {
    transform: translateY(300px);
  }

  30%,
  60% {
    transform: translateY(0);
  }
}
```

## Futuro das Animações

- **animation-timeline**: controlar a timeline de duas formas diferentes:
  - scroll() - início e fim controlado pela rolagem do scroll()
  - view() - viweport - elemento aparecendo ou não na tela

- `caniuse`: não é aplicável para todos os navegadores hoje (17/04/2026) - https://caniuse.com/?search=animation-timeline

- **SCROLL**

-- quanto maior o scroll, maior o tempo da animação
-- argumentos => direção do scroll (`y` ou `block`) é o scroll padrão; `x` ou `inline` é o scroll horizontal

- **VIEW**

-- início e fim da animação, baseado na visibilidade do elemento na viewport
-- animação inicia quando o elemento aparecer na viewport, e termina quando sai da viewport
-- argumentos =>
--- deslocamento do topo: finaliza a animação assim que o elemento chegar a X do topo = `top`
--- descolamento do fundo: inicia a animação assim que o elemento se deslocar X do fundo = `bottom`
--- unit => _px_, _rem_, _percentage_
--- se apenas 'um valor', deslocamento `top` e `bottom`
-- **animation-range**: _start_ e _end_ - sempre em relação ao 'fundo' - bottom
--- `start`: inicia em relação ao bottom
--- `end`: termina em relação ao bottom
--- units
---- px, rem e percentage
---- `contain` => elemento completamente visível na viewport, se sair dos limites não esta mais contido; animação inicia quando todo o elemento estiver na viewport e finaliza logo que o 'topo' do elemento começar a sair da viewport
---- `cover` => elemento começou a aparecer na viewport começa a animação e termina ao sair totalmente da viewport
---- `entry` => inicia a animação ao começar a aparecer na viewport e termina quando finalizar de entrar na viewport
---- `exit` => inicia assim que o elemento começar a sair da viewport e finaliza quando o elemento sair totalmente da viewport

```css
article > img {
  animation: fade linear; /* não coloca o tempo porque quem vai controlar é o scroll  */
  animation-timeline: scroll();
  animation-timeline: scroll(y);
  animation-timeline: scroll(inline);

  animation-view: ();
  animation-view: (50% 100px);
  animation-view: (200px 100px);
  animation-view: (200px); /* aqui aplica para os dois */

  animation-range-start: 10px;
  animation-range-end: 100px;

  animation-range: 10px 100px /* start + end */

  animation-range: contain;
  animation-range: cover;
  animation-range: entry;
  animation-range: exit;

  animation-range: contain 100px; /* para iniciar tem que estar em tela e a 100px de offset do bottom */
  animation-range: 100px; /* padrão é 'cover', inicia observando apenas o deslocamento bottom */
  animation-range: 100px 200px; /* start e end */
}

@keyframes fade {
  0% {
    opacity: 0;
  }

  100% {
    opacity: 1;
  }
}
```

## Questões

- As CSS Transitions são ideais para criar transições suaves entre estados de um elemento quando uma propriedade CSS muda seu valor, como um hover. Elas são, em sua essência, projetadas para transições simples de um estado a outro. Já as CSS Animations são mais poderosas, permitindo a criação de sequências de estilo complexas com múltiplos estágios (keyframes), controle de repetição e atraso, sem a necessidade de um gatilho como uma mudança de propriedade, podendo iniciar automaticamente ao carregar a página ou serem controladas via JavaScript.

- A propriedade animation-duration é a propriedade CSS correta usada para especificar quanto tempo uma animação leva para completar um ciclo. Você define a duração em segundos (s) ou milissegundos (ms), por exemplo, animation-duration: 2s;.

- A propriedade animation-delay em CSS é utilizada para especificar um atraso antes que uma animação comece sua execução. O valor é dado em segundos (s) ou milissegundos (ms), permitindo controlar precisamente o momento de início da animação.

- Você identificou a sintaxe correta para a propriedade transition. Ao usar transition: background-color 0.5s;, você especifica que a transição deve ser aplicada à propriedade background-color e que a duração dessa transição deve ser de 0.5 segundos. Quando a background-color do elemento mudar (por exemplo, ao passar o mouse), essa mudança ocorrerá suavemente ao longo do tempo especificado.

- A propriedade CSS transform é fundamental para realizar alterações visuais em elementos HTML, permitindo manipulações como rotate() (rotação), translate() (translação/movimentação), scale() (dimensionamento/escala) e skew() (inclinação), entre outras, sem afetar o fluxo do documento.

- A propriedade transition-duration é a responsável por definir o tempo que uma transição CSS leva para ser concluída. Neste caso, 0.5s significa que a mudança de cor do botão levará meio segundo para acontecer, criando um efeito suave e gradual quando o mouse passar sobre ele e quando ele sair.
