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
  <a href="https://www.geeksforgeeks.org/hashing-data-structure/" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <file-icons-sandbox/>1
  </a>
  <a href="https://www.cs.usfca.edu/~galles/visualization/ClosedHash.html" target="_blank" alt="GitHub"
    class="text-xl icon-btn opacity-50 !border-none !hover:text-white">
    <file-icons-sandbox/>2
  </a>
</div>

---

# Que es una tablas de hash?

Es una estructura de datos que permite almacenar un conjunto de datos en **O(1)cp**

- Busqueda
- Insertar
- Eliminar

<br>
<br>

> 📗 Nota: Los elementos de la tabla de hash deben ser **unicos**.

<br/>

> 📘 Nota 2: Los elementos no necesitan definir un orden para ser almacenados. A diferencia de los ABB | AVL.


---
layout: image-right
image: https://c.tenor.com/IvyuPtEfzhoAAAAC/matrix.gif
---

# Vocabulario

## La tabla en si
Es un array que contendra los elementos.

## Buckets
Cada celda del array se lo conoce como "buckets" 🪣

## Funcion de hash
Toda tabla de hash necesita una funcion de hash para realizar sus operciones basicas.

---

# Caracteristicas de una funcion de hash

- Toma los elementos de la tabla los convierte a un **numero entero**.
- Deben ser **deterministas**.

<br>

```cpp
// Una funcion de hash que toma un string y devuelve 
// un entero.
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

# Caracteristicas de una **buena** funcion de hash ✅

<br>

<div class="grid grid-cols-2 gap-4">
  <div>
    <ul>
      <li>Evitar colisiones 💢</li>
      <li>Ser O(1)pc 🚀</li>
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

[Ejemplos de distribucion](https://docs.google.com/spreadsheets/d/1Rkgw8dTzOiEo9i2jh9iKmjVFG_UXsTeaLfKUk8GIkP4/edit#gid=0)

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

---
layout: center
class: text-center
---

# Learn More

[Documentations](https://sli.dev) · [GitHub](https://github.com/slidevjs/slidev) · [Showcases](https://sli.dev/showcases.html)
