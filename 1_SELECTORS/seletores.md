# Seletores CSS

## O que são?
Na CSS, seletores são combinações que associam uma ou mais regras de estilo, para um ou mais elementos.

```css
p {
	color: blue;
	text-align: center; 
}
```

Na CSS, seletores são combinações que associam uma ou mais regras de estilo, para um ou mais elementos.

O exemplo acima é um conjunto de regras. **Um conjunto de regras CSS consiste em um seletor e um bloco de declarações**. A função do seletor é aplicar os estilos definidos nas declarações a um determinado elemento. Nesse caso, estamos aplicando ao elemento `p` uma cor de texto azul (`color : blue;`) e um alinhamento de texto no centro (`text-align: center`).

Todo o conjunto de regras é constituído de seletor e bloco de declarações, sendo o último formado por **propriedade e valor da propriedade.** No nosso exemplo, as propriedades declaradas são `color` e `text-align`, e seus valores de propriedade são `blue` e `center`, respectivamente. Já o nosso seletor é a própria indicação do elemento `p`.

Em suma:

* Conjunto de Regras: 
```css
p {
	color: blue;
	text-align: center; 
}
```
* Seletor: `p`
* Bloco de declarações:
```css
{
	color: blue;
	text-align: center;
}
```
* Propriedades: `color` e `text-align`
* Valores de propriedade: `blue` e `center`



## Seletores Básicos

Do mais simples para o mais complexo, os seletores básicos CSS podem ser dividos entre:
* Seletor Universal,
* Seletor de Tipo,
* Seletor de Classe,
* Seletor de ID e
* Seletor de Atributo.


### Seletor Universal
Este seletor se associa com todos os elementos no documento HTML.
```css
* {
	color: red;
}
```

### Seletor de Tipo
Este seletor se associa com um determinado tipo de elemento. No nosso exemplo ele se aplica aos elementos `div`:
```css
div {
	width: 300px;
}
```

### Seletor de Classe
Se associa com uma classe que está ligada a um ou mais elementos no documento HTML. Neste exemplo, se aplicará a todos os elementos marcados com a classe `minha-clase`.

```xml
<p class="minha-classe outra classe">···</p>
<h1 class="minha-classe">···</h1>
```

```css
.minha-classe {
	background: skyblue;
}
```
Nessa situação, a estilização se aplicará aos dois elementos no documento HTML, pois estão marcados com a classe `minha-classe`


### Seletor de ID
Considerando a regra do HTML de que o valor do atributo  `id` para um elemento dever ser único a esse elemento, ou seja, ele não se repetirá em outros elementos, no CSS segue-se a mesma ideia, que um seletor assinalado com um ID aplicará regra apenas aquele elemento.

```xml
<div id="meu-ID">···</div>
```
```css
#meu-ID {
	background: pink;
}
```


### Seletor de Atributo

A ideia geral dos seletores de atributo é de que as regras serão aplicadas em função da presença de um atributo ou por determinado valor que ele contém.

####  `elemento[atributo]`
Contém determinado atributo.
```css
input[required] {}
```
Seleciona todos os elementos `input` que possuem o atributo `required`:

#### `elemento[atributo=valor]`
Contém um atributo com valor exato.
```css
a[="Alguma informação"] {}
```
Seleciona todos os elementos `a` que possuem um atributo `alt` exatamente igual a `"Alguma informação"`:

#### `elemento[atributo=valor i]`
Contém um atributo com valor exato².
```xml
<a alt="ALgUMA InfORMAÇãO">···</a>
```
```css
a[alt="Alguma informação i] {}
```
Seleciona todos os elementos `a` que possuem um atributo `alt` exatamente igual a `"Alguma informação"` **sem considerar maiúsculas ou minúsculas**:

#### `elemento[atributo~=valor]`
Contém um valor em uma lista de valores separados por espaço.
```xml
<a alt="Alguma informação">···</a>
```
```css
a[alt~="informação"] {}
```
Devido ao elemento `a` possuir o atributo `alt`, e em seu valor estar uma lista de palavras **separas por espaço** e uma dessas palavras corresponder com o seletor, então os estilos serão aplicados nesse elemento.

#### `elemento[atributo|=valor]` 
O valor ou o valor seguido de um hífen, no ínicio de uma lista de palavras separadas por espaço.
```xml
<div lang="pt-br">···</div>
```
```css
div[lang|="pt"] {}
```
Neste exemplo o elemento `div` possui um atributo `lang` o qual seu valor começa com uma palavra seguida exatamente de **hífen**.

Nesse caso o estilo tambem será aplicado:
```xml
<div lang="pt">···</div>
```

#### `elemento[atributo^=valor]`
Atributo que começa exatamente com o valor fornecido.
```xml
<a alt="Alguma informação">···</a>
```
```css
a[alt^="Alguma"] {}
```
Neste nosso exemplo, o elemento `a` tem um atributo que começa exatamente com o requerido no seletor: `alt="Alguma"`

#### `elemento[atributo$=valor]`
Atributo que termina exatamente com o valor fornecido.
```xml
<a alt="Alguma informação">···</a>
```
```css
a[class$="ção"] {}
```
Neste nosso exemplo, o elemento `a` possui um atributo que termina exatamente com o requerido no seletor: `alt="ção"`

#### `elemento[atributo*=valor]`
Qualquer ocorrência do valor indicado.
```xml
<a alt="Alguma informação">···</a>
```
```css
a[alt*="gum"] {}
```
Os estilos serão aplicados, pois nessa situação o elemento `a` tem um ocorrência de `"gum"` no atributo `alt`.

## Utilizando Seletores

