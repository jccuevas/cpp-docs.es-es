---
title: 2. Directivas
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882874"
---
# <a name="2-directives"></a>2. Directivas

Las directivas se basan en las directivas de `#pragma` definidas en C++ los estándares C y.  Los compiladores que admiten la API C++ y C de OpenMP incluirán una opción de línea de comandos que active y permita la interpretación de todas las directivas de compilador de OpenMP.

## <a name="21-directive-format"></a>formato de directiva 2,1

La sintaxis de una directiva de OpenMP se especifica formalmente con la gramática en el [Apéndice C](c-openmp-c-and-cpp-grammar.md)y, de manera informativa, de la manera siguiente:

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Cada directiva comienza con `#pragma omp`, para reducir la posibilidad de que se produzca un conflicto con otras directivas pragma (no de OpenMP o extensiones de proveedor a OpenMP) con los mismos nombres. El resto de la Directiva sigue las convenciones de los estándares C C++ y para las directivas de compilador. En concreto, se puede usar el espacio en blanco antes y después del `#`y, en ocasiones, se debe usar el espacio en blanco para separar las palabras de una directiva. Los tokens de preprocesamiento que siguen a los `#pragma omp` están sujetos a sustitución de macros.

Las directivas distinguen mayúsculas de minúsculas. El orden en que aparecen las cláusulas en las directivas no es significativo. Las cláusulas de las directivas se pueden repetir según sea necesario, en función de las restricciones que se indican en la descripción de cada cláusula. Si *variable-List* aparece en una cláusula, debe especificar solo variables. Solo se puede especificar un *nombre de directiva* por directiva.  Por ejemplo, no se permite la siguiente directiva:

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Una directiva de OpenMP se aplica a como máximo una instrucción correcta, que debe ser un bloque estructurado.

## <a name="22-conditional-compilation"></a>2,2 compilación condicional

El nombre de la macro `_OPENMP` se define mediante implementaciones compatibles con OpenMP como la constante decimal *YYYYMM*, que será el año y el mes de la especificación aprobada. Esta macro no debe ser el asunto de una `#define` o de una directiva de preprocesamiento `#undef`.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si los proveedores definen las extensiones de OpenMP, pueden especificar macros predefinidas adicionales.

## <a name="23-parallel-construct"></a>2,3 construcción paralela

La siguiente Directiva define una región paralela, que es una región del programa que va a ser ejecutada por muchos subprocesos en paralelo. Esta directiva es la construcción fundamental que comienza la ejecución en paralelo.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

La *cláusula* es una de las siguientes:

- `if(` `)` *de expresión escalar*
- `private(` `)` *de lista variable*
- `firstprivate(` `)` *de lista variable*
- `default(shared | none)`
- `shared(` `)` *de lista variable*
- `copyin(` `)` *de lista variable*
- `reduction(` *operador* `:`*lista de variables* `)`
- `num_threads(` *Integer-expression* `)`

Cuando un subproceso llega a una construcción paralela, se crea un equipo de subprocesos si se cumple uno de los siguientes casos:

- No existe ninguna cláusula de `if`.
- La expresión `if` se evalúa como un valor distinto de cero.

Este subproceso se convierte en el subproceso principal del equipo, con un número de subprocesos de 0, y todos los subprocesos del equipo, incluido el subproceso principal, ejecutan la región en paralelo. Si el valor de la expresión `if` es cero, la región se serializa.

Para determinar el número de subprocesos solicitados, se tendrán en cuenta las siguientes reglas en orden. Se aplicará la primera regla cuya condición se cumpla:

1. Si la cláusula `num_threads` está presente, el valor de la expresión de tipo entero es el número de subprocesos solicitados.

1. Si se ha llamado a la función de biblioteca `omp_set_num_threads`, el valor del argumento en la llamada ejecutada más recientemente es el número de subprocesos solicitados.

1. Si se define la variable de entorno `OMP_NUM_THREADS`, el valor de esta variable de entorno es el número de subprocesos solicitados.

1. Si no se usa ninguno de los métodos anteriores, el número de subprocesos solicitados está definido por la implementación.

Si la cláusula `num_threads` está presente, reemplaza el número de subprocesos solicitados por la función de biblioteca de `omp_set_num_threads` o la variable de entorno `OMP_NUM_THREADS` solo para la región paralela a la que se aplica. Las regiones paralelas posteriores no se ven afectadas por esta.

El número de subprocesos que ejecutan la región paralela depende también de si está habilitado el ajuste dinámico del número de subprocesos. Si el ajuste dinámico está deshabilitado, el número solicitado de subprocesos ejecutará la región paralela. Si el ajuste dinámico está habilitado, el número de subprocesos solicitados es el número máximo de subprocesos que pueden ejecutar la región paralela.

Si se encuentra una región paralela mientras se deshabilita el ajuste dinámico del número de subprocesos y el número de subprocesos solicitados para la región paralela es mayor que el número que el sistema en tiempo de ejecución puede proporcionar, el comportamiento del programa es definido por la implementación. Una implementación puede, por ejemplo, interrumpir la ejecución del programa o puede serializar la región paralela.

La función de biblioteca `omp_set_dynamic` y la variable de entorno `OMP_DYNAMIC` se pueden usar para habilitar y deshabilitar el ajuste dinámico del número de subprocesos.

El número de procesadores físicos que hospedan realmente los subprocesos en un momento dado está definido por la implementación. Una vez creado, el número de subprocesos del equipo permanece constante mientras dure la región paralela. Puede cambiarse explícitamente por el usuario o automáticamente por el sistema en tiempo de ejecución desde una región paralela a otra.

Cada subproceso ejecuta las instrucciones contenidas en la extensión dinámica de la región paralela, y cada subproceso puede ejecutar una ruta de instrucciones que es diferente de los demás subprocesos. Las directivas que se encuentran fuera de la extensión léxica de una región paralela se conocen como directivas huérfanas.

Existe una barrera implícita al final de una región paralela. Solo el subproceso maestro del equipo continúa la ejecución al final de una región paralela.

