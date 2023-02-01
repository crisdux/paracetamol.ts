<div align="center">
  <img height="60" src="https://skorpil.cz/sites/default/files/2020-03/1_mn6bOs7s6Qbao15PMNRyOA.png">
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