Para que possamos utilizar os seletores de forma mais apropriada, podemos fazer combinações entre eles, o que torna o processo de estilização mais preciso.

De modo a entender o funcionamento adequado dos seletores dentro de um documento HTML, é necessário observar a **árvore do documento** e as relações entre os seus elementos.

Todo elemento herda propriedades do elemento `html` que é o pais de todos os elementos, ou seja, a raiz do documento. Da mesma forma, todo elemento tem um pai, que herdará desse outras propriedades que lhe é possível.

Considere o seguinte documento HTML:
```xml
<html>
···
<body>
	<div>
		<p>Lorem ipsum <em>dolor sit amet</em></p>
    	<a href="https://example.org">···</a>
	</div>
</body>
</html>
```
Neste exemplo o ancestral comum e pai de todos os elementos é o `html`, e `body` é o ancestral de todos os elementos que são renderizados na página, `div` herda de `body` e tem dois **filhos diretos**: o elemento `em` é descendente de `div` mas não diretamente, ou seja, os filhos diretos de `div` são os elementos `p` e `a`, e `em` é filho direito de `p` mesmo sendo descendente de `div`.

É importante ressaltar que nem todas as propriedades do CSS são herdáveis e o objetivo de utilizar a herança no CSS é evitar repetição de propriedades em vários conjuntos de regras ao longo da folha de estilo.

Eis as combinações mais básicas entre seletores, e partir dessas combinações é possível fazer outras utilizando os mesmo raciocínio junto com a noção de herança e a relação dos elementos no documento HTML:

```css
h1.minha-classe {}
/*Seleciona todos os elementos h1 marcados com uma classe chamada 'minha-classe'*/

h1#meu-ID {} 
/*Seleciona todos os elementos h1 marcados com um id 'meu-ID'*/

div p {}
/*Seleciona todos elementos 'p' dentro do elemento div*/

p > span {}
/*Seleciona os elementos span filhos direito de 'p'*/

h1 + p {}
/*Seleciona os elementos 'p' que são irmãos imediatamente após h1*/

h1 ~ ul {} /*GENERAL sibling */
/*Qualquer elemento irmão*/

```
## Pseudo-classes e Pseudo-elementos

Dentre os Seletores CSS, existem os pseudo-elementos e pseudo-classes, que cumprem o papel de extender a marcação do documento, como é o caso dos pseudo-elementos, ou aplicam estilos durante um estado de determinado elemento, como é o caso das pseudo-classes.

> Pseudo-elementos criam elementos fora da marcação
> HTML, e as pseudo-classes aplicam estilos baseados no
> estado.

### Pseudo-elementos

Os pseudo-elementos tem uso simples e direto, entre eles existem o `::after` e `::before` que permitem inserção de elementos HTML na página mesmo que não estejam na marcação do documento.

```css
ul::after {
	content: "content";
}/*Cria um elemento imediatamente após o especificado. É possível especificar um conteúdo com a propriedade 'content'*/ 

ul::before {
	content: "content" ;
} /*Cria um elemento imediatamente antes do especificado, também possui a propriedade 'content'*/

ul::first-line {}
/*Primeira linha de um elemento bloco*/

ul::first-letter {}
/*Primeira letra de um elemento bloco*/

#input::placeholder {}
/*Trabalha em cima da propriedade placeholder do elemento input*/

ul::marker {}
/*Trabalha nos elementos de marcação de uma lista*/

*::selection {}
/*Atua sobre a estilização durante a seleção feita pelo usuário*/
```
### Pseudo-classes

Entre as pseudo-classes existem duas que se destacam: `:nth-child()` e `:not()`. Para o nosso entendimento, considere o seguinte exemplo:
***

```xml
···
<h1></h1>
<p></p>
<a></a>
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>5</li>
	<li>6</li>
	<li>7</li>
</ul>
···
```
Existe uma grande variedade de pseudo-classes, confira todas ela na documentação da [MDN](https://developer.mozilla.org/en-US/docs/Web/CSS/Pseudo-classes "Pseudo-classes - MDN").

```css
a:active, button:active {}
/*Atua no momento da ativação do elemento*/

:checked {}
/*Atua sobre todos os elementos input[type="radio"], input[type="checkbox"]* ou option do elemento select que estão ativados*/

input:disabled {}
/*Seleciona os elementos que estão desabilitados*/

:empty, p:empty, *:empty {}
/*Qualquer elemento que não tenha filhos, conteúdo e espaço em branco*/

:enabled { }
/*Representa um elemento ativado ou que recebeu foco*/

a:first-child {}
/*Primeiro filho do seu pai*/

a:first-of-type {}
/*Primeiro elemento em um lista de elementos do mesmo tipo*/

input:focus {}
/*Atua quando o elemento recebe foco pelo usuário*/

a:hover {}
/*Elemento que o ponteiro está sobre*/

input:invalid {}
/*Elemento de formuário que está inválido*/

a:last-child {}
/*Último elemento de uma lista de irmãos*/

a:last-of-type {}
/*Último elemento de uma lista do mesmo tipo*/

:link {}
/*Seleciona elementos que possuem atributo 'href' e que não tenham sido visitados*/

a:only-child {}
/*Seleciona um elemento caso ele seja filho único*/

a:only-type() {}
/*Seleciona um elemento caso ele não tenha irmãos do meso tipo*/

a:optional {}
/*Qualquer elemento que não tenha o atributo required*/

:root {};
/*Seleciona a raiz do documento*/

input:required {}
/*Elemento de formulário com atributo required*/

input:valid
/*Elemento de formulário válido*/

a:visited {}
/*Seleciona um link que já foi visitado pelo usuário
```