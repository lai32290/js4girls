## CSS

## 基本的CSS選擇器

選擇器是在妳讀CSS的時候最先需要學習的其中一項。選擇器是CSS基礎的一部分是無法質疑的，但是少數的程式員懂得使用它所有的淺力。即使你有辦運用例如ID或者類別的選擇器來實現許多的樣式，選擇器還可做更多的事情... CSS選擇器可以讓你選擇並且處理HTML的元素。CSS選擇器是用來：透過ID、類別、類型、屬性或者更多方式來"尋找"（或選擇）HTML元素。

我們來說說基本的。一個CSS選擇器是以一種格式來「配對」所有在檔案樹中所有適合那個格式的元素。當所有在格式中所定義的條件都滿足時，選擇器就會將文檔中的元素（們）跟選擇器中的規則進行配對。CSS的規則是簡單如下：

```css
p { color:#f00; }
```

選擇器是在CSS規則中的"{"符號前面的。這裡的選擇器是P，將會語文檔中任何段落中的文字配對，將它們變成紅色，就這麼簡單。

## 選擇器的整體觀

我將會在這個文章中的第一段裡一個一個詳細的解釋這些選擇器，你只需要繼續讀下去。在上面所提到的一些術語以及這個文章裡即將會提到的，有必要在多作解釋：

### 後代
是在文檔樹裡，為子元素、孫元素或者離某個元素更遠的子孫元素。

### Ancestor
是在文檔樹裡面，為父親、爺爺或者離某個元素更遙遠的上代元素。

### 兒子
某個元素直接的後輩元素，在兩個元素中不存在任何其他元素。

### 父親
某個元素直接的前輩元素，在兩個元素中不存在任何其他元素。

### Sibling (兄弟)
兄弟元素，是某個父元素的兒子。

## 普通選擇器與配對選擇器

有兩種基本的選擇器：普通型與配對型。

一個普通的選擇器是任何一個沒有包含屬性選擇器的，例如ID選擇器、類別選擇器或者偽元素選擇器。以下是一個普通選擇器的例子：

```css
p.info { background:#ff0; }
```

一個combined selectors（有時候也稱作contextual selector）是包含兩個或者更多的simple selectors，由一個配對的元素來分開。以下來舉一個combined selector的例子。

```css
div p { font-weight:bold; }
```

以上的規則會施加在所有div元素裡面的p元素上。

一個pseudo-element被當作一個選擇器的附加項目。在combined selectors中，pseudo-element只可以被附加在最後一個simple selector上。

在後面一點將會更詳細的深入解釋關於combined selectors、元素的配對以及pseudo-elements。

## Universal Selectors

Universal selector 是由一個星號來代表，「\*」，而它可以與文檔中的所有元素進行配對。這是一個很少在樣式表中看到的用法，但是universal selector很常被跟與ID選擇器或者class選擇器一起使用。Se o seletor universal não for o único componente de um seletor simples, o “\*” não deve ser usado :

  - .myclass 也等於 \*.myclass
  - \#myid 也等於 \*#myid

Universal selecotr一個很常用的方法是用來將所有元素的margins與paddings歸零：

```css
* { margin:0; padding:0; }
```

Este procedimento é também conhecido como `Global White Space Reset`.

## Seletores Tipo

Um seletor tipo, casa com qualquer instância de um determinado tipo de elemento. A regra a seguir casa com qualquer elemento (do tipo) parágrafo no documento e configura seu tamanho de fonte para 2em:

```css
p { font-size:2em; }
```

### Seletor – classe

O seletor de classe é representado por um ponto, “.”, e tem como alvo elementos com um determinado valor para seu atributo class. A regra a seguir aplica-se a todo elemento parágrafo cuja classe tenha o nome “info”:

```css
p.info { background:#ff0; }
```

Você pode atribuir vários nomes para a classe de um elemento – o atributo class pode conter uma lista de vários nomes separados por espaço em branco. Assim, os seletores de classe podem ser usados para casar com elementos cuja classe contenha vários nomes. A regra a seguir casa com elementos p que tenham os nomes “info” e “error” declarados em seu atributo class:

