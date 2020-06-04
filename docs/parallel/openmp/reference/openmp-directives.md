---
title: Directivas de OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP directives
- atomic
- barrier
- critical
- flush
- for
- master
- parallel
- section
- single
- threadprivate
helpviewer_keywords:
- OpenMP directives
- atomic OpenMP directive
- barrier OpenMP directive
- critical OpenMP directive
- flush OpenMP directive
- for OpenMP directive
- master OpenMP directive
- ordered OpenMP directive
- parallel OpenMP directive
- sections OpenMP directive
- single OpenMP directive
- threadprivate OpenMP directive
ms.assetid: 0562c263-344c-466d-843e-de830d918940
ms.openlocfilehash: 569419b3422b155afc6e9692efaecd4e5a06f188
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366439"
---
# <a name="openmp-directives"></a>Directivas de OpenMP

Proporciona vínculos a directivas utilizadas en la API de OpenMP.

Visual C++ admite las siguientes directivas OpenMP.

Para compartir trabajo en paralelo:

|Directiva|Descripción|
|---------|-----------|
|[parallel](#parallel)|Define una región paralela, que es código que ejecutarán varios subprocesos en paralelo.|
|[for](#for-openmp)|Hace que el `for` trabajo realizado en un bucle dentro de una región paralela se divida entre subprocesos.|
|[sections](#sections-openmp)|Identifica las secciones de código que se dividirán entre todos los subprocesos.|
|[single](#single)|Permite especificar que una sección de código se debe ejecutar en un único subproceso, no necesariamente en el subproceso maestro.|

Para maestro y sincronización:

|Directiva|Descripción|
|---------|-----------|
|[maestro](#master)|Especifica que solo el subproceso maestro debe ejecutar una sección del programa.|
|[crítica](#critical)|Especifica que el código solo se ejecuta en un subproceso a la vez.|
|[Barrera](#barrier)|Sincroniza todos los subprocesos de un equipo; todos los subprocesos se detienen en la barrera, hasta que todos los subprocesos ejecutan la barrera.|
|[atómica](#atomic)|Especifica que una ubicación de memoria que se actualizará atómicamente.|
|[rubor](#flush-openmp)|Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.|
|[Ordenó](#ordered-openmp-directives)|Especifica que el código `for` bajo un bucle paralelizado se debe ejecutar como un bucle secuencial.|

Para el entorno de datos:

|Directiva|Descripción|
|---------|-----------|
|[threadprivate](#threadprivate)|Especifica que una variable es privada para un subproceso.|

## <a name="atomic"></a><a name="atomic"></a>Atómica

Especifica que una ubicación de memoria que se actualizará atómicamente.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
La instrucción que tiene el *valor l*, cuya ubicación de memoria desea proteger contra más de una escritura.

### <a name="remarks"></a>Observaciones

La `atomic` directiva no admite cláusulas.

Para obtener más información, consulte [2.6.4 construcción atómica](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_atomic.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

#define MAX 10

int main() {
   int count = 0;
   #pragma omp parallel num_threads(MAX)
   {
      #pragma omp atomic
      count++;
   }
   printf_s("Number of threads: %d\n", count);
}
```

```Output
Number of threads: 10
```

## <a name="barrier"></a><a name="barrier"></a>Barrera

Sincroniza todos los subprocesos de un equipo; todos los subprocesos se detienen en la barrera, hasta que todos los subprocesos ejecutan la barrera.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Observaciones

La `barrier` directiva no admite cláusulas.

Para obtener más información, consulte [la Directiva de barrera 2.6.3](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Ejemplo

Para obtener un ejemplo `barrier`de cómo utilizar , consulte [master](#master).

## <a name="critical"></a><a name="critical"></a>Crítico

Especifica que el código solo se ejecuta en un subproceso a la vez.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*name*<br/>
(Opcional) Un nombre para identificar el código crítico. El nombre debe estar entre paréntesis.

### <a name="remarks"></a>Observaciones

La `critical` directiva no admite cláusulas.

Para obtener más información, consulte [2.6.2 construcción crítica](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_critical.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>

#define SIZE 10

int main()
{
    int i;
    int max;
    int a[SIZE];

    for (i = 0; i < SIZE; i++)
    {
        a[i] = rand();
        printf_s("%d\n", a[i]);
    }

    max = a[0];
    #pragma omp parallel for num_threads(4)
        for (i = 1; i < SIZE; i++)
        {
            if (a[i] > max)
            {
                #pragma omp critical
                {
                    // compare a[i] and max again because max
                    // could have been changed by another thread after
                    // the comparison outside the critical section
                    if (a[i] > max)
                        max = a[i];
                }
            }
        }

    printf_s("max = %d\n", max);
}
```

```Output
41
18467
6334
26500
19169
15724
11478
29358
26962
24464
max = 29358
```

## <a name="flush"></a><a name="flush-openmp"></a>rubor

Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parámetros

*Var*<br/>
(Opcional) Una lista separada por comas de variables que representan los objetos que desea sincronizar. Si no se especifica *var,* se vacía toda la memoria.

### <a name="remarks"></a>Observaciones

La `flush` directiva no admite cláusulas.

Para obtener más información, consulte [2.6.5 flush directive](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_flush.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

void read(int *data) {
   printf_s("read data\n");
   *data = 1;
}

void process(int *data) {
   printf_s("process data\n");
   (*data)++;
}

int main() {
   int data;
   int flag;

   flag = 0;

   #pragma omp parallel sections num_threads(2)
   {
      #pragma omp section
      {
         printf_s("Thread %d: ", omp_get_thread_num( ));
         read(&data);
         #pragma omp flush(data)
         flag = 1;
         #pragma omp flush(flag)
         // Do more work.
      }

      #pragma omp section
      {
         while (!flag) {
            #pragma omp flush(flag)
         }
         #pragma omp flush(data)

         printf_s("Thread %d: ", omp_get_thread_num( ));
         process(&data);
         printf_s("data = %d\n", data);
      }
   }
}
```

```Output
Thread 0: read data
Thread 1: process data
data = 2
```

## <a name="for"></a><a name="for-openmp"></a>Para

Hace que el `for` trabajo realizado en un bucle dentro de una región paralela se divida entre subprocesos.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parámetros

*Cláusulas*<br/>
(Opcional) Cero o más cláusulas, consulte la sección **Comentarios.**

*for_statement*<br/>
Un `for` bucle. Se producirá un comportamiento indefinido `for` si el código de usuario del bucle cambia la variable de índice.

### <a name="remarks"></a>Observaciones

La `for` directiva admite las siguientes cláusulas:

- [Privado](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [Ordenó](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Si `parallel` también se `clauses` especifica, puede ser `parallel` cualquier `for` cláusula aceptada `nowait`por las directivas o, excepto .

Para obtener más información, consulte [2.4.1 para construir](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_for.cpp
// compile with: /openmp
#include <stdio.h>
#include <math.h>
#include <omp.h>

#define NUM_THREADS 4
#define NUM_START 1
#define NUM_END 10

int main() {
   int i, nRet = 0, nSum = 0, nStart = NUM_START, nEnd = NUM_END;
   int nThreads = 0, nTmp = nStart + nEnd;
   unsigned uTmp = (unsigned((abs(nStart - nEnd) + 1)) *
                               unsigned(abs(nTmp))) / 2;
   int nSumCalc = uTmp;

   if (nTmp < 0)
      nSumCalc = -nSumCalc;

   omp_set_num_threads(NUM_THREADS);

   #pragma omp parallel default(none) private(i) shared(nSum, nThreads, nStart, nEnd)
   {
      #pragma omp master
      nThreads = omp_get_num_threads();

      #pragma omp for
      for (i=nStart; i<=nEnd; ++i) {
            #pragma omp atomic
            nSum += i;
      }
   }

   if  (nThreads == NUM_THREADS) {
      printf_s("%d OpenMP threads were used.\n", NUM_THREADS);
      nRet = 0;
   }
   else {
      printf_s("Expected %d OpenMP threads, but %d were used.\n",
               NUM_THREADS, nThreads);
      nRet = 1;
   }

   if (nSum != nSumCalc) {
      printf_s("The sum of %d through %d should be %d, "
               "but %d was reported!\n",
               NUM_START, NUM_END, nSumCalc, nSum);
      nRet = 1;
   }
   else
      printf_s("The sum of %d through %d is %d\n",
               NUM_START, NUM_END, nSum);
}
```

```Output
4 OpenMP threads were used.
The sum of 1 through 10 is 55
```

## <a name="master"></a><a name="master"></a>Maestro

Especifica que solo el subproceso maestro debe ejecutar una sección del programa.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Observaciones

La `master` directiva no admite cláusulas.

La [directiva single](#single) le permite especificar que una sección de código se debe ejecutar en un único subproceso, no necesariamente el subproceso maestro.

Para obtener más información, consulte [2.6.1 master construct](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_master.cpp
// compile with: /openmp
#include <omp.h>
#include <stdio.h>

int main( )
{
    int a[5], i;

    #pragma omp parallel
    {
        // Perform some computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] = i * i;

        // Print intermediate results.
        #pragma omp master
            for (i = 0; i < 5; i++)
                printf_s("a[%d] = %d\n", i, a[i]);

        // Wait.
        #pragma omp barrier

        // Continue with the computation.
        #pragma omp for
        for (i = 0; i < 5; i++)
            a[i] += i;
    }
}
```

```Output
a[0] = 0
a[1] = 1
a[2] = 4
a[3] = 9
a[4] = 16
```

## <a name="ordered"></a><a name="ordered-openmp-directives"></a>Ordenó

Especifica que el código `for` bajo un bucle paralelizado se debe ejecutar como un bucle secuencial.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Observaciones

La `ordered` directiva debe estar dentro de `parallel for` la extensión `ordered` dinámica de un [for](#for-openmp) o construir con una cláusula.

La `ordered` directiva no admite cláusulas.

Para obtener más información, consulte [2.6.6 construcción ordenada](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_ordered.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

static float a[1000], b[1000], c[1000];

void test(int first, int last)
{
    #pragma omp for schedule(static) ordered
    for (int i = first; i <= last; ++i) {
        // Do something here.
        if (i % 2)
        {
            #pragma omp ordered
            printf_s("test() iteration %d\n", i);
        }
    }
}

void test2(int iter)
{
    #pragma omp ordered
    printf_s("test2() iteration %d\n", iter);
}

int main( )
{
    int i;
    #pragma omp parallel
    {
        test(1, 8);
        #pragma omp for ordered
        for (i = 0 ; i < 5 ; i++)
            test2(i);
    }
}
```

```Output
test() iteration 1
test() iteration 3
test() iteration 5
test() iteration 7
test2() iteration 0
test2() iteration 1
test2() iteration 2
test2() iteration 3
test2() iteration 4
```

## <a name="parallel"></a><a name="parallel"></a>Paralelo

Define una región paralela, que es código que ejecutarán varios subprocesos en paralelo.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*Cláusulas*<br/>
(Opcional) Cero o más cláusulas, consulte la sección **Comentarios.**

### <a name="remarks"></a>Observaciones

La `parallel` directiva admite las siguientes cláusulas:

- [if](openmp-clauses.md#if-openmp)
- [Privado](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [default](openmp-clauses.md#default-openmp)
- [Compartido](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

`parallel`también se puede utilizar con las directivas [for](#for-openmp) y [sections.](#sections-openmp)

Para obtener más información, vea [2.3 construcción paralela](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer el número de subprocesos y definir una región paralela. El número de subprocesos es igual de predeterminado al número de procesadores lógicos de la máquina. Por ejemplo, si tiene una máquina con un procesador físico que tiene habilitado el hyperthreading, tendrá dos procesadores lógicos y dos subprocesos. El orden de salida puede variar en diferentes máquinas.

```cpp
// omp_parallel.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(4)
   {
      int i = omp_get_thread_num();
      printf_s("Hello from thread %d\n", i);
   }
}
```

```Output
Hello from thread 0
Hello from thread 1
Hello from thread 2
Hello from thread 3
```

## <a name="sections"></a><a name="sections-openmp"></a>Secciones

Identifica las secciones de código que se dividirán entre todos los subprocesos.

```cpp
#pragma omp [parallel] sections [clauses]
{
   #pragma omp section
   {
      code_block
   }
}
```

### <a name="parameters"></a>Parámetros

*Cláusulas*<br/>
(Opcional) Cero o más cláusulas, consulte la sección **Comentarios.**

### <a name="remarks"></a>Observaciones

La `sections` directiva puede contener `section` cero o más directivas.

La `sections` directiva admite las siguientes cláusulas:

- [Privado](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Si `parallel` también se `clauses` especifica, puede ser `parallel` cualquier `sections` cláusula aceptada `nowait`por las directivas o, excepto .

Para obtener más información, consulte [2.4.2 secciones construir](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_sections.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
    #pragma omp parallel sections num_threads(4)
    {
        printf_s("Hello from thread %d\n", omp_get_thread_num());
        #pragma omp section
        printf_s("Hello from thread %d\n", omp_get_thread_num());
    }
}
```

```Output
Hello from thread 0
Hello from thread 0
```

## <a name="single"></a><a name="single"></a>soltero

Permite especificar que una sección de código se debe ejecutar en un único subproceso, no necesariamente en el subproceso maestro.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*Cláusulas*<br/>
(Opcional) Cero o más cláusulas, consulte la sección **Comentarios.**

### <a name="remarks"></a>Observaciones

La `single` directiva admite las siguientes cláusulas:

- [Privado](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

La directiva [maestra](#master) le permite especificar que una sección de código se debe ejecutar solo en el subproceso maestro.

Para obtener más información, consulte [2.4.3 construcción única](../../../parallel/openmp/2-4-3-single-construct.md).

### <a name="example"></a>Ejemplo

```cpp
// omp_single.cpp
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int main() {
   #pragma omp parallel num_threads(2)
   {
      #pragma omp single
      // Only a single thread can read the input.
      printf_s("read input\n");

      // Multiple threads in the team compute the results.
      printf_s("compute results\n");

      #pragma omp single
      // Only a single thread can write the output.
      printf_s("write output\n");
    }
}
```

```Output
read input
compute results
compute results
write output
```

## <a name="threadprivate"></a><a name="threadprivate"></a>threadprivate

Especifica que una variable es privada para un subproceso.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parámetros

*Var*<br/>
Una lista separada por comas de variables que desea que sean privadas para un subproceso. *var* debe ser una variable de ámbito global o de espacio de nombres o una variable estática local.

### <a name="remarks"></a>Observaciones

La `threadprivate` directiva no admite cláusulas.

La `threadprivate` directiva se basa en el atributo [thread](../../../cpp/thread.md) mediante la palabra clave [__declspec;](../../../cpp/declspec.md) límites `__declspec(thread)` en `threadprivate`aplicar a . Por ejemplo, `threadprivate` una variable existirá en cualquier subproceso iniciado en el proceso, no solo en aquellos subprocesos que forman parte de un equipo de subprocesos generado por una región paralela. Tenga en cuenta este detalle de implementación; puede observar que los `threadprivate` constructores de un tipo definido por el usuario se llaman con más frecuencia y que se espera.

Puede usar `threadprivate` en un archivo DLL que se carga estáticamente al `threadprivate` iniciar el proceso, sin embargo, no se puede utilizar en ningún archivo DLL que `LoadLibrary`se cargará a través de [LoadLibrary,](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) como los archivos DLL que se cargan con [/DELAYLOAD (importación](../../../build/reference/delayload-delay-load-import.md)de carga de retardo), que también usa .

No `threadprivate` se garantiza que una variable de un tipo *destructible* tenga su destructor llamado. Por ejemplo:

```cpp
struct MyType
{
    ~MyType();
};

MyType threaded_var;
#pragma omp threadprivate(threaded_var)
int main()
{
    #pragma omp parallel
    {}
}
```

Los usuarios no tienen ningún control en cuanto a cuándo finalizarán los subprocesos que constituyen la región paralela. Si esos subprocesos existen cuando se cierra el proceso, los subprocesos no se notificarán `threaded_var` sobre la salida del proceso y no se llamará al destructor en ningún subproceso excepto en el que sale (aquí, el subproceso principal). Por lo tanto, el código `threadprivate` no debe contar con la destrucción adecuada de las variables.

Para obtener más información, consulte [2.7.1 threadprivate directive](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Ejemplo

Para obtener un `threadprivate`ejemplo de uso, consulte [private](openmp-clauses.md#private-openmp).
