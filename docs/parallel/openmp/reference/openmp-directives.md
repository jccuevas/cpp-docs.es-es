---
title: Directivas de OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 10/22/2018
ms.technology:
- cpp-parallel
ms.topic: reference
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98fec6659c2f4e998b946983a0bd2bdea6d0cde1
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50083261"
---
# <a name="openmp-directives"></a>Directivas de OpenMP

Proporciona vínculos a las directivas que se utilizan en la API de OpenMP.

Visual C++ admite las siguientes directivas de OpenMP:

|Directiva|Descripción|
|---------|-----------|
|[atomic](#atomic)|Especifica que una ubicación de memoria que se actualizarán de forma atómica.|
|[barrier](#barrier)|Sincroniza todos los subprocesos en un equipo; todos los subprocesos se detendrá en la barrera, hasta que todos los subprocesos ejecuten la barrera.|
|[critical](#critical)|Especifica que código solo se ejecuta en un subproceso a la vez.|
|[flush](#flush-openmp)|Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.|
|[for](#for-openmp)|Hace que el trabajo realizado en un `for` bucle dentro de una región paralela a dividirse entre subprocesos.|
|[master](#master)|Especifica que sólo el subproceso principal debe ejecutar una sección del programa.|
|[Ordenada](#ordered-openmp-directives)|Especifica que el código en una ejecución en paralelo `for` bucle se debe ejecutar como un bucle secuencial.|
|[parallel](#parallel)|Define una región paralela, que es código que se va a ejecutar varios subprocesos en paralelo.|
|[Secciones](#sections-openmp)|Identifica las secciones de código se divide entre todos los subprocesos.|
|[single](#single)|Le permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente el subproceso principal.|
|[threadprivate](#threadprivate)|Especifica que una variable privada a un subproceso.|

## <a name="atomic"></a>Atomic

Especifica que una ubicación de memoria que se actualizarán de forma atómica.

```
#pragma omp atomic
   expression
```

### <a name="parameters"></a>Parámetros

*Expresión*<br/>
La instrucción que tiene el valor de l, cuya ubicación de memoria que desea protegerse frente a más de una escritura. Para obtener más información acerca de los formularios de expresión legal, consulte la especificación OpenMP.

### <a name="remarks"></a>Comentarios

El `atomic` directiva es compatible con ningún cláusulas de OpenMP.

Para obtener más información, consulte [2.6.4 atomic construir](../../../parallel/openmp/2-6-4-atomic-construct.md).

### <a name="example"></a>Ejemplo

```
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

## <a name="barrier"></a>barrera

Sincroniza todos los subprocesos en un equipo; todos los subprocesos se detendrá en la barrera, hasta que todos los subprocesos ejecuten la barrera.

```
#pragma omp barrier
```

### <a name="remarks"></a>Comentarios

El `barrier` directiva es compatible con ningún cláusulas de OpenMP.

Para obtener más información, consulte [2.6.3 directiva barrera](../../../parallel/openmp/2-6-3-barrier-directive.md).

### <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar `barrier`, consulte [maestro](#master).

## <a name="critical"></a>Crítico

Especifica que código se solo se ejecuta en un subproceso a la vez.

```
#pragma omp critical [(name)]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*name*<br/>
(Opcional) Un nombre para identificar el código crítico. Tenga en cuenta que ese nombre debe ir entre paréntesis.

### <a name="remarks"></a>Comentarios

El `critical` directiva es compatible con ningún cláusulas de OpenMP.

Para obtener más información, consulte [2.6.2 críticos construir](../../../parallel/openmp/2-6-2-critical-construct.md).

### <a name="example"></a>Ejemplo

```
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

## <a name="flush-openmp"></a>Flush (OpenMP)

Especifica que todos los subprocesos tienen la misma vista de memoria para todos los objetos compartidos.

```
#pragma omp flush [(var)]
```

### <a name="parameters"></a>Parámetros

*var*<br/>
(Opcional) Una lista separada por comas de variables que representan los objetos que desea sincronizar. Si `var` no se especifica, toda la memoria se vacía.

### <a name="remarks"></a>Comentarios

El `flush` directiva es compatible con ningún cláusulas de OpenMP.

Para obtener más información, consulte [2.6.5 flush (directiva)](../../../parallel/openmp/2-6-5-flush-directive.md).

### <a name="example"></a>Ejemplo

```
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

## <a name="for-openmp"></a>(OpenMP)

Hace que el trabajo realizado en un `for` bucle dentro de una región paralela a dividirse entre subprocesos.

```
#pragma omp [parallel] for [clauses]
   for_statement
```

### <a name="parameters"></a>Parámetros

*Cláusulas*<br/>
(Opcional) Cero o más cláusulas. Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con `for`.

*for_Statement*<br/>
Un `for` bucle. Se producirá un comportamiento indefinido si el código de usuario de la `for` bucle cambia la variable de índice.

### <a name="remarks"></a>Comentarios

El `for` directiva es compatible con las cláusulas de OpenMP siguientes:

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [Ordenada](openmp-clauses.md#ordered-openmp-clauses)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [schedule](openmp-clauses.md#schedule)

Si `parallel` también se especifica, `clauses` puede ser cualquier cláusula aceptado por el `parallel` o `for` directivas, excepto `nowait`.

Para obtener más información, consulte [2.4.1 for (construcción)](../../../parallel/openmp/2-4-1-for-construct.md).

### <a name="example"></a>Ejemplo

```
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

## <a name="master"></a>Master

Especifica que sólo el subproceso principal debe ejecutar una sección del programa.

```
#pragma omp master
{
   code_block
}
```

### <a name="remarks"></a>Comentarios

El `master` directiva es compatible con ningún cláusulas de OpenMP.

El [único](#single) directiva le permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente el subproceso principal.

Para obtener más información, consulte [2.6.1 master construcción](../../../parallel/openmp/2-6-1-master-construct.md).

### <a name="example"></a>Ejemplo

```
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

## <a name="ordered-openmp-directives"></a>ordered (directivas de OpenMP)

Especifica que el código en una ejecución en paralelo `for` bucle se debe ejecutar como un bucle secuencial.

```
#pragma omp ordered
   structured-block
```

### <a name="remarks"></a>Comentarios

El `ordered` directiva debe estar dentro de la extensión dinámica de un [para](#for-openmp) o `parallel for` construir con un `ordered` cláusula.

El `ordered` directiva es compatible con ningún cláusulas de OpenMP.

Para obtener más información, consulte [2.6.6 ordered (construcción)](../../../parallel/openmp/2-6-6-ordered-construct.md).

### <a name="example"></a>Ejemplo

```
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

## <a name="parallel"></a>Paralelo

Define una región paralela, que es código que se va a ejecutar varios subprocesos en paralelo.

```
#pragma omp parallel [clauses]
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*Cláusulas*<br/>
(Opcional) Cero o más cláusulas.  Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con `parallel`.

### <a name="remarks"></a>Comentarios

El `parallel` directiva es compatible con las cláusulas de OpenMP siguientes:

- [copyin](openmp-clauses.md#copyin)
- [default](openmp-clauses.md#default-openmp)
- [firstprivate](openmp-clauses.md#firstprivate)
- [if](openmp-clauses.md#if-openmp)
- [num_threads](openmp-clauses.md#num-threads)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)
- [Compartido](openmp-clauses.md#shared-openmp)

`parallel` También puede utilizarse con el [secciones](#sections-openmp) y [para](#for-openmp) directivas.

Para obtener más información, consulte [2.3 parallel (construcción)](../../../parallel/openmp/2-3-parallel-construct.md).

### <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo establecer el número de subprocesos y definir una región paralela. El número de subprocesos es igual de forma predeterminada en el número de procesadores lógicos en el equipo. Por ejemplo, si tiene un equipo con un procesador físico que tiene habilitado el hiperproceso, tendrá dos procesadores lógicos y dos subprocesos.

```
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

### <a name="comment"></a>Comentario

Tenga en cuenta que el orden de salida puede variar en equipos diferentes.

## <a name="sections-openmp"></a>secciones (OpenMP)

Identifica las secciones de código se divide entre todos los subprocesos.

```
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
(Opcional) Cero o más cláusulas. Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con `sections`.

### <a name="remarks"></a>Comentarios

El `sections` directiva puede contener cero o más `section` directivas.

El `sections` directiva es compatible con las cláusulas de OpenMP siguientes:

- [firstprivate](openmp-clauses.md#firstprivate)
- [lastprivate](openmp-clauses.md#lastprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)
- [reduction](openmp-clauses.md#reduction)

Si `parallel` también se especifica, `clauses` puede ser cualquier cláusula aceptado por el `parallel` o `sections` directivas, excepto `nowait`.

Para obtener más información, consulte [2.4.2 sections (construcción)](../../../parallel/openmp/2-4-2-sections-construct.md).

### <a name="example"></a>Ejemplo

```
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

## <a name="single"></a>único

Le permite especificar que una sección de código debe ejecutarse en un único subproceso, no necesariamente el subproceso principal.

```
#pragma omp single [clauses] 
{
   code_block
}
```

### <a name="parameters"></a>Parámetros

*Cláusulas*<br/>
(Opcional) Cero o más cláusulas. Vea la sección Comentarios para obtener una lista de las cláusulas compatibles con `single`.

### <a name="remarks"></a>Comentarios

El `single` directiva es compatible con las cláusulas de OpenMP siguientes:

- [copyprivate](openmp-clauses.md#copyprivate)
- [firstprivate](openmp-clauses.md#firstprivate)
- [nowait](openmp-clauses.md#nowait)
- [private](openmp-clauses.md#private-openmp)

El [maestro](#master) directiva le permite especificar que una sección de código debe ejecutarse solo en el subproceso principal.

Para obtener más información, consulte [2.4.3 single construir](../../../parallel/openmp/2-4-3-single-construct.md).

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

Especifica que una variable privada a un subproceso.

```
#pragma omp threadprivate(var)
```

### <a name="parameters"></a>Parámetros

*var*<br/>
Una lista separada por comas de variables que desea convertir en privado a un subproceso. `var` debe ser una variable global o espacio de nombres de ámbito o una variable local estática.

### <a name="remarks"></a>Comentarios

El `threadprivate` directiva es compatible con ningún cláusulas de OpenMP.

Para obtener más información, consulte [2.7.1 threadprivate (directiva)](../../../parallel/openmp/2-7-1-threadprivate-directive.md).

El `threadprivate` directiva se basa en el [subproceso](../../../cpp/thread.md) atributo mediante la [__declspec](../../../cpp/declspec.md) palabra clave; límites en `__declspec(thread)` se aplican a `threadprivate`.

No puede usar `threadprivate` en cualquier archivo DLL que se cargan a través de [LoadLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-loadlibrarya).  Esta prohibición incluye los archivos DLL que se cargan con [/DELAYLOAD (Retrasar importación de carga)](../../../build/reference/delayload-delay-load-import.md), que también utiliza `LoadLibrary`.

Puede usar `threadprivate` en un archivo DLL que se carga estáticamente al iniciarse el proceso.

Dado que `threadprivate` se basa en `__declspec(thread)`, un `threadprivate` variable existirá en cualquier subproceso que inició en el proceso, no solo entre los subprocesos que forman parte de un grupo de subprocesos generado por una región paralela.  Tenga en cuenta este detalle de implementación. es posible que observe, por ejemplo, que los constructores de una `threadprivate` se denominan más a menudo, a continuación, se esperaba el tipo definido por el usuario.

Un `threadprivate` variable de un tipo destructable no está garantizado que tiene su destructor denominado.  Por ejemplo:

```
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

Los usuarios no tienen ningún control sobre cuándo se terminarán los subprocesos que constituyen la región paralela.  Si esos subprocesos existen cuando se cierra el proceso, los subprocesos no se le notifique la salida del proceso y no se llama al destructor para `threaded_var` en cualquier subproceso, excepto en el que se cierra (aquí, el subproceso principal).  Por lo que el código no debería contar con la destrucción adecuada de `threadprivate` variables.

### <a name="example"></a>Ejemplo

Para obtener un ejemplo del uso de `threadprivate`, consulte [privada](openmp-clauses.md#private-openmp).
