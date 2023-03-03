<div align="center">
  <img height="60" src="https://static-00.iconduck.com/assets.00/typescript-plain-icon-256x256-ypojgpyj.png">
  <h1>Paracetamol.ts</h1>
  <h2>Preguntas de TypeScript</h2>

---

<span>Me encanta JavaScript, pero en pleno 2023 me parece una necesidad aprender TypeScript tarde o temprano, este repo en un intento para lograr eso. Última vez actualizado: <a href=#20230303><b>03 Mar</b></a>

Los retos consisten en preguntas de selección múltiple en tres niveles: Básico, Intermedio y Avanzado. Las respuestas estarán collapsadas para no spoilearnos, el objetivo es aprender, así que trata de solucionar el reto sin ver la solución ni ejecutar el código.

Sigueme en mis redes para más! 😊 <br />
<a href="https://www.instagram.com/cris_cuetillo/">Instagram</a> || <a href="https://twitter.com/cris_cuetillo">Twitter</a> || <a href="https://www.linkedin.com/in/crisfer-dux/">LinkedIn</a> || <a href="https://dev.to/duxtech">Dev.to</a>
</div>

| Diviertete! |
|---|

---

##### 1. ¿Cuál de las siguientes variables estan bien declaradas?

```ts
let x: number;
let y = 0; 
let z: number = 123.456; 
let big: bigint = 100n; 
```

- A. `x` y `y`
- B. `Todas menos big`
- C. `x` y `z`
- D. `Todas`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ D. `Todas`

`number` y `bigint` son tipos de datos primitivos en TypeScript, veamos caso por caso:

* `x` esta bien puesto que las variables escritas con `let` pueden ser declaradas pero no inicializadas.
* `y` esta bien por que al inicializar la variable con un valor numerico entonces el motor de TypeScript **infiere** a tipo `number`.
* `z` esta bien por que es posible declarar la variable, asignarle el tipo de dato y luego darle un valor, perfectamente valido.
* `big` esta bien por que `bigint` es un tipo primitivo en TypeScript; al igual que con `z`, declaramos el tipo y hacemos la asignación de valor.

</p>
</details>

---

##### 2. Explica este código Typescript

```ts
enum Semana {
  Lunes,
  Martes,
  Miercoles,
  Jueves,
  Viernes,
  Sabado,
  Domingo,
}

let diaDivertido: Semana = Semana.Viernes;
console.log(diaDivertido); //???
```

- A. `Viernes`
- B. `4`
- C. `5`
- D. `Ninguna de las anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ B. `4`

Los `enum` son útiles para **agrupar conjuntos de constantes relacionadas** además de que se pueden usar como **tipo de dato**.
Siempre que un procedimiento acepte un conjunto limitado de variables, considere el uso de un `enum`.

En el ejemplo creamos un `enum` llamado `Semana` que contiene todos los días de la semana, la variable `diaDivertido` es de tipo `Semana`, lo que significa que solo puede tener uno de estos valores. 

Por defecto, un `enum` empieza por el valor `0`, (como si se tratara de un arreglo), entonces tendríamos: `0 -> Lunes`, `1 -> Martes`, `2 -> Miercoles`, `3 -> Jueves`, `4 -> Viernes`; por eso el resultado es `4`. 

</p>
</details>

---

##### 3. Explica este código Typescript

```ts
enum Helados{
  Crema = 10,
  Agua,
}

let miHeledo: Helados = Helados.Agua;
console.log(miHeledo)
```

- A. `10`
- B. `11`
- C. `ReferenceError`
- D. `RangeError`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ B. `11`

Los `enum` por defecto empiezan en `0`, tal cual como si fueran un arreglo; lo interesante es que podemos modificar este comportamiento asignando un index arbitrario que reemplace al valor `0` inicial.

En este caso tenemos `Crema = 10`, y por ende el siguiente valor será `Agua = 11`.

</p>
</details>

---

##### 4. ¿Cúal es la diferencia entre el bloque de código A y el bloque de código B?

```ts
//A
let y:any = "hola";
console.log(y.toUpperCase()) // HOLA

