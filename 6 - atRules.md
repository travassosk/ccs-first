# At- Rules

* São regras relacionadas ao comportamento do CSS 
* Começa com um sinal de @ seguido do identificador e do valor.

## Exemplos comuns

@import             /* serve para incluir um CSS externo. */
@media              /* são regras condicionais para vários dispositivos. */
@font-face          /* é para colocar fontes externas. */
@keyframes          /* serve para as animations do CSS. */

### CSS

@import url("http://local.com/style.css);

@media (min-width: 500px) {
    /* rules here */
}

@font-face {
    /* rules here */
}

@keyframes nameofanimation {
    /* rules here */
}