Si un subproceso de un equipo que ejecuta una región paralela encuentra otra construcción paralela, crea un nuevo equipo y se convierte en el maestro del nuevo equipo. Las regiones paralelas anidadas se serializan de forma predeterminada. Como resultado, de forma predeterminada, una región paralela anidada se ejecuta en un equipo compuesto por un subproceso. El comportamiento predeterminado se puede cambiar mediante la función de biblioteca en tiempo de ejecución `omp_set_nested` o la variable de entorno `OMP_NESTED`. Sin embargo, el número de subprocesos de un equipo que ejecutan una región paralela anidada está definido por la implementación.

Las restricciones de la Directiva de `parallel` son las siguientes:

- Como máximo, puede aparecer una cláusula `if` en la Directiva.

- No se especifica si se producen efectos secundarios dentro de las expresiones if o `num_threads`.

- Una `throw` ejecuta dentro de una región paralela debe hacer que la ejecución se reanude dentro de la extensión dinámica del mismo bloque estructurado y debe ser detectada por el mismo subproceso que produjo la excepción.

- Solo puede aparecer una sola cláusula `num_threads` en la Directiva. La expresión `num_threads` se evalúa fuera del contexto de la región paralela y debe evaluarse como un valor entero positivo.

- El orden de evaluación de las cláusulas `if` y `num_threads` no está especificado.

### <a name="cross-references"></a>Referencias cruzadas

- cláusulas `private`, `firstprivate`, `default`, `shared`, `copyin`y `reduction` ([sección 2.7.2](#272-data-sharing-attribute-clauses))
- Variable de entorno [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) función de biblioteca
- Variable de entorno [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)
- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) función)
- Variable de entorno [OMP_NESTED](4-environment-variables.md#44-omp_nested)
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) función de biblioteca

## <a name="24-work-sharing-constructs"></a>2,4 construcciones de uso compartido de trabajo

Una construcción de uso compartido de trabajo distribuye la ejecución de la instrucción asociada entre los miembros del equipo que la encuentran. Las directivas de uso compartido de trabajo no inician nuevos subprocesos y no hay ninguna barrera implícita en la entrada a una construcción de uso compartido de trabajo.

La secuencia de construcciones de uso compartido de trabajo y las directivas de `barrier` encontradas deben ser las mismas para todos los subprocesos de un equipo.

OpenMP define las siguientes construcciones de uso compartido de trabajo y estas construcciones se describen en las secciones siguientes:

- [for](#241-for-construct) (Directiva)
- [Sections](#242-sections-construct) (Directiva)
- directiva [única](#243-single-construct)

### <a name="241-for-construct"></a>2.4.1 for (construcción)

La Directiva `for` identifica una construcción iterativa de uso compartido de trabajo que especifica que las iteraciones del bucle asociado se ejecutarán en paralelo. Las iteraciones del bucle `for` se distribuyen entre los subprocesos que ya existen en el equipo que ejecuta la construcción paralela a la que se enlaza. La sintaxis de la construcción `for` es la siguiente:

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

La cláusula es una de las siguientes:

- `private(` `)` *de lista variable*
- `firstprivate(` `)` *de lista variable*
- `lastprivate(` `)` *de lista variable*
- `reduction(` *operador* `:` *lista de variables* `)`
- `ordered`
- `schedule(` *clase* [`,` *chunk_size*] `)`
- `nowait`

La Directiva `for` coloca restricciones en la estructura del bucle de `for` correspondiente. En concreto, el bucle de `for` correspondiente debe tener una forma canónica:

`for (` *init-expr* `;` *var Logical-OP b* `;` *incr-expr* `)`

*init-expr*<br/>
Uno de los siguientes:

- *var* = *lb*
- *variable de tipo entero:*  = *lb*

*incr-expr*<br/>
Uno de los siguientes:

- `++` *var*
- `++` *var*
- `--` *var*
- `--` *var*
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
Variable de entero con signo. Si, de lo contrario, esta variable sería compartida, es privada implícitamente mientras dure el `for`. No modifique esta variable en el cuerpo de la instrucción `for`. A menos que se especifique la variable `lastprivate`, su valor después del bucle es indeterminado.

*operación lógica*<br/>
Uno de los siguientes:

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b*y *incr*<br>
Expresiones de entero invariable de bucle. No hay ninguna sincronización durante la evaluación de estas expresiones, por lo que los efectos secundarios evaluados producen resultados indeterminados.

La forma canónica permite calcular el número de iteraciones de bucle en la entrada al bucle. Este cálculo se realiza con valores en el tipo de *var*, después de promociones enteras. En concreto, si el valor de *b* `-` *lb* `+` *incr* no se puede representar en ese tipo, el resultado es indeterminado. Además, si *la operación lógica* está `<` o `<=`, *incr-expr* debe hacer que *var* aumente en cada iteración del bucle.   Si *Logical-OP* es `>` o `>=`, *incr-expr* debe hacer que *var* se reduzca en cada iteración del bucle.

La cláusula `schedule` especifica cómo se dividen las iteraciones del bucle de `for` entre los subprocesos del equipo. La corrección de un programa no debe depender del subproceso que ejecuta una iteración concreta. El valor de *chunk_size*, si se especifica, debe ser una expresión de tipo entero invariable de bucle con un valor positivo. No hay ninguna sincronización durante la evaluación de esta expresión, por lo que los efectos secundarios evaluados producen resultados indeterminados. El *tipo* de programación puede ser uno de los siguientes valores:

Tabla 2-1: valores de *tipo* de cláusula `schedule`

|||
|-|-|
|estática|Cuando se especifica `schedule(static,` *chunk_size* `)`, las iteraciones se dividen en fragmentos de un tamaño especificado por *chunk_size*. Los fragmentos se asignan estáticamente a los subprocesos del equipo en un modo Round Robin en el orden del número de subprocesos. Cuando no se especifica ningún *chunk_size* , el espacio de iteración se divide en fragmentos que tienen aproximadamente el mismo tamaño, con un fragmento asignado a cada subproceso.|
|dinámico|Cuando se especifica `schedule(dynamic,` *chunk_size* `)`, las iteraciones se dividen en una serie de fragmentos, cada uno de los cuales contiene *chunk_size* iteraciones. Cada fragmento se asigna a un subproceso que está esperando una asignación. El subproceso ejecuta el fragmento de iteraciones y, a continuación, espera a su siguiente asignación, hasta que no se conservan los fragmentos. El último fragmento que se va a asignar puede tener un número menor de iteraciones. Cuando no se especifica ningún *chunk_size* , el valor predeterminado es 1.|
|varia|Cuando se especifica `schedule(guided,` *chunk_size* `)`, las iteraciones se asignan a los subprocesos en fragmentos con tamaños decrecientes. Cuando un subproceso finaliza su fragmento de iteraciones asignado, se asigna dinámicamente a otro fragmento, hasta que no quede ninguno. En el caso de una *chunk_size* de 1, el tamaño de cada fragmento es aproximadamente el número de iteraciones sin asignar dividido por el número de subprocesos. Estos tamaños disminuyen de forma exponencial en 1. En el caso de una *chunk_size* con el valor *k* mayor que 1, los tamaños disminuyen de forma exponencial a *k*, salvo que el último fragmento puede tener menos de *k* iteraciones. Cuando no se especifica ningún *chunk_size* , el valor predeterminado es 1.|
|en tiempo de ejecución|Cuando se especifica `schedule(runtime)`, la decisión relativa a la programación se aplaza hasta el tiempo de ejecución. El *tipo* de programación y el tamaño de los fragmentos se pueden elegir en tiempo de ejecución si se establece la variable de entorno `OMP_SCHEDULE`. Si no se establece esta variable de entorno, la programación resultante está definida por la implementación. Cuando se especifica `schedule(runtime)`, no se debe especificar *chunk_size* .|

En ausencia de una cláusula `schedule` definida explícitamente, el `schedule` predeterminado está definido por la implementación.

Un programa compatible con OpenMP no debe depender de una programación determinada para la ejecución correcta. Un programa no debe basarse en un *tipo* de programación que se ajuste exactamente a la descripción indicada anteriormente, ya que es posible tener variaciones en las implementaciones de la misma *clase* de programación en diferentes compiladores. Las descripciones se pueden usar para seleccionar la programación adecuada para una situación determinada.

La cláusula `ordered` debe estar presente cuando `ordered` directivas se enlazan a la construcción `for`.

Hay una barrera implícita al final de una construcción `for` a menos que se especifique una cláusula `nowait`.

Las restricciones de la Directiva de `for` son las siguientes:

- El bucle `for` debe ser un bloque estructurado y, además, su ejecución no debe terminar con una instrucción `break`.

- Los valores de las expresiones de control de bucle del bucle `for` asociado a una directiva `for` deben ser los mismos para todos los subprocesos del equipo.

- La variable de iteración del bucle `for` debe tener un tipo entero con signo.

- En una directiva de `for` solo puede aparecer una cláusula de `schedule` única.

- En una directiva de `for` solo puede aparecer una cláusula de `ordered` única.

- En una directiva de `for` solo puede aparecer una cláusula de `nowait` única.

- No se especifica si o con qué frecuencia se producen efectos secundarios dentro de las expresiones *chunk_size*, *lb*, *b*o *incr* .

- El valor de la expresión *chunk_size* debe ser el mismo para todos los subprocesos del equipo.

#### <a name="cross-references"></a>Referencias cruzadas

- cláusulas `private`, `firstprivate`, `lastprivate`y `reduction` ([sección 2.7.2](#272-data-sharing-attribute-clauses))
- Variable de entorno [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule)
- construcción [ordenada](#266-ordered-construct)
- cláusula [Schedule](d-using-the-schedule-clause.md)

### <a name="242-sections-construct"></a>2.4.2 Sections (construcción)

La Directiva `sections` identifica una construcción de uso compartido de trabajo no iterativo que especifica un conjunto de construcciones que se van a dividir entre los subprocesos de un equipo. Cada sección se ejecuta una vez por un subproceso del equipo. La sintaxis de la Directiva `sections` es la siguiente:

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

La cláusula es una de las siguientes:

- `private(` `)` *de lista variable*
- `firstprivate(` `)` *de lista variable*
- `lastprivate(` `)` *de lista variable*
- `reduction(` *operador* `:`*lista de variables* `)`
- `nowait`

Cada sección está precedida por una directiva `section`, aunque la Directiva `section` es opcional para la primera sección. Las directivas de `section` deben aparecer dentro de la extensión léxica de la Directiva `sections`. Hay una barrera implícita al final de una construcción `sections`, a menos que se especifique un `nowait`.

Las restricciones de la Directiva de `sections` son las siguientes:

- Una directiva `section` no debe aparecer fuera de la extensión léxica de la Directiva `sections`.

- En una directiva de `sections` solo puede aparecer una cláusula de `nowait` única.

#### <a name="cross-references"></a>Referencias cruzadas

- cláusulas `private`, `firstprivate`, `lastprivate`y `reduction` ([sección 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 Single (construcción)

La Directiva `single` identifica una construcción que especifica que solo un subproceso del equipo ejecuta el bloque estructurado asociado (no necesariamente el subproceso principal). La sintaxis de la Directiva `single` es la siguiente:

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

La cláusula es una de las siguientes:

- `private(` `)` *de lista variable*
- `firstprivate(` `)` *de lista variable*
- `copyprivate(` `)` *de lista variable*
- `nowait`

Hay una barrera implícita después de la construcción `single` a menos que se especifique una cláusula `nowait`.

Las restricciones de la Directiva de `single` son las siguientes:

- En una directiva de `single` solo puede aparecer una cláusula de `nowait` única.
- La cláusula `copyprivate` no debe usarse con la cláusula `nowait`.

#### <a name="cross-references"></a>Referencias cruzadas

- cláusulas `private`, `firstprivate`y `copyprivate` ([sección 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2,5 construcciones de uso compartido paralelas combinadas

Las construcciones de uso compartido paralelas combinadas son métodos abreviados para especificar una región paralela que solo tiene una construcción de uso compartido de trabajo. La semántica de estas directivas es la misma que la especificación explícita de una directiva de `parallel` seguida de una única construcción de uso compartido de trabajo.

En las secciones siguientes se describen las construcciones de uso compartido paralelas combinadas:

- [Parallel for](#251-parallel-for-construct) (Directiva)
- Directiva de [secciones paralelas](#252-parallel-sections-construct)

### <a name="251-parallel-for-construct"></a>2.5.1 Parallel for (construcción)

La Directiva `parallel for` es un método abreviado para una región `parallel` que contiene solo una única directiva `for`. La sintaxis de la Directiva `parallel for` es la siguiente:

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Esta directiva permite todas las cláusulas de la Directiva de `parallel` y la Directiva `for`, excepto la cláusula `nowait`, con significados y límites idénticos. La semántica es la misma que si se especifica explícitamente una directiva de `parallel` seguido inmediatamente de una directiva `for`.

#### <a name="cross-references"></a>Referencias cruzadas

- [Parallel](#23-parallel-construct) (Directiva)
- [for](#241-for-construct) (Directiva)
- [Cláusulas de atributos de datos](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>construcción de secciones paralelas de 2.5.2

La Directiva `parallel sections` proporciona un formulario de acceso directo para especificar una región de `parallel` que solo tiene una única directiva de `sections`. La semántica es la misma que si se especifica explícitamente una directiva de `parallel` seguido inmediatamente de una directiva `sections`. La sintaxis de la Directiva `parallel sections` es la siguiente:

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

La *cláusula* puede ser una de las cláusulas aceptadas por las directivas `parallel` y `sections`, excepto la cláusula `nowait`.

#### <a name="cross-references"></a>Referencias cruzadas

- [Parallel](#23-parallel-construct) (Directiva)
- [Sections](#242-sections-construct) (Directiva)

## <a name="26-master-and-synchronization-directives"></a>2,6 directivas maestras y de sincronización

En las secciones siguientes se describe:

- construcción [maestra](#261-master-construct)
- construcción [crítica](#262-critical-construct)
- [barrera](#263-barrier-directive) (Directiva)
- [Atomic](#264-atomic-construct) (construcción)
- [Flush](#265-flush-directive) (Directiva)
- construcción [ordenada](#266-ordered-construct)

### <a name="261-master-construct"></a>2.6.1 (construcción maestra)

La Directiva `master` identifica una construcción que especifica un bloque estructurado ejecutado por el subproceso principal del equipo. La sintaxis de la Directiva `master` es la siguiente:

```cpp
#pragma omp master new-linestructured-block
```

Otros subprocesos del equipo no ejecutan el bloque estructurado asociado. No hay ninguna barrera implícita en la entrada o salida de la construcción maestra.

### <a name="262-critical-construct"></a>construcción crítica de 2.6.2 Critical (

La Directiva `critical` identifica una construcción que restringe la ejecución del bloque estructurado asociado a un único subproceso cada vez. La sintaxis de la Directiva `critical` es la siguiente:

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Se puede usar un *nombre* opcional para identificar la región crítica. Los identificadores que se usan para identificar una región crítica tienen vinculación externa y se encuentran en un espacio de nombres que es independiente de los espacios de nombres usados por etiquetas, etiquetas, miembros e identificadores normales.

Un subproceso espera al principio de una región crítica hasta que ningún otro subproceso está ejecutando una región crítica (en cualquier parte del programa) con el mismo nombre. Todas las directivas de `critical` sin nombre se asignan al mismo nombre sin especificar.

### <a name="263-barrier-directive"></a>2.6.3 barrera (Directiva)

La Directiva `barrier` sincroniza todos los subprocesos de un equipo. Cuando se encuentran, cada subproceso del equipo espera hasta que todos los demás hayan llegado a este punto. La sintaxis de la Directiva `barrier` es la siguiente:

```cpp
#pragma omp barrier new-line
```

Una vez que todos los subprocesos del equipo han encontrado la barrera, cada subproceso del equipo empieza a ejecutar las instrucciones después de la Directiva de barrera en paralelo. Dado que la Directiva de `barrier` no tiene una instrucción de lenguaje C como parte de su sintaxis, existen algunas restricciones en su ubicación dentro de un programa. Para obtener más información sobre la gramática formal, vea el [Apéndice C](c-openmp-c-and-cpp-grammar.md). En el ejemplo siguiente se muestran estas restricciones.

```cpp
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```

### <a name="264-atomic-construct"></a>2.6.4 Atomic (construcción)

La Directiva de `atomic` garantiza que una ubicación de memoria específica se actualice de forma atómica, en lugar de exponerla a la posibilidad de varios subprocesos de escritura simultánea. La sintaxis de la Directiva `atomic` es la siguiente:

```cpp
#pragma omp atomic new-lineexpression-stmt
```

La instrucción de expresión debe tener una de las siguientes formas:

- *x binop* `=` *expr*
- `++` *x*
- `++` *x*
- `--` *x*
- `--` *x*

En las expresiones anteriores:

- *x* es una expresión lvalue con un tipo escalar.

- *expr* es una expresión con tipo escalar y no hace referencia al objeto designado por *x*.

- *binop* no es un operador sobrecargado y es uno de `+`, `*`, `-`, `/`, `&`, `^`, `|`, `<<`o `>>`.

Aunque se define en la implementación si una implementación reemplaza todas las directivas de `atomic` con directivas de `critical` que tienen el mismo *nombre*único, la directiva de `atomic` permite una mejor optimización. A menudo hay disponibles instrucciones de hardware que pueden realizar la actualización atómica con la mínima sobrecarga.

Solo la carga y el almacenamiento del objeto designado por *x* son atómicos. la evaluación de *expr* no es atómica. Para evitar las condiciones de carrera, todas las actualizaciones de la ubicación en paralelo deben protegerse con la Directiva de `atomic`, excepto aquellas que se sabe que están libres de condiciones de carrera.

Las restricciones de la Directiva de `atomic` son las siguientes:

- Todas las referencias atómicas a la ubicación de almacenamiento x en todo el programa deben tener un tipo compatible.

#### <a name="examples"></a>Ejemplos

```cpp
extern float a[], *p = a, b;
/* Protect against races among multiple updates. */
#pragma omp atomic
a[index[i]] += b;
/* Protect against races with updates through a. */
#pragma omp atomic
p[i] -= 1.0f;

extern union {int n; float x;} u;
/* ERROR - References through incompatible types. */
#pragma omp atomic
u.n++;
#pragma omp atomic
u.x -= 1.0f;
```

### <a name="265-flush-directive"></a>2.6.5 Flush (Directiva)

La Directiva `flush`, ya sea explícita o implícita, especifica un punto de secuencia "entre subprocesos" en el que la implementación es necesaria para garantizar que todos los subprocesos de un equipo tienen una vista coherente de ciertos objetos (especificados a continuación) en la memoria. Esto significa que las evaluaciones anteriores de las expresiones que hacen referencia a esos objetos están completas y las evaluaciones posteriores aún no han empezado. Por ejemplo, los compiladores deben restaurar los valores de los objetos de los registros en la memoria, y es posible que el hardware necesite vaciar los búferes de escritura en la memoria y volver a cargar los valores de los objetos de la memoria.

La sintaxis de la Directiva `flush` es la siguiente:

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Si los objetos que requieren sincronización se pueden designar todos mediante variables, esas variables se pueden especificar en la *lista de variables*opcionales. Si un puntero está presente en la *lista de variables*, se vacía el propio puntero, no el objeto al que hace referencia el puntero.

Una directiva de `flush` sin una *lista de variables* sincroniza todos los objetos compartidos excepto los objetos inaccesibles con duración de almacenamiento automática. (Es probable que se produzca más sobrecarga que una `flush` con una *lista de variables*). Una directiva de `flush` sin una *lista de variables* está implícita para las siguientes directivas:

- `barrier`
- Al entrar y salir de `critical`
- Al entrar y salir de `ordered`
- Al entrar y salir de `parallel`
- Al salir de `for`
- Al salir de `sections`
- Al salir de `single`
- Al entrar y salir de `parallel for`
- Al entrar y salir de `parallel sections`

La Directiva no está implícita si hay una cláusula `nowait`. Se debe observar que la Directiva de `flush` no está implícita para ninguno de los siguientes elementos:

- Entrada en `for`
- Al entrar o salir de `master`
- Entrada en `sections`
- Entrada en `single`

Una referencia que tiene acceso al valor de un objeto con un tipo calificado por volatile se comporta como si hubiese una directiva `flush` que especifica ese objeto en el punto de secuencia anterior. Una referencia que modifica el valor de un objeto con un tipo calificado como volátil se comporta como si hubiera una directiva de `flush` que especifica ese objeto en el punto de secuencia posterior.

Dado que la Directiva de `flush` no tiene una instrucción de lenguaje C como parte de su sintaxis, existen algunas restricciones en su ubicación dentro de un programa. Para obtener más información sobre la gramática formal, vea el [Apéndice C](c-openmp-c-and-cpp-grammar.md). En el ejemplo siguiente se muestran estas restricciones.

```cpp
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

Las restricciones de la Directiva de `flush` son las siguientes:

- Una variable especificada en una directiva de `flush` no debe tener un tipo de referencia.

### <a name="266-ordered-construct"></a>construcción ordenada 2.6.6

El bloque estructurado que sigue a una directiva de `ordered` se ejecuta en el orden en el que se ejecutarán las iteraciones en un bucle secuencial. La sintaxis de la Directiva `ordered` es la siguiente:

```cpp
#pragma omp ordered new-linestructured-block
```

Una directiva de `ordered` debe estar dentro de la extensión dinámica de una construcción de `for` o `parallel for`. La Directiva `for` o `parallel for` a la que se enlaza la construcción de `ordered` debe tener una cláusula `ordered` especificada como se describe en la [sección 2.4.1](#241-for-construct). En la ejecución de una construcción `for` o `parallel for` con una cláusula `ordered`, las construcciones `ordered` se ejecutan estrictamente en el orden en que se ejecutarían en una ejecución secuencial del bucle.

Las restricciones de la Directiva de `ordered` son las siguientes:

- Una iteración de un bucle con una construcción `for` no debe ejecutar la misma directiva ordenada más de una vez y no debe ejecutar más de una directiva `ordered`.

## <a name="27-data-environment"></a>2,7 entorno de datos

En esta sección se presenta una directiva y varias cláusulas para controlar el entorno de datos durante la ejecución de regiones paralelas, como se indica a continuación:

- Se proporciona una directiva [threadprivate](#271-threadprivate-directive) para convertir en un subproceso el ámbito de archivo, el ámbito del espacio de nombres o las variables estáticas de ámbito de bloque.

- Las cláusulas que se pueden especificar en las directivas para controlar los atributos de uso compartido de variables para la duración de las construcciones paralelas o de uso compartido de trabajo se describen en la [sección 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate (Directiva)

La Directiva `threadprivate` hace que las variables con nombre de ámbito de archivo, ámbito de espacio de nombres o ámbito de bloque estático especificadas en la *lista de variables* esté privada en un subproceso. *variable-List* es una lista separada por comas de variables que no tienen un tipo incompleto. La sintaxis de la Directiva `threadprivate` es la siguiente:

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Cada copia de una variable de `threadprivate` se inicializa una vez, en un punto no especificado del programa antes de la primera referencia a esa copia y de la manera habitual (es decir, como la copia maestra se inicializaría en una ejecución en serie del programa). Tenga en cuenta que si se hace referencia a un objeto en un inicializador explícito de una variable `threadprivate`, y el valor del objeto se modifica antes de la primera referencia a una copia de la variable, no se especifica el comportamiento.

Como con cualquier variable privada, un subproceso no debe hacer referencia a la copia de otro subproceso de un objeto `threadprivate`. Durante las regiones en serie y las regiones maestras del programa, las referencias se realizarán a la copia del objeto del subproceso maestro.

Una vez que se ejecuta la primera región paralela, se garantiza que los datos de los objetos `threadprivate` se conservan solo si se ha deshabilitado el mecanismo de subprocesos dinámicos y si el número de subprocesos permanece inalterado en todas las regiones paralelas.

Las restricciones de la Directiva de `threadprivate` son las siguientes:

- Una directiva de `threadprivate` para las variables de ámbito de archivo o de espacio de nombres debe aparecer fuera de cualquier definición o declaración y debe preceder léxicamente a todas las referencias a cualquiera de las variables de su lista.

- Cada variable de la *lista de variables* de una directiva de `threadprivate` en el ámbito de archivo o espacio de nombres debe hacer referencia a una declaración de variable en el ámbito de archivo o espacio de nombres que precede léxicamente a la Directiva.

- Una directiva de `threadprivate` para las variables estáticas de ámbito de bloque debe aparecer en el ámbito de la variable y no en un ámbito anidado. La Directiva debe preceder léxicamente a todas las referencias a cualquiera de las variables de su lista.

- Cada variable de la *lista de variables* de una directiva de `threadprivate` en el ámbito de bloque debe hacer referencia a una declaración de variable en el mismo ámbito que precede léxicamente a la Directiva. La declaración de variable debe usar el especificador de clase de almacenamiento static.

- Si se especifica una variable en una directiva de `threadprivate` en una unidad de traducción, debe especificarse en una directiva de `threadprivate` en cada unidad de traducción en la que se declara.

- Una variable `threadprivate` no debe aparecer en ninguna cláusula excepto en la cláusula `copyin`, `copyprivate`, `schedule`, `num_threads`o `if`.

- La dirección de una variable `threadprivate` no es una constante de dirección.

- Una variable `threadprivate` no debe tener un tipo incompleto o un tipo de referencia.

- Una variable `threadprivate` con un tipo de clase que no sea POD debe tener un constructor de copias accesible y no ambiguo si se ha declarado con un inicializador explícito.

En el ejemplo siguiente se muestra cómo la modificación de una variable que aparece en un inicializador puede provocar un comportamiento no especificado y cómo evitar este problema mediante el uso de un objeto auxiliar y un constructor de copia.

```cpp
int x = 1;
T a(x);
const T b_aux(x); /* Capture value of x = 1 */
T b(b_aux);
#pragma omp threadprivate(a, b)

void f(int n) {
   x++;
   #pragma omp parallel for
   /* In each thread:
   * Object a is constructed from x (with value 1 or 2?)
   * Object b is copy-constructed from b_aux
   */
   for (int i=0; i<n; i++) {
      g(a, b); /* Value of a is unspecified. */
   }
}
```

#### <a name="cross-references"></a>Referencias cruzadas

- [subprocesos dinámicos](3-run-time-library-functions.md#317-omp_set_dynamic-function)
- Variable de entorno [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic)

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 cláusulas de atributo de uso compartido de datos

Varias directivas aceptan cláusulas que permiten a un usuario controlar los atributos de uso compartido de variables para la duración de la región. Las cláusulas de atributo de uso compartido solo se aplican a las variables de la extensión léxica de la Directiva en la que aparece la cláusula. No todas las cláusulas siguientes se permiten en todas las directivas. La lista de cláusulas válidas en una directiva determinada se describe con la Directiva.

Si una variable es visible cuando se encuentra una construcción paralela o de uso compartido de trabajo, y la variable no se especifica en una cláusula de atributo de uso compartido o en una directiva de `threadprivate`, la variable se comparte. Las variables estáticas declaradas dentro de la extensión dinámica de una región paralela están compartidas. Memoria asignada en el montón (por ejemplo, el uso C++ de `malloc()` en C o C++o el operador de `new` en) se comparte. (Sin embargo, el puntero a esta memoria puede ser privado o compartido). Las variables con la duración de almacenamiento automática declarada dentro de la extensión dinámica de una región paralela son privadas.

La mayoría de las cláusulas aceptan un argumento *de lista de variables* , que es una lista separada por comas de variables que están visibles. Si una variable a la que se hace referencia en una cláusula de atributo de uso compartido de datos tiene un tipo derivado de una plantilla y no hay ninguna otra referencia a esa variable en el programa, el comportamiento es indefinido.

Todas las variables que aparecen dentro de las cláusulas de Directiva deben ser visibles. Las cláusulas se pueden repetir según sea necesario, pero no se puede especificar ninguna variable en más de una cláusula, salvo que se puede especificar una variable en una cláusula `firstprivate` y una `lastprivate`.

En las secciones siguientes se describen las cláusulas de atributo de uso compartido de datos:

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [recurso](#2724-shared)
- [valor predeterminado](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

La cláusula `private` declara las variables de la lista de variables para ser privadas para cada subproceso de un equipo. La sintaxis de la cláusula `private` es la siguiente:

```cpp
private(variable-list)
```

El comportamiento de una variable especificada en una cláusula `private` es el siguiente. Se asigna un nuevo objeto con la duración de almacenamiento automática para la construcción. El tamaño y la alineación del nuevo objeto vienen determinados por el tipo de la variable. Esta asignación se produce una vez para cada subproceso del equipo y se invoca un constructor predeterminado para un objeto de clase, si es necesario. de lo contrario, el valor inicial es indeterminado.  El objeto original al que hace referencia la variable tiene un valor indeterminado en el momento de la entrada a la construcción, no debe modificarse dentro de la extensión dinámica de la construcción y tiene un valor indeterminado al salir de la construcción.

En la extensión léxica de la construcción de la Directiva, la variable hace referencia al nuevo objeto privado asignado por el subproceso.

Las restricciones de la cláusula `private` son las siguientes:

- Una variable con un tipo de clase que se especifica en una cláusula `private` debe tener un constructor predeterminado accesible y no ambiguo.

- Una variable especificada en una cláusula `private` no debe tener un tipo calificado `const`a menos que tenga un tipo de clase con un miembro `mutable`.

- Una variable especificada en una cláusula `private` no debe tener un tipo incompleto o un tipo de referencia.

- Las variables que aparecen en la cláusula `reduction` de una directiva `parallel` no se pueden especificar en una cláusula `private` en una directiva de uso compartido de trabajo que se enlaza a la construcción Parallel.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

La cláusula `firstprivate` proporciona un superconjunto de la funcionalidad proporcionada por la cláusula `private`. La sintaxis de la cláusula `firstprivate` es la siguiente:

```cpp
firstprivate(variable-list)
```

Las variables especificadas en *la lista de variables* tienen `private` semántica de la cláusula, como se describe en la [sección 2.7.2.1](#2721-private). La inicialización o la construcción tienen lugar como si se realizara una vez por subproceso, antes de la ejecución del subproceso de la construcción. Para una cláusula `firstprivate` en una construcción paralela, el valor inicial del nuevo objeto privado es el valor del objeto original que existe inmediatamente antes de la construcción Parallel para el subproceso que lo encuentra. Para una cláusula `firstprivate` en una construcción de uso compartido de trabajo, el valor inicial del nuevo objeto privado para cada subproceso que ejecuta la construcción de uso compartido de trabajo es el valor del objeto original que existe antes del momento en que el mismo subproceso encuentra la construcción de uso compartido de trabajo. Además, en el C++ caso de los objetos, el nuevo objeto privado para cada subproceso se construye a partir del objeto original.

Las restricciones de la cláusula `firstprivate` son las siguientes:

- Una variable especificada en una cláusula `firstprivate` no debe tener un tipo incompleto o un tipo de referencia.

- Una variable con un tipo de clase que se especifica como `firstprivate` debe tener un constructor de copias accesible y no ambiguo.

- Las variables que son privadas dentro de una región paralela o que aparecen en la cláusula `reduction` de una directiva `parallel` no se pueden especificar en una cláusula `firstprivate` en una directiva de uso compartido que se enlaza a la construcción Parallel.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

La cláusula `lastprivate` proporciona un superconjunto de la funcionalidad proporcionada por la cláusula `private`. La sintaxis de la cláusula `lastprivate` es la siguiente:

```cpp
lastprivate(variable-list)
```

Las variables especificadas en la *lista de variables* tienen `private` semántica de la cláusula. Cuando aparece una cláusula `lastprivate` en la Directiva que identifica una construcción de uso compartido de trabajo, el valor de cada variable `lastprivate` de la última iteración secuencial del bucle asociado, o de la Directiva de la última sección léxica, se asigna al objeto original de la variable. Las variables a las que no se asigna un valor por la última iteración de la `for` o `parallel for`, o por la última sección léxica de la Directiva `sections` o `parallel sections`, tienen valores indeterminados después de la construcción. Los subobjetos sin asignar también tienen un valor indeterminado después de la construcción.

Las restricciones de la cláusula `lastprivate` son las siguientes:

- Se aplican todas las restricciones de `private`.

- Una variable con un tipo de clase que se especifica como `lastprivate` debe tener un operador de asignación de copia accesible y no ambiguo.

- Las variables que son privadas dentro de una región paralela o que aparecen en la cláusula `reduction` de una directiva `parallel` no se pueden especificar en una cláusula `lastprivate` en una directiva de uso compartido que se enlaza a la construcción Parallel.

#### <a name="2724-shared"></a>2.7.2.4 shared

Esta cláusula comparte las variables que aparecen en la *lista variable* entre todos los subprocesos de un equipo. Todos los subprocesos de un equipo acceden al mismo área de almacenamiento para las variables de `shared`.

La sintaxis de la cláusula `shared` es la siguiente:

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

La cláusula `default` permite al usuario afectar a los atributos de uso compartido de datos de las variables. La sintaxis de la cláusula `default` es la siguiente:

```cpp
default(shared | none)
```

Especificar `default(shared)` es equivalente a enumerar explícitamente cada variable visible actualmente en una cláusula `shared`, a menos que sea `threadprivate` o se califique `const`. En ausencia de una cláusula `default` explícita, el comportamiento predeterminado es el mismo que si se especificara `default(shared)`.

La especificación de `default(none)` requiere que se cumpla al menos uno de los siguientes elementos para cada referencia a una variable en la extensión léxica de la construcción Parallel:

- La variable se muestra explícitamente en una cláusula de atributo de uso compartido de datos de una construcción que contiene la referencia.

- La variable se declara dentro de la construcción Parallel.

- La variable es `threadprivate`.

- La variable tiene un tipo `const`calificado.

- La variable es la variable de control de bucle para un bucle `for` que sigue inmediatamente a una directiva `for` o `parallel for`, y la referencia a la variable aparece dentro del bucle.

Al especificar una variable en una cláusula `firstprivate`, `lastprivate`o `reduction` de una directiva delimitada, se produce una referencia implícita a la variable en el contexto envolvente. Dichas referencias implícitas también están sujetas a los requisitos mencionados anteriormente.

Solo se puede especificar una sola cláusula `default` en una directiva `parallel`.

El atributo de uso compartido de datos predeterminado de una variable se puede invalidar mediante las cláusulas `private`, `firstprivate`, `lastprivate`, `reduction`y `shared`, tal como se muestra en el ejemplo siguiente:

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

Esta cláusula realiza una reducción en las variables escalares que aparecen en la *lista de variables*, con el operador *OP*. La sintaxis de la cláusula `reduction` es la siguiente:

`reduction(` *op* `:` *variable-List* `)`

Normalmente se especifica una reducción para una instrucción con uno de los siguientes formatos:

- *expresión* *x* `=` *x* *OP*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *OP* *x* (excepto para resta)
- `++` *x*
- `++` *x*
- `--` *x*
- `--` *x*

donde:

*x*<br/>
Una de las variables de reducción especificadas en la lista.

*lista de variables*<br/>
Lista separada por comas de variables de reducción escalar.

*expr*<br/>
Expresión con tipo escalar que no hace referencia a *x*.

*operador*<br/>
No es un operador sobrecargado pero uno de `+`, `*`, `-`, `&`, `^`, `|`, `&&`o `||`.

*binop*<br/>
No es un operador sobrecargado pero uno de `+`, `*`, `-`, `&`, `^`o `|`.

El siguiente es un ejemplo de la cláusula `reduction`:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Como se muestra en el ejemplo, un operador puede ocultarse dentro de una llamada de función. El usuario debe tener cuidado de que el operador especificado en la cláusula `reduction` coincida con la operación de reducción.

Aunque el operando derecho del operador `||` no tiene efectos secundarios en este ejemplo, están permitidos, pero deben usarse con cuidado. En este contexto, el efecto secundario que se garantiza que no se produzca durante la ejecución secuencial del bucle puede producirse durante la ejecución en paralelo. Esta diferencia puede producirse porque el orden de ejecución de las iteraciones es indeterminado.

El operador se usa para determinar el valor inicial de todas las variables privadas utilizadas por el compilador para la reducción y para determinar el operador de finalización. Especificar explícitamente el operador permite que la instrucción de reducción esté fuera de la extensión léxica de la construcción. Se puede especificar cualquier número de cláusulas de `reduction` en la Directiva, pero puede aparecer una variable en como máximo una cláusula `reduction` para esa Directiva.

Se crea una copia privada de cada variable en la *lista de variables* , una para cada subproceso, como si se hubiera usado la cláusula `private`. La copia privada se inicializa según el operador (vea la tabla siguiente).

Al final de la región para la que se especificó la cláusula `reduction`, el objeto original se actualiza para reflejar el resultado de la combinación de su valor original con el valor final de cada una de las copias privadas mediante el operador especificado. Los operadores de reducción son todos asociativos (excepto para la resta), y el compilador puede reasociar libremente el cálculo del valor final. (Los resultados parciales de una reducción de resta se agregan para formar el valor final).

El valor del objeto original se convierte en indeterminados cuando el primer subproceso alcanza la cláusula contenedora y permanece así hasta que se completa el cálculo de reducción.  Normalmente, el cálculo se completará al final de la construcción; sin embargo, si se utiliza la cláusula `reduction` en una construcción a la que se aplica también `nowait`, el valor del objeto original permanece indeterminado hasta que se ha realizado una sincronización de barrera para asegurarse de que todos los subprocesos han completado la cláusula `reduction`.

En la tabla siguiente se enumeran los operadores válidos y sus valores de inicialización canónicos. El valor de inicialización real será coherente con el tipo de datos de la variable de reducción.

|Operator|Inicialización|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

Las restricciones de la cláusula `reduction` son las siguientes:

- El tipo de las variables de la cláusula `reduction` debe ser válido para el operador de reducción, excepto en que nunca se permiten tipos de puntero y tipos de referencia.

- Una variable que se especifica en la cláusula `reduction` no debe estar calificada `const`.

- Las variables que son privadas dentro de una región paralela o que aparecen en la cláusula `reduction` de una directiva `parallel` no se pueden especificar en una cláusula `reduction` en una directiva de uso compartido que se enlaza a la construcción Parallel.

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }

   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```

#### <a name="2727-copyin"></a>2.7.2.7 copyin

La cláusula `copyin` proporciona un mecanismo para asignar el mismo valor a `threadprivate` variables para cada subproceso del equipo que ejecuta la región paralela. Para cada variable especificada en una cláusula `copyin`, se copia el valor de la variable en el subproceso maestro del equipo, como si se hubiera asignado, a las copias de subproceso privado al principio de la región paralela. La sintaxis de la cláusula `copyin` es la siguiente:

```cpp

copyin(
variable-list
)
```

Las restricciones de la cláusula `copyin` son las siguientes:

- Una variable que se especifica en la cláusula `copyin` debe tener un operador de asignación de copia accesible y no ambiguo.

- Una variable que se especifica en la cláusula `copyin` debe ser una variable `threadprivate`.

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

La cláusula `copyprivate` proporciona un mecanismo para utilizar una variable privada con el fin de difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor cuando proporcionar este tipo de variable compartida sería difícil (por ejemplo, en una recursividad que requiera una variable diferente en cada nivel). La cláusula `copyprivate` solo puede aparecer en la Directiva `single`.

La sintaxis de la cláusula `copyprivate` es la siguiente:

```cpp

copyprivate(
variable-list
)
```

El efecto de la cláusula `copyprivate` en las variables de su lista de variables se produce después de la ejecución del bloque estructurado asociado a la construcción `single` y antes de que cualquiera de los subprocesos del equipo haya dejado la barrera al final de la construcción. Después, en todos los demás subprocesos del equipo, para cada variable de la *lista de variables*, esa variable se define (como si se hubiera asignado) con el valor de la variable correspondiente en el subproceso que ejecutó el bloque estructurado de la construcción.

Las restricciones de la cláusula `copyprivate` son las siguientes:

- Una variable que se especifica en la cláusula `copyprivate` no debe aparecer en una cláusula `private` o `firstprivate` para la misma directiva `single`.

- Si se encuentra una directiva de `single` con una cláusula `copyprivate` en la extensión dinámica de una región paralela, todas las variables especificadas en la cláusula `copyprivate` deben ser privadas en el contexto envolvente.

- Una variable que se especifica en la cláusula `copyprivate` debe tener un operador de asignación de copia no ambiguo accesible.

## <a name="28-directive-binding"></a>2,8 enlace de directivas

El enlace dinámico de directivas debe cumplir las siguientes reglas:

- Las directivas `for`, `sections`, `single`, `master`y `barrier` se enlazan al `parallel`de inclusión dinámica, si existe, independientemente del valor de cualquier cláusula `if` que pueda estar presente en esa Directiva. Si no se está ejecutando ninguna región paralela, las directivas las ejecuta un equipo compuesto solo por el subproceso maestro.

- La Directiva `ordered` se enlaza a la `for`de inclusión dinámica.

- La Directiva `atomic` exige el acceso exclusivo con respecto a las directivas de `atomic` en todos los subprocesos, no solo al equipo actual.

- La Directiva `critical` exige el acceso exclusivo con respecto a las directivas de `critical` en todos los subprocesos, no solo al equipo actual.

- Una directiva nunca se puede enlazar a ninguna directiva fuera de la `parallel`de inclusión dinámica más cercana.

## <a name="29-directive-nesting"></a>2,9 anidamiento de directivas

La anidación dinámica de directivas debe cumplir las siguientes reglas:

- Una directiva de `parallel` dinámicamente dentro de otra `parallel` establece lógicamente un nuevo equipo, que se compone solo del subproceso actual, a menos que esté habilitado el paralelismo anidado.

- las directivas `for`, `sections`y `single` que se enlazan a la misma `parallel` no se pueden anidar dentro de otras.

- las directivas de `critical` con el mismo nombre no se pueden anidar unas dentro de otras. Tenga en cuenta que esta restricción no es suficiente para evitar el interbloqueo.

- las directivas `for`, `sections`y `single` no se permiten en la extensión dinámica de las regiones `critical`, `ordered`y `master` si las directivas se enlazan a la misma `parallel` que las regiones.

- las directivas de `barrier` no se permiten en la extensión dinámica de las regiones `for`, `ordered`, `sections`, `single`, `master`y `critical` si las directivas se enlazan a la misma `parallel` que las regiones.

- las directivas de `master` no se permiten en la extensión dinámica de las directivas `for`, `sections`y `single` si las directivas de `master` se enlazan al mismo `parallel` que las directivas de uso compartido de trabajo.

- las directivas de `ordered` no se permiten en la extensión dinámica de las regiones `critical` si las directivas se enlazan a la misma `parallel` que las regiones.

- También se permite cualquier directiva que se permita cuando se ejecute dinámicamente dentro de una región paralela cuando se ejecute fuera de una región paralela. Cuando se ejecuta de forma dinámica fuera de una región paralela especificada por el usuario, la Directiva se ejecuta en un equipo compuesto solo por el subproceso maestro.