//B
let x:unknown = "hola";
console.log(x.toUpperCase()) // HOLA
```

- A. `No hay ninguna diferencia`
- B. `El tipo de dato unknown no existe en TypeScript`
- C. `El bloque de código B necesita una comprobación de tipo`
- D. `Ninguno de los anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ C. `El bloque de código B necesita una comprobación de tipo`

¿Cuál es la diferencia entre `any` y `unknown`?

`any` literalmente significa **cualquiera**, osea que una variable de tipo `any` puede almacenar cualquier valor, esto hace que TypeScript pierda un poco de su magia por eso se recomienda usarlo en migraciones de proyectos JavaScript a TypeScript o para la manipulación de librerías de terceros.

`unknown` literalmente significa **desconocido**, en escencia también puede recibir cualquier tipo de dato como `any`, **la diferencia es que a una variable de tipo `unknown` no es posible acceder a sus metodos y propiedades**, antes es necesario hacer una **comprobación de tipos**: 

```ts
let x:unknown = "hola";
if(typeof x === "string") console.log(x.toUpperCase()) // HOLA
```

Des esta manera, primero comprobamos que la variable es de tipo `string` antes de poder usar el método `toUpperCase()` que como sabemos es propio de las cadenas de texto.

`unknown` permite dar un poco más de seguridad que `any` con la comprobación de tipos pero sin perder la capacidad de asignarle cualquier tipo de variable.

</p>
</details>

---

##### 5. Explica este código Typescript

```ts
function add(x: number | string, y: number | string) {
  if (typeof x === 'number' && typeof y === 'number') return x + y;
  if (typeof x === 'string' && typeof y === 'string') return x.concat(y);
  throw new Error('Parameters must be numbers or strings');
}
console.log(add('one', 'two'));  //🤔
console.log(add(1, 2));          //🤔
console.log(add('one', 2));      //🤔
```

- A. `TypeError`, `"12"`, `undefined`
- B. `"onetwo"`, `3`, `Uncaught Error: Parameters must be numbers or strings`
- C. `"onetwo"`, `"12"`, `null`
- D. `Ninguno de los anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ B. `onetwo`, `3`, `Uncaught Error: Parameters must be numbers or strings`

El signo `|` en TypeScript significa **unión**. 

Esta operación es útil para hacer **multitype**, osea, que una misma variable acepte un conjunto de tipos.

En el ejemplo: `x` y `y` son parámetros que pueden aceptar dos tipos de dato: `number` o `string`. la función varifica, si son `number` los suma, si son `string` los concatena.

El último caso lanza un error por que no tenemos una validación en el cuerpo de la función. 

</p>
</details>

---

##### 6. Explica este código Typescript

```ts
type Fruta = "pera" | "limon" | "naranja";
let fruta: Fruta;
fruta = "zandia"; // A
fruta = "limon"; // B
```

- A. `Ambos son validos`
- B. `A invalido, B valido`
- C. `B invalido, A valido`
- D. `Ninguna de las anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ B. `A invalido, B valido`

Si la variable `fruta` fuera de tipo `string` podría recibir cualquier cadena de texto valida, pero que tal si necesitamos restringir la variable para que si o si solo pueda recibir un conjunto de cadenas especificas, en el ejemplo: `pera`, `limon` o `naranja`.

Con la palabra reservada `type` creamos lo que se denomina un **litteral type** `Fruta` que solo puede contener uno de estos tres valores, si intentamos asignarle cualquier otra cosa, como por ejemplo `zandia` tendremos una advertencia para no caer en esta mala practica.

</p>
</details>

---

##### 7. ¿Cuál de las siguientes sintaxis de arreglo es la correcta?

```ts
const numeros: number[] = [1,2,3];
const nombres: Array<string> = ["Carlos", "Juan"]
```

- A. `Solo numeros`
- B. `Solo nombres`
- C. `Ninguna es correcta`
- D. `Ambas son correctas`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ D. `Ambas son correctas`