```css
p.info.error { color:#900; font-weight:bold; }
```

O tipo de elemento não precisa necessariamente ser declarado. Este procedimento, não declarar o tipo de elemento, equivale a usar o seletor universal como tipo de elemento. A regra a seguir casa com qualquer elemento da classe “info”, independentemente do tipo de elemento:

```css
.info { background:#ff0; }
```


### Seletor – ID

O seletor ID é representado por um sinal de "tralha" (ou "jogo da velha"), “#”, e tem como alvo elementos com um deteminado valor de atributo ID. A regra a seguir aplica-se a todos os elementos cujo nome de ID seja “info”, independentemente do tipo de elemento:

```css
#info { background:#ff0; }
```

Se você especificar um determinado tipo de elemento a regra será aplicada somente àquele tipo de elemento que tenha o nome da ID especificado:

```css
p#info { background:#ff0; }
```

É importante lembrar que seletores ID tem uma especificidade maior que seletores de classe e que um valor de ID deve ser único em um mesmo documento. Assim um determinado seletor ID será aplicável a um único elemento no documento.


### Elementos de combinação

Elementos de combinação de seletores são usados para separar dois ou mais seletores simples que compõem um seletor combinado. Os elementos de combinação disponíveis são: espaço em branco (qualquer quantidade de espaço, tabulação ou caracteres de espaçamento), o sinal de maior “>” e o sinal de adição “+” . A função de cada um destes elementos de combinação dos seletores será descrita adiante.

### Seletores descendentes

Um seletor descendente é uma combinação de dois ou mais seletores simples separados por um espaço em branco. Casa com elementos que sejam descendentes do primeiro elemento simples declarado no seletor. Por exemplo, na regra a seguir o seletor casa com todos os elementos pque sejam descendentes do elemento div:

```css
div p { color:#f00; }
```

Cada um dos seletores que compõem um seletor descendente pode ser um seletor simples de qualquer natureza. Na regra a seguir o seletor casa com todo o elemento p da classe info contido em um elemento li que esteja contido em um elemento div cuja id seja myid.

```css
div#myid li p.info { color:#f00; }
```

Seletores descendentes permitem que você case um elemento sem necessidade de atribuir-lhe uma classe ou uma id, o que resultará em uma marcação mais limpa. Vamos supor uma lista de navegação conforme a marcação abaixo:

```html
<ul id="nav">
  <li><a href="#">Link 1</a></li>
</ul>
<ul>
  <li><a href="#">Link 2</a></li>
  <li><a href="#">Link 3</a></li>
</ul>
```

Para atingir os itens de lista e links contidos na lista de navegação você poderia usar as seguintes regras CSS:

```css
#nav li { display:inline; } 
#nav a { font-weight:bold; }
```

Estas regras não serão aplicadas a nenhum outro item de lista ou links dentro do documento. Agora compare com a opção de nomear uma classe para cada item da lista e para os links e você perceberá quão mais limpa poderá tornar-se sua marcação com o uso de seletores descendente

### Seletores Filho

Um seletor filho tem como alvo um filho imediato de um elemento. O seletor filho consiste de um ou mais seletores simples separados por um sinal de maior “>”. O elemento pai fica à esquerda do sinal “>”, e é permitido deixar espaço em branco entre o elemento de combinação e os seletores.
A regra a seguir aplica-se a todos os elementos strong que sejam filhos de um elemento div:

```css
div > strong { color:#f00; }
```

Somente elementos strong que sejam descendentes diretos do elemento div serão afetados por esta regra. Se houver qualquer outro elemento entre o elemento div e o elemento strong na árvore do documento, o seletor não se aplicará. No exemplo a seguir, somente “Texto um” será afetado pela regra:

```html
<div>
  <strong>Texto um</strong>
  <p><strong>Texto dois</strong></p>
</div>
```

### Seletores Irmãos adjacentes (sibling selectors)

Um seletor filho tem como alvo um filho imediato de um elemento. O seletor filho consiste de um ou mais seletores simples separados por um sinal de maior “+”. O elemento pai fica à esquerda do sinal “+”, e é permitido deixar espaço em branco entre o elemento de combinação e os seletores.
A regra a seguir aplica-se a todos os elementos strong que sejam filhos de um elemento div:

```css
p + strong { color:#f00; }
```

Somente elementos strong que sejam irmãos diretos do elemento p serão afetados por esta regra. Se houver qualquer outro elemento entre o elemento + e o elemento strong na árvore do documento, o seletor não se aplicará. No exemplo a seguir, somente “Texto dois” será afetado pela regra:

```html
<div>
  <p><strong>Texto um</strong></p>
  <strong>Texto dois</strong>
</div>
```

### Agrupando seletores

Eu decidi abordar o agrupamento a esta altura do artigo, porque um erro comum que eu vejo as pessoas cometer quando estão aprendendo CSS diz respeito ao agrupamento de seletores.

Para aplicar uma mesma regra a diferentes elementos alvo casados por diferentes seletores você pode agrupar os seletores em uma lista e separando-os por uma vírgula no lugar de escrever repetidamente a mesma regra para cada um dos seletores. O erro que muitos cometem é o de não listar de modo completo todos os seletores. Considere a seguinte marcação:

```html
<div id="news"> 
  <h3>News</h3>
  <ul>
    <li>Item 1</li>
    <li>Item 2</li>
  </ul>
</div>
```

Agora considere que você quer aplicar a mesma margem para cabeçalhos do nível 3 e para listas não ordenadas que estejam dentro do elemento div cuja id é “news”. Aqui maneira errada:

```css
div#news h3, ul { margin:0 2em; }
```

Esta regra será aplicada a ambos os elementos h3 e ul na div#news. O problema é que atingirá todos os elementos ul contidos no documento, e não apenas aqueles na div#news.

Agora a maneira correta de grupar os seletores para este caso:

```css
div#news h3,div#news ul { margin:0 2em; }
```

Assim, quando grupar seletores lembre-se de escrever por completo cada um deles.

### Seletores de Atributo

Seletores de atributo atingem elementos baseados no valor de atributo declarado no seletor. Existem quatro maneiras de declarar um seletor de atributo:

  - [att] Casa com qualquer elemento com o atributo att independente do seu valor.
  - [att=val] - Casa com qualquer elemento com o atributo att cujo valor seja “val”.
  - [att~=val] - Casa com qualquer elemento que tenha um atributo att de valor igual a um valor qualquer separado por um espaço de um valor igual “val”. Neste caso “val” não pode conter espaços.
  - [att|=val] - Casa com qualquer elemento que tenha um atributo att de valor igual a um valor qualquer separado por um hífen de um valor começando com “val”. O principal uso deste seletor é o de casar elementos com um valor de idioma especificado no atributo lang (xml:lang em XHTML), por exemplo;“en”, “en-us”, “en-gb”, etc.

#### Exemplos
O seletor na regra a seguir casa com todos os elementos p que tenham o atributo title, independentemente do valor do atributo:

```css
p[title] { color:#f00; }
```

No próximo exemplo o seletor casa com todos os elementos div que tem um valor para o atributo class igual a error:

```css
div[class=error] { color:#f00; }
```

Para atingir todos os elementos td cujo atributo headers contenha o valor “col1”, podemos usar o seguinte seletor:

```css
td[headers~=col1] { color:#f00; }
```

E finalmente, o seletor seguinte atinge todo elemento p cujo atributo lang comece com en:

```css
p[lang|=en] { color:#f00; }
```

Múltiplos seletores de atributos podem ser usados em um mesmo seletor. Isto possibilita atingir vários diferentes atributos para o mesmo elemento. a regra a seguir aplica-se a todos os elementos blockquote que tenham o atributo class de valor igual a “quote”, e mais o atributo cite (independentemente do seu valor):

```css
blockquote[class=quote][cite] { color:#f00; }
```

### Seletores Pseudo-elementos

Como o contéudo iria se extender demais se abordassemos mais esse tópico, por isso quero deixar avisado aqui que a continuação dessa parte do CSS será mehor explicada em materiais futuros que você poderá estudar por aqui.




