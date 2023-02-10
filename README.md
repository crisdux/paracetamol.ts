<div align="center">
  <img height="60" src="https://static-00.iconduck.com/assets.00/typescript-plain-icon-256x256-ypojgpyj.png">
  <h1>Paracetamol.ts</h1>
  <h2>Preguntas de TypeScript</h2>

---

<span>Me encanta JavaScript, pero en pleno 2023 me parece una necesidad aprender TypeScript tarde o temprano, este repo en un intento para lograr eso. Última vez actualizado: <a href=#20230201><b>01 Feb</b></a>

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

#### Respuesta: 
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

#### Respuesta: 
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

#### Respuesta: 
✅ B. `11`

Los `enum` por defecto empiezan en `0`, tal cual como si fueran un arreglo; lo interesante es que podemos modificar este comportamiento asignando un index arbitrario que reemplace al valor `0` inicial.

En este caso tenemos `Crema = 10`, y por ende el siguiente valor será `Agua = 11`.

</p>
</details>

---

<!-- ##### 4. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 
✅ 

</p>
</details>

--- -->

<!-- ##### 5. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 
✅ 

</p>
</details>

--- -->

<!-- ##### 6. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 
✅ 

</p>
</details>

--- -->

<!-- ##### 7. Explica este código Typescript

```ts

```

- A. ``
- B. ``
- C. ``
- D. ``

<details><summary><b>Respuesta</b></summary>
<p>

#### Respuesta: 
✅ 

</p>
</details>

--- -->