En TypeScript tenemos 2 sintaxis para declarar arreglos:
* Usando `[]` y el tipo de dato del arreglo per se.
* Usando notación de genericos, la palabra reservada `Array` y entre `<>` el tipo de dato del arreglo.

En la practica no existe ventaja de una sobre la otra, por ello por buenas practicas se recomienda elegir una y usarla de manera consistente a lo largo de todo un proyecto. 

</p>
</details>

---

##### 8. Explica este código Typescript

```ts
function welcomePeople(x: string[] | string) {
  if (Array.isArray(x)) {
    const formatter = new Intl.ListFormat('es', { style: 'long', type: 'conjunction' });
    console.log(`Hello ${formatter.format(x)}`);
  } else {
    console.log("Welcome lone traveler " + x);
  }
}

welcomePeople(["Alice", "Philip", "Anet"])
welcomePeople("Alice")
```

- A. `"Hello Alice, Philip y Anet"`, `"Welcome lone traveler Alice"`
- B. `"Hello undefined, undefined y undefined"`, `"Welcome lone traveler undefined"`
- C. `"Hello null, null y null"`, `"Welcome lone traveler null"`
- D. `Ninguna de las anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ A. `"Hello Alice, Philip y Anet"`, `"Welcome lone traveler Alice"`

La función `welcomePeople` recibe un parámetro `x` que puede ser un arreglo de objetos o una cadena, por ende nuestro código tendra comportamientos diferentes dependiendo del argumento que le pasemos.

Cuando le pasamos un arreglo, usamos el objeto `Intl` para formatear el arreglo en forma de lista imprimiendo `"Hello Alice, Philip y Anet"`.

Y si pasamos una cadena solo concatenamos su valor e imprimimos `"Welcome lone traveler Alice"`.

---

Mas información sobre el objeto `Intl` [aquí](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Intl)


</p>
</details>

---

##### 9. Explica este código Typescript

```ts
let addThreeNumbers = (x: number, y: number, z: number): number => x + y + z;
console.log(addThreeNumbers(10, 20))
console.log(addThreeNumbers(10, 20, 30, 40))
```

- A. `30`, `100`
- B. `30`, `60`
- C. `NaN`, `60`
- D. `undefined`, `60`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ C. `NaN`, `60`

Todos los parámetros de la función `addThreeNumbers` son obligatorios, lo que significa que para recibir la salida correcta debemos pasarle el número exacto de parámetros.

Para el primer caso:
`x = 10`, `y = 20`, `z = undefined`, entonces `10 + 20 + undefined` no es una operación valida, por ello el resultado es `NaN`. Además TypeScript nos ayuda un poco mas dandonos una advertencia: `Expected 3 arguments, but got 2.`

Para el segundo caso: 
`x = 10`, `y = 20`, `z = 30`, pero el 40 no tiene un parámetro asignado dentro de la función, así que al igual como en JavaScript este valor será completamente ignorado regresando `60` pero con una advertencia en nuestro editor: `Expected 3 arguments, but got 4.`

</p>
</details>

---

##### 10. Explica este código Typescript

```ts
const fn = (name?:string, edad:number) => {
  return `${name} - ${edad}`
}

console.log(fn("Carlos", 25))
console.log(fn(25))
```

A. `Carlos - 25`, `undefined - 25`
B. `Carlos - 25`, `25 - undefined`
C. `Carlos - 25`, `TypeError`
D. `Carlos - 25`, `undefined - undefined`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ B. `Carlos - 25`, `25 - undefined`

En TypeScript existen los parámetros opcionales (que no es lo mismo que los parámetros por defecto), consiste obviamente en dar la posibilidad al programa de funcionar normalmente omitiendo el parámetro opcional.

En TypeScript todos los parámetros de una función son obligatorios a no ser que se le indique lo contrario. La única condición para usarlos es que los parámetros opcionales deben ser escritos al final de la función siempre: 

```ts
const fn = (edad: number, name?: string) => {
  return `${name} - ${edad}`
}

