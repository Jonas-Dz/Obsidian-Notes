## Funciones normales

Sintaxis:

```ts
function nombre(
    parametro:tipo
):tipoRetorno{
}
```

Ejemplo:

```ts
function sumar(
    a:number,
    b:number
):number{
    return a+b;
}

console.log(sumar(6,5));
```

---

## Funciones flecha (Arrow Functions)

Forma moderna y compacta.

Sintaxis:

```ts
const nombre = (
    parametros
):tipo => {
};
```

Ejemplo:

```ts
const calcularNotaFinal = (
    nota1:number,
    nota2:number,
    nota3:number
):number=>{
    return (
        nota1+
        nota2+
        nota3
    )/3;
};

const verificarAprobacion = (
    promedio:number
):string=>{
    return promedio >= 14
        ? "Aprobado"
        : "Reprobado";
};

let promedio =
    calcularNotaFinal(
        15,
        12,
        15
    );

console.log(promedio);
```

---

## Operador ternario

Forma corta de un `if`.

Sintaxis:

```ts
condicion
? valorVerdadero
: valorFalso
```

Ejemplo:

```ts
return promedio >= 14
? "Aprobado"
: "Reprobado";
```

---

## Buenas prácticas

Tipar parámetros  
Tipar retorno  
Nombres descriptivos  
Evitar funciones muy largas