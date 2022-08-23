---
# try also 'default' to start simple
theme: default
# random image from a curated Unsplash collection by Anthony
# like them? see https://unsplash.com/photos/6terqWC_KCk
background: https://images.unsplash.com/photo-1611702700098-dec597b27d9d?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1920&q=80
# apply any windi css classes to the current slide
class: 'text-center'
# https://sli.dev/custom/highlighters.html
highlighter: shiki
# show line numbers in code blocks
lineNumbers: true
# some information about the slides, markdown enabled
drawings:
  persist: false
css: windicss
---

# Tablas de hash

La posibilidad de llegar al O(1) 🚀🚀🚀


<div class="abs-br m-6 flex gap-2">
  <a href="https://www.geeksforgeeks.org/hashing-data-structure/" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <simple-icons-geeksforgeeks/>
  </a>
  <a href="https://www.cs.usfca.edu/~galles/visualization/OpenHash.html" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <file-icons-sandbox/>1
  </a>
  <a href="https://www.cs.usfca.edu/~galles/visualization/ClosedHash.html" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <file-icons-sandbox/>2
  </a>
</div>

---

# Qué es una tablas de hash?

Es una estructura de datos que permite almacenar un conjunto de datos en **O(1)cp**

- `Búsqueda`
- `Insertar`
- `Eliminar`

<br>
<br>

> 📗 Nota: Los elementos de la tabla de hash deben ser **únicos**.

<br/>

> 📘 Nota 2: Los elementos no necesitan definir un orden para ser almacenados. A diferencia de los ABB | AVL.


---
layout: image-right
image: /definition.jpg
---

# Vocabulario

<br/>

## La tabla en sí
Es un array que contendra los elementos.

## Buckets 🪣
Cada celda del array se lo conoce como "buckets".

## Función de hash
Toda tabla de hash necesita una función de hash para realizar sus operciones básicas.

---

# Características de una función de hash

- Toma los elementos de la tabla los convierte a un **número entero**.
- Deben ser **deterministas**.

<br>

```cpp
// Una funcion de hash que toma un string y devuelve un entero.
// Para ello suma todos los caracteres del string.
int hash(string key) {
  int h = 0;
  for (int i = 0; i < key.length(); i++)
    h = h + key[i];
  return h;
}
```
<br>

---

# Características de una **buena** función de hash ✅

<br>

<div class="grid grid-cols-2 gap-4">
  <div>
    <ul>
      <li>Evitar colisiones 💢</li>
      <li>Ser O(1)pc 🚀</li>
      <li>Efecto avalancha 🏔️ 
        <a href="https://en.wikipedia.org/wiki/Avalanche_effect" target="_blank">link</a>
      </li>
    </ul>
  </div>
  <div >
    <img class="max-w-xs" src="/6qpf3b.jpg">
  </div>
</div>


---
layout: two-cols
---

<Hashing m="t-4" />