console.log(fn(25, "Carlos")) // Carlos - 25
console.log(fn(25)) // undefined - 25
```

Pese a que la salida es similar al resultado de este reto, esta sería la forma correcta de escribir la función para que no salten advertencias en nuestro editor de código.

Uno de los problemas de usar parámetros opcionales es que estos puden venir como `undefined` entonces tenemos que validar estos casos, pero esto lo dejamos para otro reto...

</p>
</details>

---


##### 11. Explica este código Typescript

```ts
const temperatura:[number,string] = [20, "C"]
temperatura.push("Hola mundo");
console.log(temperatura); // 🤔🤔
```

- A. `[ 20, "C", "Hola mundo" ]`
- B. `[ 20, "C"]`
- C. `TypeError`
- D. `ReferenceError`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ A. `[ 20, "C", "Hola mundo" ]`

Las tuplas en TypeScript son como una especie de arreglo con restrucciones de posición, cuando creamos una tupla como esta `const temperatura:[number,string] = [20, "C"]` queremos decir que explicitamente necesitamos un arreglo de dos posiciones: la primera recibirá un valor numérico y la segunda una cadena.

Al usar el método `push` intentamos agregar un tercer elemento a una tupla que solo admite dos. Este es un caso particular que solo pasa con tuplas cuando queremos agregarle un nuevo elemento, un comportamiento similar ocurre con el método `concat` o usando el spread operator.

</p>
</details>

---

##### 12. Explica este código Typescript

```ts
function stringify123(callback: (num: number) => string):string {
  return callback(123);
}

console.log(stringify123(String));
```

- A. `"123"`
- B. `123`
- C. `ReferenceError`
- D. `Ninguna de las anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ B. `123`

Las funciones en TypeScript pueden ser escritas de manera explicita con su valor de retorno.
En el ejemplo:
* El callback regresa `string`:

```ts
callback: (num: number) => string
```

* Y la función principal `stringify123` también regresa un `string`:

```ts
function stringify123(callback: (num: number) => string):string {}
```

Al pasarle como callback el contructor `String` convertiremos cualquier número a cadena de texto, por ello el resultado es `123` como número.

En muchas ocaciones no es necesario escribir de manera explicita el tipo de retorno de una función, TypeScript tiene la capacidad de deducirlo según el código que escribamos; en otras ocaciones por legibilidad es mejor si escribirlo, así sabemos de una pasada el valor de retorno de una fucnión sin leer su cuerpo. Ya depende de cada dev.

</p>
</details>

---

##### 13. Explica este código Typescript

```ts
function f1(): void {
  return undefined;
}

function f2(): void { }

console.log(f1()) // 🤔
console.log(f2()) // 🤔
```

- A. `undefined`, `void`
- B. `null`, `null`
- C. `undefined`, `undefined`
- D. `undefined`, `NaN`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ C. `undefined`, `undefined`

`void` es un tipo de retorno que se suele usar a menudo con algunas funciones. En praxis significa que una función regresa `undefined`. 

* `f1` literalmente regresa `undefined`.
* `f2` al no tener cuerpo, también regrasa `undefined`.
</p>
</details>

---

##### 14. Explica este código Typescript

```ts
const f1 = (a = 0, b = 0):[number, number] => {
  return [a, b]
}

console.log(f1()) // 🤔
console.log(f1(1,2)) // 🤔
```

- A. `[number, number]`, `[1, 2]`
- B. `ReferenceError`, `[1, 2]`
- C. `undefined`, `[1, 2]`
- D. `[0, 0]`, `[1, 2]`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 
✅ D. `[0, 0]`, `[1, 2]`

TypeScript al igual que JavaScript admite valores por defecto para los parámetros.
En este caso la función `f1` recibe dos parámetros: `a` y `b` que tienen valores por defecto de `0`; la función regresa una tupla de dos posiciones ambas de tipo `number`; finalmente solo regresamos la tupla.

Para el primer caso:
Llamamos a la función sin ningún parámetro, por ello regresamos los valores por defecto : [0, 0].

