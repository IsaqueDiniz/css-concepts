# Position e Float

## Position

A propriedade `position` controla como e onde os elementos serão e estarão posicionados dentro do fluxo do documento. Ela aceita 4 valores: `static` (padrão), `relative`, `absolute`, `fixed` e `sticky`. Além disso,  o posicionamento do CSS pode ser trabalhado junto com o auxílio de outras 4 propriedades: `top`, `bottom`, `left`, `right` que controlam o deslocamento em relação a outro elemento ou ponto.

### `static`

Este posicionamento é o valor padrão do elemento, e não é afetado pelas propriedades de deslocamento e segue o fluxo normal do documento.

### `relative`

* O posicionamento `relative` permite trabalhar com as propriedades de deslocamento (usam **valores de comprimento ou porcentagem**);
* O posicionamento se dará relativamaente ao seu elemento ancestral; 
* O elemento só sairá do fluxo normal do documento caso as propriedades de deslocamento sejam definidas;
* Quando um elemento é definido com `position: relavive;` e ele tem as propriedades de deslocamento defindias, ou seja, ele visivelmente sairá do fluxo, o espaço que ele ocuparia no documento continuará preservado.

### `absolute`

* Permite trabalhar com as propriedades de deslocamento;
* Ao contrário do `position: relative;`, o espaço no fluxo normal do documento não é preservado e é colapsado;
* As propriedades de deslocamento serão relativas ao elemento mais próximo que não esteja definido como `static`;

### `fixed`

* Permite trabalhar com as propriedades de deslocamento;
* O espaço no fluxo normal do documento não é preservado e é colapsado;
* As propriedades de deslocamento serão relativas a janela do navegador;
* Os elementos não serão influenciados pela rolagem do mouse;


### `sticky`

* É uma mistura entre `fixed` e `relative`;
* Possui um comportamento `relative` até que o elemento ultrapasse um determinado limite que é definido com a propriedade `top`.
* Ao atingir o limite definido, o elemento se torna `fixed` e sai do fluxo normal do documento, e ao reecontrar as dimensões do seu elemento pai torna-se `relative` novamente.

### Z-Index

Existe a propriedade `z-index` que controla o deslocamento dentro do eixo *z*. Ela é útil para definir qual elemento será sobreposto sobre outro quando há mais de um com um posicionamento absoluto ou fixado. Ela aceita valores inteiros, os quanto maior o valor de um elemento em relação aos outros, mais acima ele estará dentro do documento.