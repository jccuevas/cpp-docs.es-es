---
title: R. Ejemplos
ms.date: 01/18/2019
ms.assetid: c0f6192f-a205-449b-b84c-cb30dbcc8b8f
ms.openlocfilehash: 061490d34829175bfbdcd84d6208aa396bb19671
ms.sourcegitcommit: 382e247c0f1b4cb7c2dab837b8b6fdff24bff47a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/28/2019
ms.locfileid: "55087306"
---
# <a name="a-examples"></a>R. Ejemplos

Los siguientes son ejemplos de las estructuras definidas en este documento. Una instrucción que sigue a una directiva está compuesta solo cuando sea necesario y se aplica sangría a una instrucción que no es compuesta de una directiva que le precede.

## <a name="a1-a-simple-loop-in-parallel"></a>A.1 un simple bucle en paralelo

En el ejemplo siguiente se muestra cómo paralelizar un bucle con el [paralelas para](2-directives.md#251-parallel-for-construct) directiva. La variable de iteración del bucle es privada de forma predeterminada, por lo que no es necesario especificarla explícitamente en una cláusula privada.

```cpp
#pragma omp parallel for
    for (i=1; i<n; i++)
        b[i] = (a[i] + a[i-1]) / 2.0;
```

## <a name="a2-conditional-compilation"></a>Compilación condicional A.2

Los siguientes ejemplos ilustran el uso de la compilación condicional mediante la macro OpenMP [_OPENMP](2-directives.md#22-conditional-compilation). Con la compilación de OpenMP, el `_OPENMP` macro queda definida.

```cpp
# ifdef _OPENMP
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

El operador de preprocesador definido permite más de una macro que probarse en una sola directiva.

```cpp
# if defined(_OPENMP) && defined(VERBOSE)
    printf_s("Compiled by an OpenMP-compliant implementation.\n");
# endif
```

## <a name="a3-parallel-regions"></a>A.3 regiones en paralelo

El [paralelo](2-directives.md#23-parallel-construct) directiva puede usarse en programas paralelos más generales. En el ejemplo siguiente, cada subproceso de la región paralela decide qué parte de la matriz global `x` que trabajar, en función del número de subprocesos:

```cpp
#pragma omp parallel shared(x, npoints) private(iam, np, ipoints)
{
    iam = omp_get_thread_num();
    np =  omp_get_num_threads();
    ipoints = npoints / np;
    subdomain(x, iam, ipoints);
}
```

## <a name="a4-the-nowait-clause"></a>A.4 la cláusula nowait

Si hay muchos bucles independientes dentro de una región paralela, puede usar el [nowait](2-directives.md#241-for-construct) cláusula para evitar la barrera implícita al final de la `for` directiva, como se indica a continuación:

```cpp
#pragma omp parallel
{
    #pragma omp for nowait
        for (i=1; i<n; i++)
             b[i] = (a[i] + a[i-1]) / 2.0;
    #pragma omp for nowait
        for (i=0; i<m; i++)
            y[i] = sqrt(z[i]);
}
```

## <a name="a5-the-critical-directive"></a>A.5 la directiva critical

En el ejemplo siguiente se incluyen varios [críticos](2-directives.md#262-critical-construct) directivas. El ejemplo muestra un modelo de puesta en cola en el que se quita de la cola y trabajó en una tarea. Para protegerse contra muchos subprocesos de cola de la misma tarea, la operación de eliminación de cola debe estar en un `critical` sección. Dado que las dos colas en este ejemplo son independientes, que están protegidos por `critical` directivas con nombres diferentes, *valor* y *eje y*.

```cpp
#pragma omp parallel shared(x, y) private(x_next, y_next)
{
    #pragma omp critical ( xaxis )
        x_next = dequeue(x);
    work(x_next);
    #pragma omp critical ( yaxis )
        y_next = dequeue(y);
    work(y_next);
}
```

## <a name="a6-the-lastprivate-clause"></a>A.6 la cláusula lastprivate

A veces, la ejecución correcta depende del valor que la última iteración de un bucle que se asigna a una variable. Estos programas deben enumerar todas las variables como argumentos a un [lastprivate](2-directives.md#2723-lastprivate) cláusula para que los valores de las variables son el mismo que cuando se ejecuta el bucle secuencial.

```cpp
#pragma omp parallel
{
   #pragma omp for lastprivate(i)
      for (i=0; i<n-1; i++)
         a[i] = b[i] + b[i+1];
}
a[i]=b[i];
```

En el ejemplo anterior, el valor de `i` será igual al final de la región paralela `n-1`, como en el caso secuencial.

## <a name="a7-the-reduction-clause"></a>A.7 la cláusula reduction

En el ejemplo siguiente se muestra el [reducción](2-directives.md#2726-reduction) cláusula:

```cpp
#pragma omp parallel for private(i) shared(x, y, n) \
                         reduction(+: a, b)
    for (i=0; i<n; i++) {
        a = a + x[i];
        b = b + y[i];
    }
```

## <a name="a8-parallel-sections"></a>A.8 de secciones paralelas

En el ejemplo siguiente (para [sección 2.4.2](2-directives.md#242-sections-construct)), las funciones *valor*, *eje y*, y *zaxis* se puede ejecutar simultáneamente. La primera `section` directiva es opcional.  Todos los `section` directivas deben aparecer en la extensión de léxico el `parallel sections` construir.

```cpp
#pragma omp parallel sections
{
    #pragma omp section
        xaxis();
    #pragma omp section
        yaxis();
    #pragma omp section
        zaxis();
}
```

## <a name="a9-single-directives"></a>A.9 directivas Single

En el ejemplo siguiente se muestra el [único](2-directives.md#243-single-construct) directiva. En el ejemplo, un solo subproceso (normalmente, el primer subproceso que se encuentra el `single` directiva) imprime el mensaje de progreso. El usuario no debe hacer ninguna suposición como a qué subproceso ejecutará el `single` sección. Todos los demás subprocesos se omitirá la `single` sección y detenerse en la barrera al final de la `single` construir. Si otros subprocesos puedan continuar sin esperar el subproceso que ejecuta el `single` sección, un `nowait` cláusula se puede especificar en el `single` directiva.

```cpp
#pragma omp parallel
{
    #pragma omp single
        printf_s("Beginning work1.\n");
    work1();
    #pragma omp single
        printf_s("Finishing work1.\n");
    #pragma omp single nowait
        printf_s("Finished work1 and beginning work2.\n");
    work2();
}
```

## <a name="a10-sequential-ordering"></a>A.10 un orden secuencial

[Ordenada secciones](2-directives.md#266-ordered-construct) son útiles para ordenar la salida de trabajo que se realiza en paralelo de secuencialmente. El siguiente programa imprime los índices en orden secuencial:

```cpp
#pragma omp for ordered schedule(dynamic)
    for (i=lb; i<ub; i+=st)
        work(i);
void work(int k)
{
    #pragma omp ordered
        printf_s(" %d", k);
}
```

## <a name="a11-a-fixed-number-of-threads"></a>A.11 un número fijo de subprocesos

Algunos programas confían en un número fijo, especificado previamente de subprocesos se ejecute correctamente.  Dado que la configuración predeterminada para el ajuste dinámico del número de subprocesos es definido por la implementación, estos programas pueden elegir desactivar la capacidad de subprocesos dinámica y establezca el número de subprocesos explícitamente para mantener la portabilidad. El ejemplo siguiente muestra cómo hacer esto con [omp_set_dynamic ()](3-run-time-library-functions.md#317-omp_set_dynamic-function), y [omp_set_num_threads ()](3-run-time-library-functions.md#311-omp_set_num_threads-function):

```cpp
omp_set_dynamic(0);
omp_set_num_threads(16);
#pragma omp parallel shared(x, npoints) private(iam, ipoints)
{
    if (omp_get_num_threads() != 16)
      abort();
    iam = omp_get_thread_num();
    ipoints = npoints/16;
    do_by_16(x, iam, ipoints);
}
```

En este ejemplo, el programa se ejecutará correctamente solo si se ejecuta por 16 subprocesos. Si la implementación no es capaz de admitir 16 subprocesos, el comportamiento de este ejemplo es definido por la implementación.

El número de subprocesos que se ejecutan en una región paralela se mantiene constante durante una región paralela, independientemente de los subprocesos dinámicos de configuración. El mecanismo de subprocesos dinámica determina el número de subprocesos que se utilizarán al principio de la región paralela y mantiene constante para la duración de la región.

## <a name="a12-the-atomic-directive"></a>A.12 la directiva atomic

En el ejemplo siguiente, se evita las condiciones de carrera (actualizaciones simultáneas de un elemento de *x* por muchos subprocesos) mediante el uso de la [atómica](2-directives.md#264-atomic-construct) directiva:

```cpp
#pragma omp parallel for shared(x, y, index, n)
    for (i=0; i<n; i++)
    {
        #pragma omp atomic
            x[index[i]] += work1(i);
        y[i] += work2(i);
    }
```

La ventaja de usar el `atomic` directiva en este ejemplo es que permite que las actualizaciones de dos elementos diferentes de x que se produzcan en paralelo. Si un [críticos](2-directives.md#262-critical-construct) directiva se usa en su lugar, todas las actualizaciones a los elementos de *x* se ejecutan en serie (aunque no en cualquier garantiza el orden).

El `atomic` directiva se aplica solo a la instrucción de C o C++ le sigue.  Como resultado, los elementos de *y* no se actualizan de forma atómica en este ejemplo.

## <a name="a13-a-flush-directive-with-a-list"></a>A.13 A la directiva flush con una lista

En el ejemplo siguiente se usa el `flush` la directiva para la sincronización de punto a punto de determinados objetos entre los pares de subprocesos:

```cpp
int   sync[NUMBER_OF_THREADS];
float work[NUMBER_OF_THREADS];
#pragma omp parallel private(iam,neighbor) shared(work,sync)
{
    iam = omp_get_thread_num();
    sync[iam] = 0;
    #pragma omp barrier

    // Do computation into my portion of work array
    work[iam] = ...;

    //  Announce that I am done with my work
    // The first flush ensures that my work is
    // made visible before sync.
    // The second flush ensures that sync is made visible.
    #pragma omp flush(work)
    sync[iam] = 1;
    #pragma omp flush(sync)

    // Wait for neighbor
    neighbor = (iam>0 ? iam : omp_get_num_threads()) - 1;
    while (sync[neighbor]==0)
    {
        #pragma omp flush(sync)
    }

    // Read neighbor's values of work array
    ... = work[neighbor];
}
```

## <a name="a14-a-flush-directive-without-a-list"></a>A.14 A la directiva flush sin una lista

El ejemplo siguiente (para [sección 2.6.5](2-directives.md#265-flush-directive)) distingue los objetos compartidos afectados por un `flush` la directiva con ninguna lista de los objetos compartidos que no se ven afectados:

```cpp
// omp_flush_without_list.c
#include <omp.h>

int x, *p = &x;

void f1(int *q)
{
    *q = 1;
    #pragma omp flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

void f2(int *q)
{
    #pragma omp barrier
    *q = 2;

    #pragma omp barrier
    // a barrier implies a flush
    // x, p, and *q are flushed
    //   because they are shared and accessible
    // q is not flushed because it is not shared.
}

int g(int n)
{
    int i = 1, j, sum = 0;
    *p = 1;

    #pragma omp parallel reduction(+: sum) num_threads(10)
    {
        f1(&j);
        // i, n and sum were not flushed
        //   because they were not accessible in f1
        // j was flushed because it was accessible
        sum += j;
        f2(&j);
        // i, n, and sum were not flushed
        //   because they were not accessible in f2
        // j was flushed because it was accessible
        sum += i + j + *p + n;
    }
    return sum;
}

int main()
{
}
```

## <a name="a15-the-number-of-threads-used"></a>A.15 el número de subprocesos usados

Considere el siguiente ejemplo incorrecto (para [sección 3.1.2](3-run-time-library-functions.md#312-omp_get_num_threads-function)):

```cpp
np = omp_get_num_threads(); // misplaced
#pragma omp parallel for schedule(static)
    for (i=0; i<np; i++)
        work(i);
```

El `omp_get_num_threads()` llamada devuelve 1 en la sección de serie del código, por lo que *np* siempre será igual a 1 en el ejemplo anterior. Para determinar el número de subprocesos que se implementarán para la región paralela, debe ser la llamada dentro de la región paralela.

El ejemplo siguiente muestra cómo volver a escribir este programa sin necesidad de incluir una consulta para el número de subprocesos:

```cpp
#pragma omp parallel private(i)
{
    i = omp_get_thread_num();
    work(i);
}
```

## <a name="a16-locks"></a>A.16 bloqueos

En el ejemplo siguiente (para [sección 3.2](3-run-time-library-functions.md#32-lock-functions)), el argumento a las funciones de bloqueo debe tener tipo `omp_lock_t`, y que no hay ninguna necesidad de vaciarlo.  Las funciones de bloqueo, hacer que los subprocesos estén inactivos mientras espera de entrada a la primera sección crítica, pero realice otro trabajo mientras se espera para que la segunda entrada.  El `omp_set_lock` bloques de función, pero la `omp_test_lock` no la función, lo que permite el trabajo en `skip()` realizarse.

```cpp
// omp_using_locks.c
// compile with: /openmp /c
#include <stdio.h>
#include <omp.h>

void work(int);
void skip(int);

int main() {
   omp_lock_t lck;
   int id;

   omp_init_lock(&lck);
   #pragma omp parallel shared(lck) private(id)
   {
      id = omp_get_thread_num();

      omp_set_lock(&lck);
      printf_s("My thread id is %d.\n", id);

      // only one thread at a time can execute this printf
      omp_unset_lock(&lck);

      while (! omp_test_lock(&lck)) {
         skip(id);   // we do not yet have the lock,
                     // so we must do something else
      }
      work(id);     // we now have the lock
                    // and can do the work
      omp_unset_lock(&lck);
   }
   omp_destroy_lock(&lck);
}
```

## <a name="a17-nestable-locks"></a>A.17 los bloqueos Anidables

El ejemplo siguiente (para [sección 3.2](3-run-time-library-functions.md#32-lock-functions)) muestra cómo se puede utilizar un bloqueo anidable para sincronizar las actualizaciones a una estructura completa tanto a uno de sus miembros.

```cpp
#include <omp.h>
typedef struct {int a,b; omp_nest_lock_t lck;} pair;

void incr_a(pair *p, int a)
{
    // Called only from incr_pair, no need to lock.
    p->a += a;
}

void incr_b(pair *p, int b)
{
    // Called both from incr_pair and elsewhere,
    // so need a nestable lock.

    omp_set_nest_lock(&p->lck);
    p->b += b;
    omp_unset_nest_lock(&p->lck);
}

void incr_pair(pair *p, int a, int b)
{
    omp_set_nest_lock(&p->lck);
    incr_a(p, a);
    incr_b(p, b);
    omp_unset_nest_lock(&p->lck);
}

void f(pair *p)
{
    extern int work1(), work2(), work3();
    #pragma omp parallel sections
    {
        #pragma omp section
            incr_pair(p, work1(), work2());
        #pragma omp section
            incr_b(p, work3());
    }
}
```

## <a name="a18-nested-for-directives"></a>Nested A.18 directivas for

El siguiente ejemplo de `for` [anidamiento de directivas](2-directives.md#29-directive-nesting) es compatible con porque el interior y exterior `for` directivas enlazar a diferentes regiones en paralelo:

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
        {
            #pragma omp parallel shared(i, n)
            {
                #pragma omp for
                    for (j=0; j<n; j++)
                        work(i, j);
            }
        }
}
```

Una variación siguiente del ejemplo anterior también es compatible con:

```cpp
#pragma omp parallel default(shared)
{
    #pragma omp for
        for (i=0; i<n; i++)
            work1(i, n);
}

void work1(int i, int n)
{
    int j;
    #pragma omp parallel default(shared)
    {
        #pragma omp for
            for (j=0; j<n; j++)
                work2(i, j);
    }
    return;
}
```

## <a name="a19-examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 ejemplos donde se muestra un anidamiento incorrecto de uso compartido directivas

Los ejemplos de esta sección muestran el [anidamiento de directivas](2-directives.md#29-directive-nesting) reglas.

El ejemplo siguiente no es conforme porque interno y externo `for` directivas anidadas y enlazar a la misma `parallel` directiva:

```cpp
void wrong1(int n)
{
  #pragma omp parallel default(shared)
  {
      int i, j;
      #pragma omp for
      for (i=0; i<n; i++) {
          #pragma omp for
              for (j=0; j<n; j++)
                 work(i, j);
     }
   }
}
```

La siguiente versión de forma dinámica anidada del ejemplo anterior también será no compatible:

```cpp
void wrong2(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++)
        work1(i, n);
  }
}

void work1(int i, int n)
{
  int j;
  #pragma omp for
    for (j=0; j<n; j++)
      work2(i, j);
}
```

El ejemplo siguiente no es compatible porque la `for` y `single` las directivas se pueden anidar y se enlazan a la misma región paralela:

```cpp
void wrong3(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        #pragma omp single
          work(i);
      }
  }
}
```

El ejemplo siguiente no es conforme porque un `barrier` directiva dentro de un `for` puede producir un interbloqueo:

```cpp
void wrong4(int n)
{
  #pragma omp parallel default(shared)
  {
    int i;
    #pragma omp for
      for (i=0; i<n; i++) {
        work1(i);
        #pragma omp barrier
        work2(i);
      }
  }
}
```

El ejemplo siguiente no es compatible porque la `barrier` da como resultado un interbloqueo debido al hecho de que sólo un subproceso a la vez puede entrar en la sección crítica:

```cpp
void wrong5()
{
  #pragma omp parallel
  {
    #pragma omp critical
    {
       work1();
       #pragma omp barrier
       work2();
    }
  }
}
```

El ejemplo siguiente no es compatible porque la `barrier` da como resultado un interbloqueo debido al hecho de que sólo un subproceso ejecuta el `single` sección:

```cpp
void wrong6()
{
  #pragma omp parallel
  {
    setup();
    #pragma omp single
    {
      work1();
      #pragma omp barrier
      work2();
    }
    finish();
  }
}
```

## <a name="a20-bind-barrier-directives"></a>Directivas A.20 enlace barrier

El enlace de la directiva de reglas de llamada para un `barrier` directiva para enlazar con la envolvente más cercana `parallel` directiva. Para obtener más información sobre el enlace de directivas, consulte [sección 2.8](2-directives.md#28-directive-binding).

En el ejemplo siguiente, la llamada de *principal* a *sub2* es compatible porque la `barrier` (en *sub3*) se enlaza a la región paralela en *sub2* . La llamada de *principal* a *sub1* es compatible porque la `barrier` enlaza a la región paralela en la subrutina *sub2*.  La llamada de *principal* a *sub3* es compatible porque el `barrier` no se enlaza a cualquier región paralela y se omite. Además, el `barrier` sólo sincroniza de subprocesos en la región paralela envolvente y no todos los subprocesos creados en el equipo de *sub1*.

```cpp
int main()
{
    sub1(2);
    sub2(2);
    sub3(2);
}

void sub1(int n)
{
    int i;
    #pragma omp parallel private(i) shared(n)
    {
        #pragma omp for
        for (i=0; i<n; i++)
            sub2(i);
    }
}

void sub2(int k)
{
     #pragma omp parallel shared(k)
     sub3(k);
}

void sub3(int n)
{
    work(n);
    #pragma omp barrier
    work(n);
}
```

## <a name="a21-scope-variables-with-the-private-clause"></a>A.21 variables de ámbito con la cláusula private

Los valores de `i` y `j` en el ejemplo siguiente no está definida en la salida de la región paralela:

```cpp
int i, j;
i = 1;
j = 2;
#pragma omp parallel private(i) firstprivate(j)
{
  i = 3;
  j = j + 2;
}
printf_s("%d %d\n", i, j);
```

Para obtener más información sobre la `private` cláusula, vea [sección 2.7.2.1](2-directives.md#2721-private).

## <a name="a22-the-defaultnone-clause"></a>A.22 la cláusula default (None)

El ejemplo siguiente distingue las variables que se ven afectadas por la `default(none)` cláusula desde las variables que no son:

```cpp
// openmp_using_clausedefault.c
// compile with: /openmp
#include <stdio.h>
#include <omp.h>

int x, y, z[1000];
#pragma omp threadprivate(x)

void fun(int a) {
   const int c = 1;
   int i = 0;

   #pragma omp parallel default(none) private(a) shared(z)
   {
      int j = omp_get_num_thread();
             //O.K.  - j is declared within parallel region
      a = z[j];       // O.K.  - a is listed in private clause
                      //      - z is listed in shared clause
      x = c;          // O.K.  - x is threadprivate
                      //      - c has const-qualified type
      z[i] = y;       // C3052 error - cannot reference i or y here

      #pragma omp for firstprivate(y)
         for (i=0; i<10 ; i++) {
            z[i] = y;  // O.K. - i is the loop control variable
                       // - y is listed in firstprivate clause
          }
       z[i] = y;   // Error - cannot reference i or y here
   }
}
```

Para obtener más información sobre la `default` cláusula, vea [sección 2.7.2.5](2-directives.md#2725-default).

## <a name="a23-examples-of-the-ordered-directive"></a>A.23 ejemplos de la directiva ordered

Es posible tener varias secciones ordenadas con una `for` especificado con el `ordered` cláusula. El primer ejemplo no es conforme debido a la API especifica la siguiente regla:

"Una iteración de un bucle con un `for` construcción no debe ejecutar el mismo `ordered` la directiva más de una vez y no deben ejecutar más de un `ordered` directiva." (Consulte [sección 2.6.6](2-directives.md#266-ordered-construct).)

En este ejemplo no compatible, todas las iteraciones ejecutan dos secciones ordenadas:

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    #pragma omp ordered
    { ... }
    ...
    #pragma omp ordered
    { ... }
    ...
}
```

Muestra el siguiente ejemplo conforme un `for` con más de una sección ordenada:

```cpp
#pragma omp for ordered
for (i=0; i<n; i++)
{
    ...
    if (i <= 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
    (i > 10)
    {
        ...
        #pragma omp ordered
        { ... }
    }
    ...
}
```

## <a name="a24-example-of-the-private-clause"></a>A.24 ejemplo de la cláusula private

El [privada](2-directives.md#2721-private) cláusula de una región paralela sólo tiene efecto en el ámbito léxico de la región, pero no para la extensión dinámica de la región.  Por lo tanto, en el ejemplo siguiente, todos los usos de la variable *un* dentro de la `for` bucle en la rutina *f* hace referencia a una copia privada de *un*, mientras que un uso en rutina *g* hace referencia a la plantilla global *un*.

```cpp
int a;

void f(int n)
{
    a = 0;

    #pragma omp parallel for private(a)
    for (int i=1; i<n; i++)
    {
        a = i;
        g(i, n);
        d(a);     // Private copy of "a"
        ...
    }
    ...

void g(int k, int n)
{
    h(k,a); // The global "a", not the private "a" in f
}
```

## <a name="a25-examples-of-the-copyprivate-data-attribute-clause"></a>A.25 ejemplos de la cláusula de atributos de datos copyprivate

**Ejemplo 1:** El [copyprivate](2-directives.md#2728-copyprivate) cláusula puede usarse para difundir valores adquiridos por un único subproceso directamente a todas las instancias de las variables privadas de los demás subprocesos.

```cpp
float x, y;
#pragma omp threadprivate(x, y)

void init( )
{
    float a;
    float b;

    #pragma omp single copyprivate(a,b,x,y)
    {
        get_values(a,b,x,y);
    }

    use_values(a, b, x, y);
}
```

Si la rutina *init* se llama desde una región de la serie, no se ve afectado por la presencia de las directivas de su comportamiento. Después de llamar a la *get_values* rutina se ha ejecutado por un subproceso, no hay ningún subproceso deja la construcción hasta que los objetos privados designados por *un*, *b*, *x*, y *y* en todos los subprocesos se convierten en ha definido con los valores leídos.

**Ejemplo 2:** A diferencia del ejemplo anterior, suponga que un subproceso determinado, por ejemplo el subproceso principal debe realizar la operación de lectura. En este caso, el `copyprivate` cláusula no puede utilizarse para realizar la difusión directamente, pero se puede usar para proporcionar acceso a un objeto temporal compartido.

```cpp
float read_next( )
{
    float * tmp;
    float return_val;

    #pragma omp single copyprivate(tmp)
    {
        tmp = (float *) malloc(sizeof(float));
    }

    #pragma omp master
    {
        get_float( tmp );
    }

    #pragma omp barrier
    return_val = *tmp;
    #pragma omp barrier

    #pragma omp single
    {
       free(tmp);
    }

    return return_val;
}
```

**Ejemplo 3:** Suponga que el número de objetos de bloqueo necesarios dentro de una región paralela no puede determinarse fácilmente antes de especificarlo. El `copyprivate` cláusula puede usarse para proporcionar acceso a objetos de bloqueo compartido que se asignan dentro de esa región paralela.

```cpp
#include <omp.h>

omp_lock_t *new_lock()
{
    omp_lock_t *lock_ptr;

    #pragma omp single copyprivate(lock_ptr)
    {
        lock_ptr = (omp_lock_t *) malloc(sizeof(omp_lock_t));
        omp_init_lock( lock_ptr );
    }

    return lock_ptr;
}
```

## <a name="a26-the-threadprivate-directive"></a>A.26 la directiva threadprivate

Los ejemplos siguientes muestran cómo usar el [threadprivate](2-directives.md#271-threadprivate-directive) directiva asignarle a cada subproceso un contador independiente.

### <a name="example-1"></a>Ejemplo 1

```cpp
int counter = 0;
#pragma omp threadprivate(counter)

int sub()
{
    counter++;
    return(counter);
}
```

### <a name="example-2"></a>Ejemplo 2

```cpp
int sub()
{
    static int counter = 0;
    #pragma omp threadprivate(counter)
    counter++;
    return(counter);
}
```

## <a name="a27-c99-variable-length-arrays"></a>Matrices de longitud variable C99 A.27

En el ejemplo siguiente se muestra cómo usar matrices de longitud Variable C99 (VLA) en un [firstprivate](2-directives.md#2722-firstprivate) directiva.

> [!NOTE]
> Matrices de longitud variable no se admiten en Visual C++.

```cpp
void f(int m, int C[m][m])
{
    double v1[m];
    ...
    #pragma omp parallel firstprivate(C, v1)
    ...
}
```

## <a name="a28-the-numthreads-clause"></a>A.28 la cláusula num_threads

En el ejemplo siguiente se muestra el [num_threads](2-directives.md#23-parallel-construct) cláusula. La región paralela se ejecuta con un máximo de 10 subprocesos.

```cpp
#include <omp.h>
main()
{
    omp_set_dynamic(1);
    ...
    #pragma omp parallel num_threads(10)
    {
        ... parallel region ...
    }
}
```

## <a name="a29-work-sharing-constructs-inside-a-critical-construct"></a>A.29 construcciones de uso compartido en una construcción critical

El ejemplo siguiente se muestra cómo utilizar una construcción de uso compartido dentro de un `critical` construir. En este ejemplo es compatible porque el uso compartido de construir y `critical` construcción no se enlaza a la misma región paralela.

```cpp
void f()
{
  int i = 1;
  #pragma omp parallel sections
  {
    #pragma omp section
    {
      #pragma omp critical (name)
      {
        #pragma omp parallel
        {
          #pragma omp single
          {
            i++;
          }
        }
      }
    }
  }
}
```

## <a name="a30-reprivatization"></a>Reprivatización A.30

El ejemplo siguiente muestra el reprivatización de variables. Se pueden marcar variables privadas `private` nuevo en una directiva anidada. No es necesario compartir esas variables en la región paralela envolvente.

```cpp
int i, a;
...
#pragma omp parallel private(a)
{
  ...
  #pragma omp parallel for private(a)
  for (i=0; i<10; i++)
     {
       ...
     }
}
```

## <a name="a31-thread-safe-lock-functions"></a>A.31 funciones de bloqueo de subprocesos

En el ejemplo de C++ siguiente se muestra cómo inicializar una matriz de bloqueos en una región paralela mediante [omp_init_lock](3-run-time-library-functions.md#321-omp_init_lock-and-omp_init_nest_lock-functions).

```cpp
// A_13_omp_init_lock.cpp
// compile with: /openmp
#include <omp.h>

omp_lock_t *new_locks() {
   int i;
   omp_lock_t *lock = new omp_lock_t[1000];
   #pragma omp parallel for private(i)
   for (i = 0 ; i < 1000 ; i++)
      omp_init_lock(&lock[i]);

   return lock;
}

int main () {}
```