Para el segundo caso:
Llamos a la función con los parámetros `f1(1,2)` entonces regresamos dichos valores en el formato de la tupla, omitiendo asi los valores por defecto: `[1, 2]`

</p>
</details>

---

##### 15. Explica este código Typescript

```ts
const obj = {
  id: 1,
  title: "test",
}
obj.description = "hello";
console.log(obj); // 🤔
```

- A. `{ description: "hello", id:1, title: "test" }`
- B. `TypeError`
- C. `{ id:1, title: "test" }`
- D. `ReferenceError`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 

✅ A. `{ description: "hello", id:1, title: "test" }`

La respuesta de este reto es un poco trampa y vamos a explicar por que.

El código del reto tanto en JavaScript como en TypeScript se ejecuta sin ningún error, peeero en TypeScript nos marca una advertencia: `Property 'description' does not exist on type '{ id: number; title: string; }'`; ¿pero por que pasa esto?

En TypeScript los objetos literales son como interfaces anónimas, lo que quiere decir que deben cumplir el contrato que las contiene.

En nuestro ejemplo, el objeto `obj` es del tipo `{ id: number; title: string; }` lo que significa que debe tener un campo `id` y un campo `title` si o si, no mas campos ni menos.

Al intentar agregar el campo `description` el contrato se rompe y esto causa la advertencia que nos arroja TypeScript.

</p>
</details>

---

##### 16. Explica este código Typescript

```ts
enum Values{
  "No",
  "Yes",
  "Maybe"
};

function print(value: Values){
  switch(value){
    case Values.No:
      return "Non";
      break;
    case Values.Yes:
      return "Oui";
      break;
    default:
      return "Maybe"
  }
}
console.log(print(Values.Yes)) // 🤔
```

- A. `Oui`
- B. `Non`
- C. `Maybe`
- D. `Ninguno de los anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 

✅ A. `Oui`

Los `enum` son una cualidad propia de TypeScript que no existe de manera nativa en JavaScript.

En terminos sencillos, los `enum` son un conjunto de variables que comparten algo en común; en nuestro ejemplo la función `print` recibe un `value` de tipo `Values`, esto significa que value solo podría ser "No", "Yes" o "Maybe", pasarle otro valor producirá un error.

Pasamos como argumento `Values.Yes`, por ello la salida es `Oui`.

</p>
</details>

---

##### 17. Explica este código Typescript

```ts
enum Values{
  "No" = false,
  "Yes",
  "Maybe",
};

console.log(Values.No);
```

- A. `0`
- B. `No`
- C. `Type 'false' is not assignable to type 'Values'`
- D. `Ninguno de los anteriores`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 

✅ C. `Type 'false' is not assignable to type 'Values'`

Los `enum` en TypeScript solo pueden ser inicializados con valores  de tipo `string` o `number`. 

Si intentamos usar cualquier otro valor como inicializador tendremos un error, no podemos usar arreglos, objetos, boleanos, ni siquiera símbolos.

A tomar en cuenta!

</p>
</details>

---

##### 18. Explica este código Typescript

¿Cúal de las siguientes sintaxis de enum es una buena practica?

```ts
//A
enum diasDeLaSemana{
 ...
};

//B
enum diasdelasemana{
  ...
}

//C
enum dias_de_la_semana{
  ...
}

//D
enum DiasDeLaSemana{
  ...
}
```

- A. `A`
- B. `B`
- C. `C`
- D. `D`

<details><summary><b>Respuesta</b></summary>
<p>

#### **Respuesta**: 

✅ D. `D`

Si bien todas son sintaxis válidas y funcionarían sin ningún problema, usar PascalCase es lo que se aconseja para tener un código con buenas practicas.

</p>
</details>

---

<!-- ##### 19. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 


</p>
</details>

--- -->

<!-- ##### 20. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 


</p>
</details>

--- -->

<!-- ##### 21. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 


</p>
</details>

--- -->

<!-- ##### 22. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 


</p>
</details>

--- -->

<!-- ##### 23. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 


</p>
</details>

--- -->

<!-- ##### 24. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 


</p>
</details>

--- -->