# Adventjs-retos

AdventJavaScript Retos y regalos de programación navideños ¡Cada día, un nuevo reto de programación!

## Reto #1: 🎁 ¡Primer regalo repetido!

En la fábrica de juguetes del Polo Norte, cada juguete tiene un número de identificación único.

Sin embargo, debido a un error en la máquina de juguetes, algunos números se han asignado a más de un juguete.

¡Encuentra el primer número de identificación que se ha repetido, **donde la segunda ocurrencia tenga el índice más pequeño**!

En otras palabras, si hay más de un número repetido, debes devolver el número cuya segunda ocurrencia aparezca primero en la lista. Si no hay números repetidos, devuelve -1.

### Ejemplos

```javascript
const giftIds = [2, 1, 3, 5, 3, 2];
const firstRepeatedId = findFirstRepeated(giftIds);
console.log(firstRepeatedId); // 3
// Aunque el 2 y el 3 se repiten
// el 3 aparece primero por segunda vez

const giftIds2 = [1, 2, 3, 4];
const firstRepeatedId2 = findFirstRepeated(giftIds2);
console.log(firstRepeatedId2); // -1
// Es -1 ya que no se repite ningún número

const giftIds3 = [5, 1, 5, 1];
const firstRepeatedId3 = findFirstRepeated(giftIds3);
console.log(firstRepeatedId3); // 5
```

### Solución

```javascript
function findFirstRepeated(gifts) {
    let result = gifts.filter((item, index) => {
        return gifts.indexOf(item) != index;
    });
    return result[0] || -1;
}
```

<!-- //////////////////////////////-2-///////////////////////////////////// -->

## Reto #2: 🏭 Ponemos en marcha la fábrica

En el taller de Santa, los elfos tienen una lista de regalos que desean fabricar y un conjunto limitado de materiales.

Los regalos son cadenas de texto y los materiales son caracteres. Tu tarea es escribir una función que, dada una lista de regalos y los materiales disponibles, devuelva una lista de los regalos que se pueden fabricar.

Un regalo se puede fabricar si contamos con todos los materiales necesarios para fabricarlo.

### Ejemplos

```javascript
const gifts = ["tren", "oso", "pelota"];
const materials = "tronesa";

manufacture(gifts, materials); // ["tren", "oso"]
// 'tren' SÍ porque sus letras están en 'tronesa'
// 'oso' SÍ porque sus letras están en 'tronesa'
// 'pelota' NO porque sus letras NO están en 'tronesa'

const gifts = ["juego", "puzzle"];
const materials = "jlepuz";

manufacture(gifts, materials); // ["puzzle"]

const gifts = ["libro", "ps5"];
const materials = "psli";

manufacture(gifts, materials); // []
```

### Solución

```javascript
function manufacture(gifts, materials) {
    return gifts.filter((word, index) => {
        let arrayLetters = word.split("");
        let LettersIsNotThere = arrayLetters.find((letter) => {
            return !materials.includes(letter);
        });
        return !LettersIsNotThere;
    });
}
```

<!-- //////////////////////////////-3-///////////////////////////////////// -->

## Reto #3: 😏 El elfo travieso

En el taller de Santa, un elfo travieso ha estado jugando en la cadena de fabricación de regalos, añadiendo o eliminando un paso no planificado.

Tienes la secuencia original de pasos en la fabricación original y la secuencia modificada modified que puede incluir un paso extra o faltar un paso.

Tu tarea es escribir una función que identifique y devuelva el primer paso extra que se ha añadido o eliminado en la cadena de fabricación. Si no hay ninguna diferencia entre las secuencias, devuelve una cadena vacía.

### Ejemplos

```javascript
const original = "abcd";
const modified = "abcde";
findNaughtyStep(original, modified); // 'e'

const original = "stepfor";
const modified = "stepor";
findNaughtyStep(original, modified); // 'f'

const original = "abcde";
const modified = "abcde";
findNaughtyStep(original, modified); // ''
```

A tener en cuenta:

-   Siempre habrá un paso de diferencia o ninguno.
-   La modificación puede ocurrir en cualquier lugar de la cadena.
-   La secuencia original puede estar vacía

### Solución

```javascript
function findNaughtyStep(original, modified) {
    if (original === modified) return "";

    let shortWord = "";
    let longWord = "";
    if (original.toString().length > modified.toString().length) {
        longWord = original;
        shortWord = modified;
    } else {
        shortWord = original;
        longWord = modified;
    }

    for (let index = 0; index < longWord.length; index++) {
        if (longWord[index] != shortWord[index]) {
            return longWord[index];
        }
    }
}
```
