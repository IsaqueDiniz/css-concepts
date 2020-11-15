# Unidades de medida

## Conceito

Toda propriedade nas CSS possui um valor que definine seu funcionamento. Tal valor, é caracterizado por uma unidade de medida, que estão ligadas à propriedades específicas, não sendo possível atribui-las para outras propriedades. Por exemplo, a propriedade `background-color` não aceita o valor `10px`, pois este não define uma cor e sim um comprimento.
## Tipos de dados
Dentro das especificações, os tipos de dados da CSS são definidos entre colchetes, e.g. `<color>`.

Tipo de dados | Descrição
--------------|-----------
`<integer>` | número inteiro, como 512 ou 15.
`<number>`	| representa um número decimal. Por exemplo,  0.30  -1.2.
`<dimension>` |	é um `<number>` com uma unidade anexada a ele. Por exemplo,  45deg, 5s, ou 10px. `<dimension>`é uma categoria abrangente que inclui os tipos `<length>`, `<angle>`, `<time>`, e `<resolution>`.
`<percentage>` |	A `<percentage>`representa uma fração de algum outro valor. Por exemplo  50%,. Os valores percentuais são sempre relativos a outra quantidade. Por exemplo, o comprimento de um elemento é relativo ao comprimento de seu elemento pai.

### Comprimento

Os valores de comprimentos são os mais usados e são representados por `<length>`.

#### `<length>` absolutos
Valores de comprimentos absolutos não são relativos a nada e sempre representarão as mesmas dimensões.

Unidade	| Nome	| Equivalente a
--------|-------|---------------
`cm`	|Centimetros	|1cm = 96px / 2,54
`mm`	|Milímetros	1mm = |1/10 de 1cm
`Q`	|Quarto de milímetro	|1Q = 1/40 de 1 cm
`in`	|Polegadas	|1in = 2,54cm = 96px
`pc`	|Paica	|1pc = 1/6 de 1 pol.
`pt`	|Pontos |	1pt = 1/72 de 1 pol.
`px`	|Píxeis	|1px = 1/96 de 1 pol.

##### O pixel das CSS o pixel do dispositivo

Existe um diferença entre a **resolução da CSS** a **resolução dos dispositivos**. Enquando a primeira serve para cálculos internos da CSS a segunda representa o atual número de pixels na tela. Lembrando que, resolução é quantidadade de pixels que há em uma linha e uma coluna. Dessa forma, se considerarmos a tela de um celular e a tela de um monitor, chegamos a conclusão que eles terão resoluções diferentes, ou seja, quantidade de pixels diferentes, pois suas dimensões físicas são diferentes. Esse raciocínio poderia fazer sentido caso não existe celulares e monitores com resoluções iguais mesmo que seus tamanhos sejam diferentes. É perfeitamente razoável encontrar celulares com a mesma resolução de um monitor, e esse comportamento denota que para diferentes tipos de telas haverá diferentes quantidades de pixels dispostas em quantidade de espaço iguais entre sí.

Essse comportamento é chamado de *densidade de pixel*, que diz respeito a quantidade de pixel em determinado espaço físico, geralmente uma polegada, que é representado por *ppi* (pixels per inch). Enfim, densidade de pixel ou densidade de tela, é a proporção entre a resolução da tela e a resolução das css. Observe os seguintes exemplos:

Dispositivo 		| Pixels CSS | Pixels na Tela | Densidade
--------------------|:-------------:|:--------------:|:--------:
iPhone 11 | 1 | 2 | 2x
iPhone 11 Pro | 1 | 3 | 3x
Samsung Galaxy S10 |1| 4 | 4x

Sendo assim, os dimensões físicas da tela e o *ppi* são inversamente proporcionais: quanto maior a tela, menor será o *ppi*; quanto menor a tela, maior será o *ppi*.

#### `<length>` relativos
Valores de comprimentos relativos são relativos à outra coisa, por exemplo ao elemento pai ou às dimensões de tela. Uma das vantagens de se usar tamanhos relativos é tornar as dimensões dos elementos flexíveis, mas se faz necessário um planejamento cauteloso para tal.

Unidade | Relativo a
--------|----------
`em`	|Tamanho da fonte do pai, no caso de propriedades tipográficas como `font-size`, e tamanho da fonte do próprio elemento, no caso de outras propriedades como width.
`ex`	|altura x da fonte do elemento.
`ch`	|A medida de avanço (largura) do glifo "0" da fonte do elemento.
`rem`	|Tamanho da fonte do elemento raiz.
`lh`	|Altura da linha do elemento.
`vw`	|1% da largura da janela de visualização.
`vh`	|1% da altura da janela de visualização.
`vmin`  |1% da dimensão menor da janela de visualização.
`vmax` 	|1% da dimensão maior da janela de visualização.

### Porcentagens `%` `<percentage>`

Porcentagens são os valores de unidade relativada mais utilizado, simples e flexível. Na sua aplicação, ele considera o elemento ancestral mais próximo (na maioria dos casos o elemento pai), ou valor de propriedade que pode ser calculado e aplicado.

```css
.parent	{
	width: 400px;
}
.child	{
	width: 50%;	/*=200px*/
    padding: 50%; /*100px*/
}
```

A portecentagem pode simular qualquer outro tipo de valor, como `<length>` ou `<dimension>`, pois ela sempre retornará um valor relativo em quantidade e tipo de dado aplicado no elemento ancestral.

### Números

Há muitas propriedades que aceitam apenas um número como valor. Um exemplo disso é propriedade `opacity`:
```css
.box {
	opacity: 0.35;
}
```

Quando trabalhamos com números no CSS estes valores não podem estar dentro de aspas.

## Cores

Há várias maneiras de se trabalhar com cores no CSS, mas vamos nos ater as formas principais de fazê-lo.O sistema de cores padrão dos computadores são baseados em 24 bits, o que permite apresentar 16,7 milhões de cores diferentes nos canas vermelho, azul e verde com 256 cores diferentes por canal (256 x 256 x 256 = 16.777.216), daí têm-se o nome RGB (Red, Green, Blue).

### Palavras-chave (keyword)

A primeira maneira de definir uma cor no CSS é através da declaração do nome da cor, como por exemplo:

```css
div {
 background-color: blue; /*define um plano de fundo azul*/
}
```
### Valores RGB Hexadecimais

A segunda forma apresentada é através de um código RGB iniciado com `#`, por exemplo: `#F0F0F0` ou `#f0f0f0`. A númeração dos valores RGB se dá através dos valores hexadecimais `0123456789abcdef` que são usados para fazer o código RGB e assim representar a cor nos canais vermelho, verde e azul.
```css
.box {
  background-color: #79028b;
}
```

Também é possível utilizar a função `rgb()` que recebe os valores do valor RGB:

```css
.box {
  background-color: rgb(79, 02, 8b);
}
```

#### Valores com transparência

Uma variação chamada *RGBa* permite usar transparência nas cores através do canal *alpha*

## Imagens

## Posição

## Strings e identificadores

## Funções

