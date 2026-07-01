## Objetos en TypeScript

Los objetos permiten agrupar información.

Ejemplo:

```ts
let estudiante = {
    nombre:"Ana",
    edad:21,
    carrera:"Ingeniería en Software",
    activo:true
};
```

Acceder a propiedades:

```ts
console.log(estudiante.nombre);

console.log(estudiante.edad);
```

---

## Inferencia de tipos

TypeScript detecta automáticamente el tipo.

Ejemplo:

```ts
let edad = 21;
```

Internamente:

```ts
let edad:number = 21;
```

Esto se llama **Type Inference**.

---

# 04 - Interfaces

## ¿Qué es una interfaz?

Una interfaz define la estructura que debe cumplir un objeto.

Ejemplo:

```ts
interface Docente{
    nombre:string;
    asignatura:string;
    horas:number;
    activo:boolean;
}
```

Crear objetos:

```ts
let docente1:Docente = {
    nombre:"Juan",
    asignatura:"Matemáticas",
    horas:20,
    activo:true
};
```

---

## Propiedades opcionales (`?`)

Permiten que una propiedad exista o no.

```ts
interface Docente{
    nombre:string;
    asignatura:string;
    horas?:number;
    activo:boolean;
}
```

Si no existe:

```ts
undefined
```

Ejemplo:

```ts
const docente = {
    nombre:"Juan",
    activo:true
};
```

---

## Validar propiedades opcionales

Código seguro:

```ts
function dedicacion(
    horas?:number
):string{

    if(
        horas===undefined
    ){
        return
        "No definido";
    }

    return horas >= 8
        ? "Tiempo completo"
        : "Tiempo parcial";
}
```

Uso:

```ts
console.log(
    dedicacion(10)
);

console.log(
    dedicacion()
);
```

Resultado:

```txt
Tiempo completo
No definido
```

---

## Resumen

|Símbolo|Significado|
|---|---|
|:|Define tipo|
|?|Propiedad opcional|
|=>|Función flecha|
|void|No retorna|
|[]|Arreglo|