[Ejemplos de distribución](https://docs.google.com/spreadsheets/d/1Rkgw8dTzOiEo9i2jh9iKmjVFG_UXsTeaLfKUk8GIkP4/edit#gid=0)

::right::

```cpp
int hash1(string key) {
  int h = 0;
  for (int i = 0; i < key.length(); i++)
    h = h + key[i];
  return h;
}
```
<br/>

```cpp
int hash2(string key) {
  int h = 0;
  for (int i = 0; i < key.length(); i++)
    h = h + key[i] * (i + 1);
  return h;
}
```
<br/>

```cpp
// Ref: https://cseweb.ucsd.edu/~kube/cls/100/Lectures/lec16/lec16-15.html
int hash3(string key) {
  int h = 0;
  for (int i = 0; i < key.length(); i++)
    h = 31 * h + int(clave[i]);
  return h;
}
```

---

# Colisiones 💢
Cuando dos entradas diferentes les corresponde el mismo bucket. 

La cantidad de colisiones depende de dos factores:
- **Que tan buena es la función de hash**

A mayor distribución de la función de hash, menor cantidad de colisiones.

- **El factor de carga (λ)**

Una tabla muy "cargada" tendrá más colisiones.



---

# Colisiones = 💩
Las colisiones es algo que debemos evitar a toda costa.

La razon principal es porque las operaciones de la tabla de hash (`insertar` | `buscar` | `eliminar`) dejan de ser **O(1)cp**.
Lo cuál deja de ser una estructura de datos eficiente y pierde todo atractivo de uso. 

<v-click>
  <div class="grid place-items-center">
    <img class="center max-w-xs" src="/colisiones.png">
    Ejemplo: <a href="https://es.wikipedia.org/wiki/Paradoja_del_cumplea%C3%B1os" target="_blank" alt="GitHub">
      la paradoja del cumpleaños </a>
  </div>
</v-click>

---
layout: image
image: https://images.unsplash.com/photo-1463680942456-e4230dbeaec7?ixlib=rb-1.2.1&ixid=MnwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHx8&auto=format&fit=crop&w=1470&q=80
class: "text-center"
---

# Manejo de colisiones
Hash abierto | Hash cerrado
---
layout: two-cols
---

# Hash abierto
aka Separate chaining

Los elementos se encuentran en una estructura ilimitada (generalmente listas enlazadas).

<div class="img-container">
  <img class="max-w-xs" src="/hash-abierto.png"/>
</div>

<a href="https://www.cs.usfca.edu/~galles/visualization/OpenHash.html" target="_blank"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <file-icons-sandbox/> visualizador
</a>

::right::

# Hash cerrado
aka Open Addressing

Los elementos se encuentran dentro de los buckets. 

<div class="img-container">
  <img class="max-w-xs" src="/hash-cerrado.png"/>
</div>

<a href="https://www.cs.usfca.edu/~galles/visualization/ClosedHash.html" target="_blank"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <file-icons-sandbox/> visualizador
</a>

<style>
.img-container {
  background-color: #f5f5f5;
  width: fit-content;
}
</style>

---

# Tipos de hash cerrado
La búsqueda del bucket deseado se hace a prueba y error.

Existen tres tipos de hash cerrado:

- [Lineal](https://en.wikipedia.org/wiki/Linear_probing): prueba de forma lineal `index(key,i) = h(key) + i`
- [Cuadrático](https://en.wikipedia.org/wiki/Quadratic_probing): prueba de forma cuadrática `index(key,i) = h(key) + i^2`
- [Doble hash](https://en.wikipedia.org/wiki/Double_hashing): prueba usando una segunda función de hash `index(key,i) = h(key) + i*h2(key)`

<br/>

```cpp {all|2,3|4,5|6,7|all}
int calculateIndex(K key, unsigned int tryCount) {
  if (type == LINEAR_PROBING) 
    return abs(hashFunction(key) + tryCount) % buckets;
  else if (type == QUADRATIC_PROBING) 
    return abs(hashFunction(key) + pow(tryCount, 2)) % buckets;
  else if (type == DOUBLE_HASHING)
      return abs(hashFunction(key) + tryCount * hashFunction2(key)) % buckets;
}
```
<br>

> **Nota**: `i` es el número de intento.

---

# Hash abierto vs cerrado

|Abierto | Cerrado |
| --- | --- |
| Facilidad de implementación. | Requiere mayor cuidado, por ejemplo [cuando eliminamos](https://stackoverflow.com/questions/9127207/hash-table-why-deletion-is-difficult-in-open-addressing-scheme). |
| Nunca está "lleno" (λ puede ser mayor a 1). | El factor de carga **nunca** puede ser mayor a 1. |
| Menos sensible a la función de hash y el factor de carga. | Más sensible a la función de hash y el factor de carga. |


---

# Factor de carga (λ)
El factor de carga es un número (>=0) que indica que tan “lleno” está nuestra estructura.

```
λ = N / B
```

Donde N es la cantidad de elementos y B la cantidad de buckets

<br>

> Nota: el calculo de `λ` es el mismo para hash abierto o cerrado.

---

# Rehash
Una técnica que consiste en aumentar la cantidad de buckets.

A medida que la tabla de hash crece, nuestro λ también lo hace, lo cual aumenta la posibilidad de colisiones.

El re-hashing es una operación MUY costosa y debe ser debidamente planeada.

Por lo general el nuevo tamaño es el doble que el anterior

Tiene O(N) promedio.

<br>

> Nota: rehash es un concepto tanto para hash abierto comoo cerrado.

---

# Usos
No son buenas para todo. 🤷‍♂️

Las tablas de hash pueden ser muy útiles en operaciones como: `buscar`, `insertar` y `eliminar` elementos.

Son poco atractivas para el uso de operaciones donde los elementos están relacionados entre sí, por ejemplo listar de forma ordenada, o buscar el mínimo.


---

# Cuestionario

[https://tinyurl.com/36u39rde](https://tinyurl.com/36u39rde)
<QR qrText="https://tinyurl.com/36u39rde" qrWidth="300"></QR>
