## Declaración de variables

En TypeScript se recomienda indicar el tipo de dato.

### Sintaxis

```ts
let variable: tipo = valor;
```

Ejemplo:

```ts
let nombre:string = "Juan";
let edad:number = 25;
let activo:boolean = true;
```

Tipos básicos:

|Tipo|Descripción|Ejemplo|
|---|---|---|
|string|Texto|`"Juan"`|
|number|Números|`25`|
|boolean|Verdadero/Falso|`true`|
|array|Lista de valores|`["A","B"]`|
|void|Sin retorno|funciones|

---

## Corrección de tipos

Código incorrecto:

```ts
let nombre = 25;
let edad = "Juan";
let activo = "true";

function sumar(a,b){
    return a+b;
}
```

Problemas:

- Nombre debería ser texto.
    
- Edad debería ser número.
    
- Activo debería ser boolean.
    
- Función sin tipos.
    

Solución:

```ts
let nombre:string = "Juan";
let edad:number = 25;
let activo:boolean = true;

function sumar(a:number,b:number):number{
    return a+b;
}

console.log(sumar(5,6));
```

---

## Arreglos (Arrays)

Sintaxis:

```ts
let variable: tipo[] = [];
```

Ejemplo:

```ts
let asignaturas:string[] = [
    "Programación",
    "Base de datos"
];
```

---

## Ejemplo completo

```ts
let estudiante:string = "Andy";
let edadEstudiante:number = 21;
let matriculado:boolean = true;

let asignaturas:string[] = [
    "Programacion",
    "Base de datos"
];

function mostrarEstudiante():void{
    console.log(estudiante);
    console.log(edadEstudiante);
    console.log(matriculado);
    console.log(asignaturas);
}

mostrarEstudiante();
```

### `void`

Indica que una función **no devuelve ningún valor**.

Ejemplo:

```ts
function mostrar():void{
    console.log("Hola");
}
```