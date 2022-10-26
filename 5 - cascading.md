# A Cascata (cascading)

A escolha do browser de qual regra aplicar, caso haja muitas regras para o mesmo elemento.

Seu estilo é lido de cima para baixo, ou seja, caso haja algum selector com informações conflitantes, o mais embaixo é o que será atribuído.

Se tiver dois links css ele vai ler o último

<link rel="stylesheet" href="style1.css">
<link rel="stylesheet" href="style2.css">

Ele lerá o style2.css

São levados em consideração 3 fatores:

1. A origem do estilo;
2. A especificidade;
3. A importância;

### Origem do estilo

A força vai ser na seguinte ordem

inline > tag style > tag link

in line = <h1 style="color: red">
tag style = <style> h1 { color: red;} </style>
tag link =  <link rel="stylesheet" href="./5.1 - cascata.css"> o arquivo css isolado (cascata.css)

### Especificidade

É um cálculo matemático, onde cada tipo de seletor e origem do estilo, possuem valores a serem considerados.

0. Universal selector, combinators e negation pseud-class (:not())
1. Element type selector e pseudo-elements (::before, ::after)

No exemplo abaixo ele vai priorizar o último h1 pois o seletor universal tem o valor de 0 e o h1 tem valor de 1.

h1 {
    color: red;
}

h1 {
    color: blue;
}

* {
    color: green;
}


10. Classes e atribute selectors ([type="radio])

No exemplo abaixo o referenciado pela class title tem poder em cima do h1, pois class tem peso 10 e element type selector peso 1.

<h1 class="title"> Título </h1>

.title {
    color: red;
}

h1 {
    color: blue;
}


100. ID selector

O ID é mais forte que a class e por isso tem prioridade.

<h1 class="title" id="mytitle"> Título </h1>

#mytitle {
    color: gray;
}

.title {
    color: red;
}

h1 {
    color: blue;
}

1000. Inline

Inline é mais forte do que todos.

<h1 class="title" id="mytitle" style="color: orange;" > Título </h1>

#### Juntando as forças

<h1 class="title" id="my-title" style="color: orange;" > Título </h1>

Aqui temos 111 de força, pois usei todos os seletores do elemento.

h1.title#my-title {
    color: blue;
}

##### Outros exemplos

<h1 class="title" id="my-title" style="color: orange;" >Título <strong>Alo</strong></h1>

Aplicar a cor orange para o strong, assim o Alo também ficará cinza

#my-title,
#my-title strong {
    color; gray;
}

###### Regra important

O important rouba a força de tudo, é a força absoluta ele sobscreve tudo

* cuidado, evite o uso
* não é considerado uma boa prática
* qubera o fluxo natural da cascata

No caso abaixo o h1 vai ser priorizado.

#my-title,
#my-title strong {
    color; gray;

.title {
    color: red;
}

h1 {
    color: blue !important;
}

* {
    color: green;
}