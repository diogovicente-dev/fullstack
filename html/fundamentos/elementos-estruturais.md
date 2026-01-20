# Anatomia de um documento HTML

- Estrutura Fundamental de um HTML

- <!DOCTYPE html>

  -- tag que identifica que o documento será do tipo html;

- <html>
  -- tag 'root', raiz do html
  -- dentro dessa tag tem duas tags essenciais
  -- <head> e <body>

- <head>
  -- configuração da página
  -- <title> => título da página
  -- <meta> => formatação de textos: charset="utf-8"

- <body>
  -- onde inserimos o conteúdo da página que será exibido no navegador

- dica: digitar "!" no vscode e dar 'enter'
  -- preenche o básico automaticamente

# Tags Header, Main, Aside e Footer

- nem sempre utilizamos todos estes
<header> cabeçalho da página, informações iniciais do site
<main> conteúdo principal da página
<aside> extensão do conteúdo principal ou ideia de demais conteúdos
<footer> rodapé com informações extras da página, contato, etc
- elementos gerais da página, <aside> pode ser usado ou não

# Tags Nav, Section e Article

<nav> navegação - colocar links, listas (home - contato - quem somos - projetos)
-- nav pode estar dentro ou fora do <header>
<section> serve para definir seções
-- por não ser tão específico, recomenda-se utilizar um 'id' para nomear a seção <section id="home">
-- recomendado: ter um <h2> para dar o título da section
-- section pode estar no <aside> também
<article> surgiu para artigos mesmo
-- pode ter <h2>, <section> dentro delas
-- geralmente está dentro do <main>

# Tags genéricas Div e Span

<div> e <span> são geralmente usados quando é necessário alguma configuração e estruturação com o uso de classes ou identificadores <div class="" id="">
-- tags genéricas que servem para estruturar mas não tem uma semantica
