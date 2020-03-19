# Archivos de cabecera más comunes

A continuación se muestran los archivos de cabecera más comunmente usados en los programas en C que se usan en mis cursos de Sistemas Operativos y Sistemas Distribuidos.

| Archivo de cabecera | Funciones definidas |
|:-:|---|
| `stdlib.h` | `srand()` `rand()` |
| `pthread.h` | `pthread_create()` `pthread_join()` `pthread_*` |


Ejemplos de programas en C para:

* [Archivo con hilos de ejecución](#archivo-con-hilos-de-ejecucion)



---

## Archivo con hilos de ejecucion

Asuma que el código abajo es almacenado en un archivo llamado `demo.c`.

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
gcc -pthread demo.c -o demo
```
