# Caminhos Absolutos e Relativos

path => caminho
início (pasta padrão) => root

- Caminhos absolutos
  https://google.com/ = protocolo https + domínio
  -- file:// (referencia o 'meu computador')
  -- file://'/ a terceira barra representa o início do computador

- Caminhos Relativos
  -- caminho mais simples do que absolutos
  "./second.html" => o 'ponto-barra' referencia a mesma 'pasta' como 'origem' (pode ser suprimido)
  "../index.html" => subo um nível da pasta atual
  "/index.html" => nesse caso está buscando na raiz

- Protocolo correto (file, https) para busca dos arquivos ou páginas

# Caminhos absolutos e relativos em servidor

- servidor: protocolo http/https;
- localhost: http://127.0.0.1
- porta: 5500
- http://127.0.0.1:5500/ (este será o 'projeto' raiz)
