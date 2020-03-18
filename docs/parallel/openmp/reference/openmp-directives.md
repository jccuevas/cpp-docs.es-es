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
- ordered
- parallel
- section
- SECTIONS
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
ms.openlocfilehash: 4db341cf58884263e414e24aacf888c8c88e57cc
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79424156"
---
# <a name="openmp-directives"></a>Directivas de OpenMP

Proporciona vínculos a las directivas usadas en la API de OpenMP.

Visual C++ admite las siguientes directivas de OpenMP.

Para el uso compartido de trabajo paralelo:

|Directiva|Descripción|
|---------|-----------|
|[parallel](#parallel)|Define una región paralela, que es código que se ejecutará en varios subprocesos en paralelo.|
|[for](#for-openmp)|Hace que el trabajo realizado en un bucle de `for` dentro de una región paralela se divida entre subprocesos.|
|[sections](#sections-openmp)|Identifica las secciones de código que se van a dividir entre todos los subprocesos.|
|[single](#single)|Permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente en el subproceso principal.|

Para maestro y sincronización:

|Directiva|Descripción|
|---------|-----------|
|[maestra](#master)|Especifica que solo el subproceso principal debe ejecutar una sección del programa.|
|[crítica](#critical)|Especifica que el código solo se ejecuta en un subproceso cada vez.|
|[barrier](#barrier)|Sincroniza todos los subprocesos de un equipo; todos los subprocesos se pausan en la barrera, hasta que todos los subprocesos ejecutan la barrera.|
|[atomic](#atomic)|Especifica que una ubicación de memoria que se actualizará de forma atómica.|
|[flush](#flush-openmp)|Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.|
|[ordenar](#ordered-openmp-directives)|Especifica que el código bajo un bucle de `for` en paralelo debe ejecutarse como un bucle secuencial.|

Para el entorno de datos:

|Directiva|Descripción|
|---------|-----------|
|[threadprivate](#threadprivate)|Especifica que una variable es privada en un subproceso.|

## <a name="atomic"></a>elemental

Especifica que una ubicación de memoria que se actualizará de forma atómica.

```cpp
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parámetros

*expression*<br/>
La instrucción que tiene el valor *l*, cuya ubicación de memoria desea proteger frente a más de una escritura.

### <a name="remarks"></a>Observaciones

La Directiva `atomic` no admite cláusulas.

Para obtener más información, vea [2.6.4 Atomic construya](../../../parallel/openmp/2-6-4-atomic-construct.md).

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

## <a name="barrier"></a>barreras

Sincroniza todos los subprocesos de un equipo; todos los subprocesos se pausan en la barrera, hasta que todos los subprocesos ejecutan la barrera.

```cpp
#pragma omp barrier
```

### <a name="remarks"></a>Observaciones

La Directiva `barrier` no admite cláusulas.

Para obtener más información, vea [2.6.3 barrera Directive](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar `barrier`, vea [Master](#master).

## <a name="critical"></a>suma

Especifica que el código solo se ejecuta en un subproceso cada vez.

```cpp
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*name*<br/>
Opta Nombre para identificar el código crítico. El nombre debe ir entre paréntesis.

### <a name="remarks"></a>Observaciones

La Directiva `critical` no admite cláusulas.

Para obtener más información, vea [2.6.2 Critical (Critical Construct](../../../parallel/openmp/2-6-2-critical-construct.md).

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

## <a name="flush-openmp"></a>consumir

Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.

```cpp
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parámetros

*var*<br/>
Opta Lista separada por comas de variables que representan los objetos que desea sincronizar. Si no se especifica *var* , se vacía toda la memoria.

### <a name="remarks"></a>Observaciones

La Directiva `flush` no admite cláusulas.

Para obtener más información, vea [la Directiva de vaciado 2.6.5](../../../parallel/openmp/2-6-5-flush-directive.md).

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

## <a name="for-openmp"></a>para

Hace que el trabajo realizado en un bucle de `for` dentro de una región paralela se divida entre subprocesos.

```cpp
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parámetros

*cláusulas*<br/>
Opta Cero o más cláusulas, vea la sección **comentarios** .

*for_statement*<br/>
Un bucle `for`. Se producirá un comportamiento indefinido si el código de usuario del bucle `for` cambia la variable de índice.

### <a name="remarks"></a>Observaciones

La Directiva `for` admite las siguientes cláusulas:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [ordenar](openmp-clauses.md#ordered-openmp-clauses)
- [schedule](openmp-clauses.md#schedule)
- [nowait](openmp-clauses.md#nowait)

Si también se especifica `parallel`, `clauses` puede ser cualquier cláusula aceptada por las directivas `parallel` o `for`, excepto `nowait`.

Para obtener más información, vea [2.4.1 para construcciones](../../../parallel/openmp/2-4-1-for-construct.md).

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

## <a name="master"></a>maestra

Especifica que solo el subproceso principal debe ejecutar una sección del programa.

```cpp
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Observaciones

La Directiva `master` no admite cláusulas.

La [única](#single) directiva le permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente en el subproceso principal.

Para obtener más información, vea [2.6.1 Master (construcción](../../../parallel/openmp/2-6-1-master-construct.md)).

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

## <a name="ordered-openmp-directives"></a>ordenar

Especifica que el código bajo un bucle de `for` en paralelo debe ejecutarse como un bucle secuencial.

```cpp
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Observaciones

La Directiva de `ordered` debe estar dentro de la extensión dinámica de una construcción [for](#for-openmp) o `parallel for` con una cláusula `ordered`.

La Directiva `ordered` no admite cláusulas.

Para obtener más información, vea [2.6.6 ordered Construct](../../../parallel/openmp/2-6-6-ordered-construct.md).

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

## <a name="parallel"></a>poner

Define una región paralela, que es código que se ejecutará en varios subprocesos en paralelo.

```cpp
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*cláusulas*<br/>
Opta Cero o más cláusulas, vea la sección **comentarios** .

### <a name="remarks"></a>Observaciones

La Directiva `parallel` admite las siguientes cláusulas:

- [if](openmp-clauses.md#if-openmp)
- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [valor predeterminado](openmp-clauses.md#default-openmp)
- [recurso](openmp-clauses.md#shared-openmp)
- [copyin](openmp-clauses.md#copyin)
- [reduction](openmp-clauses.md#reduction)
- [num_threads](openmp-clauses.md#num-threads)

también se puede usar `parallel` con las directivas [for](#for-openmp) y [Sections](#sections-openmp) .

Para obtener más información, consulte [construcción paralela 2,3](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo establecer el número de subprocesos y definir una región paralela. De forma predeterminada, el número de subprocesos es igual al número de procesadores lógicos del equipo. Por ejemplo, si tiene un equipo con un procesador físico que tiene habilitado hyperthreading, tendrá dos procesadores lógicos y dos subprocesos. El orden de salida puede variar en diferentes equipos.

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

## <a name="sections-openmp"></a>sección

Identifica las secciones de código que se van a dividir entre todos los subprocesos.

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

*cláusulas*<br/>
Opta Cero o más cláusulas, vea la sección **comentarios** .

### <a name="remarks"></a>Observaciones

La Directiva de `sections` puede contener cero o más directivas de `section`.

La Directiva `sections` admite las siguientes cláusulas:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [reduction](openmp-clauses.md#reduction)
- [nowait](openmp-clauses.md#nowait)

Si también se especifica `parallel`, `clauses` puede ser cualquier cláusula aceptada por las directivas `parallel` o `sections`, excepto `nowait`.

Para obtener más información, vea [2.4.2 Sections (construcción](../../../parallel/openmp/2-4-2-sections-construct.md)).

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

## <a name="single"></a>sencilla

Permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente en el subproceso principal.

```cpp
#pragma omp single [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*cláusulas*<br/>
Opta Cero o más cláusulas, vea la sección **comentarios** .

### <a name="remarks"></a>Observaciones

La Directiva `single` admite las siguientes cláusulas:

- [private](openmp-clauses.md#private-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [copyprivate](openmp-clauses.md#copyprivate)
- [nowait](openmp-clauses.md#nowait)

La directiva [Master](#master) permite especificar que una sección de código debe ejecutarse solo en el subproceso principal.

Para obtener más información, vea [2.4.3 Single (construcción](../../../parallel/openmp/2-4-3-single-construct.md)).

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

## <a name="threadprivate"></a>threadprivate

Especifica que una variable es privada en un subproceso.

```cpp
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parámetros

*var*<br/>
Lista separada por comas de las variables que desea convertir en privadas en un subproceso. *var* debe ser una variable global o de ámbito de espacio de nombres o una variable estática local.

### <a name="remarks"></a>Observaciones

La Directiva `threadprivate` no admite cláusulas.

La Directiva de `threadprivate` se basa en el atributo [Thread](../../../cpp/thread.md) mediante la palabra clave [__declspec](../../../cpp/declspec.md) ; los límites de `__declspec(thread)` se aplican a `threadprivate`. Por ejemplo, una variable de `threadprivate` existirá en cualquier subproceso iniciado en el proceso, no solo en los subprocesos que forman parte de un equipo de subprocesos generado por una región paralela. Tenga en cuenta este detalle de implementación; es posible que observe que se llama a los constructores para un `threadprivate` tipo definido por el usuario más a menudo.

Puede usar `threadprivate` en un archivo DLL que se carga de forma estática en el inicio del proceso; sin embargo, no puede usar `threadprivate` en ningún archivo DLL que se cargará a través de [LoadLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-loadlibraryw) , como archivos DLL que se cargan con [/DELAYLOAD (importación de carga retrasada)](../../../build/reference/delayload-delay-load-import.md), que también usa `LoadLibrary`.

No se garantiza que una variable `threadprivate` de un tipo *puede destruir* tenga su Destructor denominado. Por ejemplo:

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

Los usuarios no tienen ningún control sobre el momento en que se terminarán los subprocesos que constituyen la región paralela. Si esos subprocesos existen cuando finaliza el proceso, no se notificará a los subprocesos sobre la salida del proceso y no se llamará al destructor para `threaded_var` en ningún subproceso excepto en el que salga (aquí, el subproceso principal). Por lo tanto, el código no debe contar en la destrucción adecuada de las variables de `threadprivate`.

Para obtener más información, vea [la Directiva 2.7.1 threadprivate](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

### <a name="example"></a>Ejemplo

Para obtener un ejemplo del uso de `threadprivate`, vea [Private](openmp-clauses.md#private-openmp).
