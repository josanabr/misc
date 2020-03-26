# Archivos de cabecera más comunes

A continuación se muestran los archivos de cabecera más comunmente usados en los programas en C que se usan en mis cursos de Sistemas Operativos y Sistemas Distribuidos.

| Archivo de cabecera | Funciones definidas | Ejemplos |
|:-:|---|---|
| `stdlib.h` | `srand()` `rand()` | [rand](rand) |
| `pthread.h` | `pthread_create()` `pthread_join()` `pthread_*` ||
| `mpi.h` | `MPI_Init()`, `MPI_Finalize()`, `MPI_*` ||


Ejemplos de programas en C para:

* [pthread](#pthread)
* [mpi](#mpi)



---

## pthread

Asuma que el código abajo es almacenado en un archivo llamado `thread.c`.

```
#include <pthread.h>
#include <stdio.h>

void* func(void* arg) {
  printf("hilo en ejecucion\n");
  pthread_exit(NULL);
}

int main(int argc, char** argv) {

  pthread_t pid_hilo;

  pthread_create(&pid_hilo, NULL, func, NULL);
  printf("main en ejecucion\n");
  pthread_exit(NULL);
}
```

Para compilar el programa anterior:

```
gcc -pthread thread.c -o thread
```

---

## mpi

Asuma que el código abajo es almacenado en un archivo llamado `mpi.c`.

```
#include <stdio.h>
#include <mpi.h>
#include <limits.h>
#include <unistd.h>
    
int main(){
  int myrank, worldsize;
  char hostname[HOST_NAME_MAX + 1];
  gethostname(hostname, HOST_NAME_MAX + 1);
  MPI_Init(NULL, NULL);
  MPI_Comm_rank(MPI_COMM_WORLD, &myrank);
  MPI_Comm_size(MPI_COMM_WORLD, &worldsize);
  printf("Process %d says Wonderful Class from %s!\n",myrank,hostname);
  MPI_Finalize();

  return(0);
} 
```

Archivo con los nodos a usar en la ejecución. Asuma que este archivo se llama `hosts`.

```
localhost
```

Compilar,

```
mpicc mpi.c -o mpi
```

Ejecutar:

```
mpirun -n 8 -f hosts ./mpi
```
