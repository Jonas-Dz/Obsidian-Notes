#### Script MPI
```
#include <mpi.h>
#include <stdio.h>
#include <string.h>
#include <unistd.h>

void trabajo_local(int rank)
{
    for (int i = 1; i <= 5; i++)
    {
        printf("[Proceso %d] Realizando trabajo local... segundo %d\n", rank, i);
        fflush(stdout);
        sleep(1);
    }
}

int main(int argc, char **argv)
{
    MPI_Init(&argc, &argv);
    int rank, size;
    MPI_Comm_rank(MPI_COMM_WORLD, &rank);
    MPI_Comm_size(MPI_COMM_WORLD, &size);
    if (size != 2)
    {
        if (rank == 0)
        {
            printf("Este programa debe ejecutarse con exactamente 2 procesos.\n");
            printf("Ejemplo:\n");
            printf("mpirun -np 2 ./demo bloqueante\n");
            printf("mpirun -np 2 ./demo nobloqueante\n");
        }
        MPI_Finalize();
        return 0;
    }
    if (argc < 2)
    {
        if (rank == 0)
        {
            printf("Debe indicar el modo de ejecución:\n");
            printf("mpirun -np 2 ./demo bloqueante\n");
            printf("mpirun -np 2 ./demo nobloqueante\n");
        }
        MPI_Finalize();
        return 0;
    }
    int numero = 123;
    MPI_Request request;
    MPI_Barrier(MPI_COMM_WORLD);
    double inicio = MPI_Wtime();
    if (strcmp(argv[1], "bloqueante") == 0)
    {
        if (rank == 0)
        {
            printf("\n=== MODO BLOQUEANTE ===\n");
            printf("[Proceso 0] Intentando enviar con MPI_Ssend...\n");
            printf("[Proceso 0] Si el proceso 1 no recibe, yo me quedo esperando.\n");
            fflush(stdout);
            MPI_Ssend(&numero, 1, MPI_INT, 1, 0, MPI_COMM_WORLD);
            printf("[Proceso 0] El envío terminó. Ahora recién puedo trabajar.\n");
            fflush(stdout);
            trabajo_local(rank);
            double fin = MPI_Wtime();
            printf("[Proceso 0] Tiempo total aproximado: %.2f segundos\n", fin - inicio);
            fflush(stdout);
        }
        if (rank == 1)
        {
            printf("[Proceso 1] Voy a esperar 5 segundos antes de recibir...\n");
            fflush(stdout);
            sleep(5);
            printf("[Proceso 1] Ahora sí ejecuto MPI_Recv.\n");
            fflush(stdout);
            MPI_Recv(&numero, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
            printf("[Proceso 1] Recibí el número: %d\n", numero);
            fflush(stdout);
        }
    }
    else if (strcmp(argv[1], "nobloqueante") == 0)
    {
        if (rank == 0)
        {
            printf("\n=== MODO NO BLOQUEANTE ===\n");
            printf("[Proceso 0] Inicio el envío con MPI_Issend...\n");
            printf("[Proceso 0] No me quedo esperando inmediatamente; puedo trabajar.\n");
            fflush(stdout);
            MPI_Issend(&numero, 1, MPI_INT, 1, 0, MPI_COMM_WORLD, &request);
            trabajo_local(rank);
            printf("[Proceso 0] Ya terminé mi trabajo local. Ahora verifico el envío con MPI_Wait.\n");
            fflush(stdout);
            MPI_Wait(&request, MPI_STATUS_IGNORE);
            double fin = MPI_Wtime();
            printf("[Proceso 0] Envío confirmado.\n");
            printf("[Proceso 0] Tiempo total aproximado: %.2f segundos\n", fin - inicio);
            fflush(stdout);
        }
        if (rank == 1)
        {
            printf("[Proceso 1] Voy a esperar 5 segundos antes de recibir...\n");
            fflush(stdout);
            sleep(5);
            printf("[Proceso 1] Ahora sí ejecuto MPI_Recv.\n");
            fflush(stdout);
            MPI_Recv(&numero, 1, MPI_INT, 0, 0, MPI_COMM_WORLD, MPI_STATUS_IGNORE);
            printf("[Proceso 1] Recibí el número: %d\n", numero);
            fflush(stdout);
        }
    }
    else
    {
        if (rank == 0)
        {
            printf("Modo no válido. Use:\n");
            printf("bloqueante\n");
            printf("nobloqueante\n");
        }
    }
    MPI_Finalize();
    return 0;
}
```

#### En Ubuntu
Comando para instalar (Ubuntu):
`sudo apt install openmpi-bin libopenmpi-dev`

Comando para compilar (Ubuntu):
`mpicc demo_bloqueante_no_bloqueante.c -o demo`

Comando para ejecutar:
```
mpirun -np 2 ./demo bloqueante
mpirun -np 2 ./demo nobloqueante
```

---
#### En Fedora
Comando para instalar (Fedora):
`sudo dnf install openmpi openmpi-devel`

Instalar el soporte para módulos:
`sudo dnf install environment-modules`

Reiniciar el terminal:
`exec bash`

Cargar el módulo de Open MPI (Fedora):
`module load mpi/openmpi-x86_64`

Compilar (Fedora):
`mpicc demo_bloqueante_no_bloqueante.c -o demo`

Hacer pruebas con los valores de rango cambiados. 
Interpretar el funcionamiento del código para bloqueante y no bloqueante.
Como verificar que haya comunicación en el código de MPI


