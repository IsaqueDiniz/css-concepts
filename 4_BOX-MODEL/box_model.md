# CSS Box Model

Analisando a disposição de elementos HTML dentro do documento, partindo da perspectiva da renderização e sendo mais especifico, a estilação desses elementos, vamos nos ater em como se dá o funcionamento, disposição, dimensionamento e relação dos elementos no documento que são estilizados pelo CSS.

Inicialmente, é importante considerar que os elementos HTML possuem propriedades que constituem o *Box Model*, como `width`, `height`, `padding`, `margin`, `border`, `display`. Todas essas propriedades se relacionam entre si para definir e formar as dimensões dos elementos.

## Relação entre as exibições e disposição interna e externa dos elementos

Os elementos HTML dentro do fluxo do documento possuem uma exibição interna e externa. A externa refere-se a forma que ele se relaciona com os outros elementos externos a ele, geralmente os elementos irmãos. Por outro lado, a exibição interna diz respeito a disposição e organização dos elementos internos desse elemento, ou seja, os elementos filhos.

No CSS, a propriedade que fará o controle de exibição interna e externa será `display` em função dos valores que a ele são definidos, isto é, existem valores de `display` que atuam internanamente, aos seus filhos, e outros valores que atuam externamente, influenciando na relação com os elementos irmãos.

Mais técnicamente: Existem valores de `display` que definem um elemento do tipo `block` bloco, `inline` em linha e `inline-block`, estes são exemplos que atuam no *outer display* (exibição externa). Há ainda, o `display:flex;` ou `display:grid;`, por exemplo, que definem um *inner display* (exibição interna). Mas, ainda assim, todos elementos possuem ao mesmo tempo uma exibição interna e externa, dessa forma, é possível definirmos propriedades para o *inner display* e o *outer display* permanecer com o valor padrão definido pelo agente de usuário (e.g. o navegador).

### Elementos inline e block

Como apresentado acima, a propriedade que controla a exibição dos elementos é `display`, que possui dois comportamentos ligados à *outer display*: `block` e `inline`.

Elementos em ***block*** possuem as seguintes características:

* Adicionam uma quebra de linha após o seu posicionamento no documento,
* se extenderão ao longo da linha que estão definidos para preencher todo o espaço disponível (considerando que um valor `width` ainda não foi definido),
* os valores de `width` e `heigth` são respeitados e
* `padding`, `margin` e `border` farão que outros elementos sejam afastados desse *box*.

Já os elementos ***inline*** possuem este comportamento:

* Não adicionam quebra de linha,
* os valores de `width` e `heigth` **não** são considerados,
* vertical `padding` , `margin` e `border` serão aplicados mas não afastarão outros elementos para longe e
* horizontal `padding`, `margin` e `border` serão aplicados e afastarão outros elementos.

Também existe o `inline-block`, que fornece um meio termo entre as duas opções: 

* Os elementos não quebrarão em uma nova linha,
* dimensões de `width` e `heigth`  serão respeitadas,
* `padding`, `margin` e `border` farão que outros elementos sejam afastados desse *box*.

## Box Model

O *Box Model* do CSS é baseado em, além dessas noções de exibição interna e externa: *Content Box*, *Padding Box*, *Border Box* e *Margin Box*. Essas quatro características definem o *Box Model* do CSS e trabalham juntas para definir as dimensões, posicionamento e aparência dos elementos na tela. Além disso, o *Box Model* se comporta de duas formas: o *Box Model* padrão e o alternativo.

* **Content box**: é a área onde o conteúdo do elemento é inserido, que  no *Box Model* padrão poderá ter suas dimensões alteradas a partir do `width` e `height`;
* **Padding box**: área que envolve a área de conteúdo como um espaço em branco, e suas dimensões podem ser controladas pelo `padding`;
* **Border box**: área que envolve a *Padding box*, e seu estilo e dimensões pode ser alterado e definido através da propriedade `border` e suas variações;
* **Margin box**: área que envolve todo o box externamente como uma caixa invisível ao seu redor, é definido e alterado pela propriedade `margin` e suas variações;

### Box-sizing

Considerando o seguinte exemplo: 

```css
.box {
	width: 100px;
	height: 100px;
	padding: 10px;
	border: 10px solid;
	margin: 10px;
}
```

Esse elemento que definimos acima, tendo o ***Box model padrão*** terá um comprimento total de `120px` pois é feito a soma das dimensões de `width`, `padding` e `border`. Esse tipo de comportamento é o padrão, que defindo com `box-sizing: content-box;` faz com que a *content box* seja definida por `width`, e dessa forma, `width` não representa o comprimento de fato, mas sim o comprimento da *content-box* e a *Padding box* se expandirá externamente.

Para alterar esse comportamento, e usarmos o ***Box model alternativo***, definimos `box-sizing: border-box;`, e dessa forma, quando definimos uma `width: 100px;` o nosso box terá exatos `100px` de comprimento e qualquer outros valores definidos no `border` e `padding` se expandirá internamente em direção a *Content box*. Vale a pena ressaltar que: caso o `padding` ou `border` sejam definidos ou se tornem maior que a `width` definida, mesmo que elas se expandam internamente comprimindo a *Content box*, ainda ocorrerá uma alteração nas dimensões da `width` e ela não mais representará o comprimento verdadeiro.