# Archivos de cabecera más comunes

A continuación se muestran los archivos de cabecera más comunmente usados en los programas en C que se usan en mis cursos de Sistemas Operativos y Sistemas Distribuidos.

| Archivo de cabecera | Funciones definidas |
|:-:|---|
| `stdlib.h` | `srand()` `rand()` |
| `pthread.h` | `pthread_create()` `pthread_join()` `pthread_*` |
| `mpi.h` | `


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
#include "mpi.h"

int main(){ 
  MPI_Init(NULL, NULL);  
  printf("Wonderful Class!\n");
  MPI_Finalize(); 

  return(0);
}
```

Compilar,

```
mpicc mpi.c -o mpi
```

Ejecutar

```
mpirun -n 8 ./mpi
```
