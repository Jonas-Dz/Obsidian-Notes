Dentro de la terminal, ejecuto este archivo touch
```
admin-glpi@glpipruebas:~/PracticaJD/CP$ nano ejercicio_sin_punteros.c
admin-glpi@glpipruebas:~/PracticaJD/CP$ gcc -O0 ejercicio_sin_punteros.c -o salida_ej_sp_0
```

El archivo ejercicio_sin_punteros.c tiene este  codigo:
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define N 1000000;

int main(){
        float A[N], B[N], C[N];

        for(int i = 0; i < N; i++ ){
                A[i] = i;
                B[i] = i*2;
        }

        clock_t inicio = clock();
        for(int i = 0; i < N; i++){
                C[i] = A[i] + B[i];
        }

        clock_t fin = clock();

        printf("Tiempo consumido: %.15f\n", (double) (final-inicio)/CLOCKS_PER_SEC);
}
```

Este ejercicio es bueno para SIMD, datos independientes misma operación. Uso instrucciones vectoriales

Además, cuando voy ejecutando
```
gcc -O0 ejercicio_sin_punteros.c -o salida_ej_sp_0
gcc -O1 ejercicio_sin_punteros.c -o salida_ej_sp_1
gcc -O2 ejercicio_sin_punteros.c -o salida_ej_sp_2
gcc -O3 ejercicio_sin_punteros.c -o salida_ej_sp_3
```

Y puedo notar que los tiempos de ejecución de cada una de las salidas **va disminuyendo**.

## Ejercicio con punteros

Realizo el mismo código al anterior
```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define N 1000000;

int main(){
        float *A = malloc(N = sizeof(float));
        float *B = malloc(N = sizeof(float));
        float *C = malloc(N = sizeof(float));

        for(int i = 0; i < N; i++ ){
                A[i] = i;
                B[i] = i*2;
        }

        clock_t inicio = clock();
        for(int i = 0; i < N; i++){
                C[i] = A[i] + B[i];
        }

        clock_t fin = clock();

        printf("Tiempo consumido: %.15f\n", (double) (final-inicio)/CLOCKS_PER_SEC);
        
        free(A);
        free(B);
        free(C);
}
```

Una vez realizado el código, nuevamente ejecuto varias salidas
```
gcc -O0 ejercicio_con_punteros.c -o salida_ej_cp_0
gcc -O1 ejercicio_con_punteros.c -o salida_ej_cp_1
gcc -O2 ejercicio_con_punteros.c -o salida_ej_cp_2
gcc -O3 ejercicio_con_punteros.c -o salida_ej_cp_3
```

Los tiempos consumidos:
- s1: hay mejor
- s2: hay mejora por el manejo vectorial
- s3: hay empeoramiento

**Los ejercicios siempre serán así, código y luego análisis de salida**

## Ejercicio multiplicación de matrices

```
#include <stdio.h> //printf
#include <stdlib.h> //malloc y free
#include <time.h> //clock_t,clock(), CLOCKS_PER_sEC

#define N 100000000
int main(){
     float A[N][N], B[N][N], C[N][N];

     for(int i=0;i<N;i++){
        for(int j=0;j<N;j++){
            A[i][j]=i;
            B[i][j]=i*2;
        }
     }

     clock_t inicio = clock();


     for(int i=0;i<N;i++){
        for(int j=0;j<N;j++){
            for(int k=0;k<N;k++){
                C[i][j]+=A[i][k]*B[k][j];
            }

        }
     }

     clock_t final=clock();

     printf("Tiempo consumido: %.15f\n",(double) (final-inicio)/CLOCKS_PER_SEC);

}
```

**Deber buscar la manera más optimizada de multiplicar la matriz**

## Ejercicio ejercicio.c

```
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define N 1000000

int main(){
        float *vector = malloc(N*size(float));

        for(int i=0; i<N; i++){
                vector[i]=i;
        }

        float suma = 0;

        clock_t inicio = clock();

        for(int i = 0; i<N; i++){
                suma += vector[i];
        }

        clock_t final = clock();

        printf("Tiempo: %.15f \n", (double)final - inicio / CLOCKS_PER_SEC);

}
```

Para el taller se realizarán ejercicios similares donde se usen punteros, sin punteros, matrices, matrices optimizadas, acceso a vectores
Cambia la declaracion de matrices con y sin punteros, revisar la multiplicacion de matrices.

Posterior a eso revisar los resultados y analizarlos (optimizacion, uso de RAM, etc)