---
title: 2. Directivas
ms.date: 01/18/2019
ms.assetid: d1a69374-6c03-45fb-8c86-e91cea8adae8
ms.openlocfilehash: 125d2d83b277e62d007e3a208e426ea717d52790
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363718"
---
# <a name="2-directives"></a>2. Directivas

Las directivas se basan en `#pragma` directivas definidas en los estándares de C y C++.  Los compiladores que admiten la de OpenMP C y C++ API incluirá una opción de línea de comandos que se activa y permite la interpretación de todas las directivas de compilador de OpenMP.

## <a name="21-directive-format"></a>2.1 formato de directivas

La sintaxis de una directiva de OpenMP se especifican formalmente la gramática en [Apéndice C](c-openmp-c-and-cpp-grammar.md)e informalmente como sigue:

```cpp
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

Cada directiva comienza con `#pragma omp`para reducir la posibilidad de conflicto con otras directivas pragma de (que no sean de OpenMP o proveedor extensiones OpenMP) con los mismos nombres. El resto de la directiva sigue las convenciones de los estándares de C y C++ para las directivas de compilador. En concreto, se puede usar espacios en blanco antes y después el `#`, y a veces se debe usar un espacio en blanco para separar las palabras en una directiva. Después de los tokens de preprocesamiento el `#pragma omp` están sujetos a reemplazo de macros.

Directivas distinguen mayúsculas de minúsculas. El orden en que aparecen en las directivas no es significativo. Las cláusulas en las directivas se pueden repetir según sea necesario, sujeto a las restricciones que aparecen en la descripción de cada cláusula. Si *variable lista* aparece en una cláusula, deben especificar solo las variables. Solo un *nombre de directiva* se puede especificar por directiva.  Por ejemplo, no se permite la directiva siguiente:

```cpp
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

Se aplica una directiva de OpenMP a lo sumo una subsiguiente instrucción, que debe ser un bloque estructurado.

## <a name="22-conditional-compilation"></a>2.2 compilación condicional

El `_OPENMP` nombre de macro se define mediante implementaciones compatibles con OpenMP como la constante decimal *AAAAMM*, que será el año y mes de la especificación aprobada. Esta macro no debe ser el sujeto de un `#define` o un `#undef` preprocesamiento de directiva.

```cpp
#ifdef _OPENMP
iam = omp_get_thread_num() + index;
#endif
```

Si los proveedores de definan extensiones para OpenMP, pueden especificar adicionales macros predefinidas.

## <a name="23-parallel-construct"></a>2.3 parallel (construcción)

La directiva siguiente define una región paralela, que es una región del programa que va a ser ejecutado por muchos subprocesos en paralelo. Esta directiva es la construcción fundamental que se inicia la ejecución en paralelo.

```cpp
#pragma omp parallel [clause[ [, ]clause] ...] new-line   structured-block
```

El *cláusula* es uno de los siguientes:

- `if(` *scalar-expression* `)`
- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `default(shared | none)`
- `shared(` *variable-list* `)`
- `copyin(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `num_threads(` *integer-expression* `)`

Cuando un subproceso llega a una construcción paralela, se crea un grupo de subprocesos si se cumple una de los casos siguientes:

- No `if` cláusula está presente.
- El `if` expresión se evalúa como un valor distinto de cero.

Este subproceso se convierte en el subproceso principal del equipo, con un número de subprocesos de 0, y todos los subprocesos en el equipo, incluido el subproceso principal, la región se ejecutan en paralelo. Si el valor de la `if` expresión es cero, se serializa la región.

Para determinar el número de subprocesos que se solicitan, se considerarán las reglas siguientes en orden. Se aplicará la primera regla cuya condición se cumple:

1. Si el `num_threads` cláusula está presente, el valor de la expresión de entero es el número de subprocesos que se solicita.

1. Si el `omp_set_num_threads` se ha llamado la función de biblioteca y, después, el valor del argumento en la llamada ha ejecutado más recientemente es el número de subprocesos que se solicita.

1. Si la variable de entorno `OMP_NUM_THREADS` está definido, el valor de esta variable de entorno es el número de subprocesos que se solicita.

1. Si se usa ninguno de los métodos anteriores, el número de subprocesos es definido por la implementación.

Si el `num_threads` cláusula está presente, a continuación, reemplaza el número de subprocesos solicitado por el `omp_set_num_threads` función de biblioteca o el `OMP_NUM_THREADS` variable de entorno solo para la región paralela que se aplica. Más adelante regiones en paralelo no se ven afectadas por ella.

El número de subprocesos que se ejecutan en la región paralela también depende de si está habilitado el ajuste dinámico del número de subprocesos. Si se deshabilita el ajuste dinámico, el número solicitado de subprocesos ejecutará la región paralela. Si está habilitado el ajuste dinámico, a continuación, el número solicitado de subprocesos es el número máximo de subprocesos que se pueden ejecutar a la región paralela.

Si se encuentra una región paralela mientras está deshabilitado el ajuste dinámico del número de subprocesos, y el número de subprocesos solicitado para la región paralela es mayor que el número que puede proporcionar el sistema de tiempo de ejecución, el comportamiento del programa es definido por la implementación. Una implementación, por ejemplo, puede interrumpir la ejecución del programa, o puede serializar la región paralela.

El `omp_set_dynamic` función de biblioteca y el `OMP_DYNAMIC` variable de entorno puede utilizarse para habilitar y deshabilitar el ajuste dinámico del número de subprocesos.

El número de procesadores físicos hospedando en realidad los subprocesos en un momento dado es definido por la implementación. Una vez creado, el número de subprocesos en el equipo permanece constante para la duración de esa región paralela. Puede cambiarse explícitamente por el usuario o automáticamente por el sistema de tiempo de ejecución de una región paralela a otra.

Se ejecutan las instrucciones incluidas en la extensión de la región paralela dinámica por cada subproceso, y cada subproceso puede ejecutar una ruta de acceso de las instrucciones que es diferente de los demás subprocesos. Las directivas que se encuentra fuera de la extensión léxica de una región paralela se conocen como directivas huérfanas.

Hay una barrera implícita al final de una región paralela. Solo el subproceso principal del equipo continúa la ejecución al final de una región paralela.

Si un subproceso en un equipo que ejecuta una región paralela encuentra otra construcción paralela, crea un nuevo equipo y se convierte en el maestro de ese nuevo equipo. Las regiones paralelas anidadas se serializan de forma predeterminada. Como resultado, de forma predeterminada, una región paralela anidada se ejecuta por un equipo que se compone de un subproceso. Se puede cambiar el comportamiento predeterminado mediante el uso de la función de biblioteca de tiempo de ejecución `omp_set_nested` o la variable de entorno `OMP_NESTED`. Sin embargo, el número de subprocesos en un equipo que ejecute una región paralela anidada es definido por la implementación.

Restricciones para el `parallel` directiva son los siguientes:

- A lo sumo, una `if` cláusula puede aparecer en la directiva.

- No se especifica si cualquiera de efectos dentro expresión o `num_threads` expresión se producen.

- Un `throw` ejecuta dentro de una región paralela debe provocar que la ejecución reanudar dentro de la extensión dinámica del mismo bloque estructurado y se debe detectar mediante el mismo subproceso que produjo la excepción.

- Una sola `num_threads` cláusula puede aparecer en la directiva. El `num_threads` expresión se evalúa fuera del contexto de la región paralela y se debe evaluar como un valor entero positivo.

- El orden de evaluación de la `if` y `num_threads` cláusulas no se ha especificado.

### <a name="cross-references"></a>Referencias cruzadas

- `private`, `firstprivate`, `default`, `shared`, `copyin`, y `reduction` cláusulas ([sección 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_NUM_THREADS](4-environment-variables.md#42-omp_num_threads) variable de entorno
- [omp_set_dynamic ()](3-run-time-library-functions.md#317-omp_set_dynamic-function) función de biblioteca
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable de entorno
- [omp_set_nested ()](3-run-time-library-functions.md#319-omp_set_nested-function) (función)
- [OMP_NESTED](4-environment-variables.md#44-omp_nested) variable de entorno
- [omp_set_num_threads ()](3-run-time-library-functions.md#311-omp_set_num_threads-function) función de biblioteca

## <a name="24-work-sharing-constructs"></a>2.4 construcciones de uso compartido

Una construcción de uso compartido distribuye la ejecución de la instrucción asociada entre los miembros del equipo que alcanzarlo. Las directivas de uso compartido no iniciar nuevos subprocesos, y no hay ninguna barrera implícita en la entrada a una construcción de uso compartido.

Construye la secuencia de uso compartido y `barrier` directivas encontradas deben ser el mismo para todos los subprocesos en un equipo.

OpenMP define las siguientes construcciones de uso compartido, y estas construcciones se describen en las secciones siguientes:

- [para](#241-for-construct) directiva
- [las secciones](#242-sections-construct) directiva
- [solo](#243-single-construct) directiva

### <a name="241-for-construct"></a>2.4.1 for (construcción)

El `for` directiva identifica una construcción de uso compartido de trabajo iterativa que especifica que las iteraciones del bucle asociada se ejecutarán en paralelo. Las iteraciones de la `for` bucle se distribuyen entre los subprocesos que ya existen en el equipo que ejecuta la construcción paralela a la que se enlaza. La sintaxis de la `for` construcción es como sigue:

```cpp
#pragma omp for [clause[[,] clause] ... ] new-line for-loop
```

La cláusula es uno de los siguientes:

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:` *variable-list* `)`
- `ordered`
- `schedule(` *kind* [`,` *chunk_size*] `)`
- `nowait`

El `for` directiva impone restricciones en la estructura de los correspondientes `for` bucle. En concreto, la correspondiente `for` bucle debe tener la forma canónica:

`for (` *init-expr* `;` *var  logical-op  b* `;` *incr-expr* `)`

*init-expr*<br/>
Uno de los siguientes:

- *var* = *lb*
- *integer-type var* = *lb*

*incr-expr*<br/>
Uno de los siguientes:

- `++` *var*
- *var* `++`
- `--` *var*
- *var* `--`
- *var* `+=` *incr*
- *var* `-=` *incr*
- *var* `=` *var* `+` *incr*
- *var* `=` *incr* `+` *var*
- *var* `=` *var* `-` *incr*

*var*<br/>
Una variable de entero con signo. Si esta variable se pueden compartir en caso contrario, se implícitamente hace privada para el tiempo que dure la `for`. No modifique esta variable dentro del cuerpo de la `for` instrucción. A menos que se especifica la variable `lastprivate`, su valor después de que el bucle es indeterminado.

*logical-op*<br/>
Uno de los siguientes:

- `<`
- `<=`
- `>`
- `>=`

*lb*, *b*, y *incr*<br>
Las expresiones de enteros invariable de bucle. No hay ninguna sincronización durante la evaluación de estas expresiones, por lo que los efectos secundarios evaluados producir resultados indeterminados.

La forma canónica permite que el número de iteraciones del bucle debe calcularse en la entrada para el bucle. Este cálculo se realiza con los valores en el tipo de *var*, después de promociones de enteros. En particular, si el valor de *b* `-` *lb* `+` *incr* no se puede representar en que el tipo, el resultado es indeterminado. Además, si *lógico op* es `<` o `<=`, a continuación, *incr expr* debe provocar *var* para aumentar en cada iteración del bucle.   Si *lógico op* es `>` o `>=`, a continuación, *incr expr* debe provocar *var* mantendría en cada iteración del bucle.

El `schedule` cláusula especifica cómo las iteraciones de la `for` bucle se dividen entre los subprocesos del equipo. La corrección de un programa no debe depender de qué subproceso ejecuta una iteración determinada. El valor de *chunk_size*, si se especifica, debe ser una expresión de entero invariable de bucle con un valor positivo. No hay ninguna sincronización durante la evaluación de esta expresión, por lo que los efectos secundarios evaluados producir resultados indeterminados. La programación *tipo* puede ser uno de los siguientes valores:

Tabla 2-1: `schedule` cláusula *tipo* valores

|||
|-|-|
|estático|Cuando `schedule(static,` *chunk_size* `)` se especifica, las iteraciones se dividen en fragmentos de un tamaño especificado por *chunk_size*. Los fragmentos se asignan estáticamente a subprocesos en el equipo en un modo round-robin en el orden el número de subprocesos. Cuando no hay ninguna *chunk_size* se especifica, el espacio de la iteración se divide en fragmentos que son aproximadamente iguales en tamaño, con un solo fragmento asignado a cada subproceso.|
|dynamic|Cuando `schedule(dynamic,` *chunk_size* `)` se especifica, las iteraciones se dividen en una serie de fragmentos, cada uno con *chunk_size* iteraciones. Cada fragmento se asigna a un subproceso que está esperando una asignación. El subproceso ejecuta el fragmento de iteraciones y, a continuación, espera para su asignación siguiente, hasta que ningún fragmento permanecen para asignarse. El último fragmento que se asignará puede tener un menor número de iteraciones. Cuando no hay ninguna *chunk_size* se especifica, el valor predeterminado es 1.|
|guiada por perfiles|Cuando `schedule(guided,` *chunk_size* `)` se especifica, las iteraciones se asignan a subprocesos en fragmentos con disminuir el tamaño. Cuando un subproceso finaliza su fragmento asignado de iteraciones, se asigna dinámicamente otro fragmento, hasta que se deja a ninguno. Para un *chunk_size* de 1, el tamaño de cada fragmento es aproximadamente el número de iteraciones sin asignar dividido por el número de subprocesos. Estos tamaños casi exponencialmente disminuyen en 1. Para un *chunk_size* con valor *k* mayor que 1, los tamaños de disminuir exponencialmente casi a *k*, salvo que el último fragmento puede tener menos de *k* iteraciones. Cuando no hay ninguna *chunk_size* se especifica, el valor predeterminado es 1.|
|motor en tiempo de ejecución|Cuando `schedule(runtime)` se especifica, la decisión sobre la programación se retrasa hasta el tiempo de ejecución. La programación *tipo* y tamaño de los fragmentos se puede elegir en tiempo de ejecución estableciendo la variable de entorno `OMP_SCHEDULE`. Si no se establece esta variable de entorno, la programación resultante es definido por la implementación. Cuando `schedule(runtime)` se especifica, *chunk_size* no debe especificarse.|

En ausencia de definido explícitamente `schedule` cláusula, el valor predeterminado `schedule` define la implementación.

Un programa compatible con OpenMP no debe confiar en un programa en particular para su ejecución correcta. Un programa no debe confiar en una programación *tipo* que se ajuste exactamente a la descripción proporcionada más arriba, porque es posible que las variaciones en las implementaciones de la misma programación *tipo* a través de diferentes compiladores. Las descripciones se pueden usar para seleccionar la programación que es adecuada para una situación en particular.

El `ordered` cláusula debe estar presente cuando `ordered` directivas enlazar a la `for` construir.

Hay una barrera implícita al final de un `for` construir a menos que un `nowait` se especifica la cláusula.

Restricciones para el `for` directiva son los siguientes:

- El `for` bucle debe ser un bloque estructurado y, además, su ejecución no debe terminar con un `break` instrucción.

- Los valores del bucle controlan las expresiones de la `for` bucle asociado con un `for` directiva debe ser el mismo para todos los subprocesos en el equipo.

- El `for` variable de iteración del bucle debe tener un tipo entero con signo.

- Una sola `schedule` cláusula puede aparecer en un `for` directiva.

- Una sola `ordered` cláusula puede aparecer en un `for` directiva.

- Una sola `nowait` cláusula puede aparecer en un `for` directiva.

- Es si no especificado o con qué frecuencia los efectos secundarios dentro de la *chunk_size*, *lb*, *b*, o *incr* las expresiones se encuentran.

- El valor de la *chunk_size* expresión debe ser el mismo para todos los subprocesos en el equipo.

#### <a name="cross-references"></a>Referencias cruzadas

- `private`, `firstprivate`, `lastprivate`, y `reduction` cláusulas ([sección 2.7.2](#272-data-sharing-attribute-clauses))
- [OMP_SCHEDULE](4-environment-variables.md#41-omp_schedule) variable de entorno
- [ordenar](#266-ordered-construct) construir
- [programación](d-using-the-schedule-clause.md) cláusula

### <a name="242-sections-construct"></a>2.4.2 secciones construcción

El `sections` directiva identifica una construcción noniterative uso compartido que especifica un conjunto de construcciones que se va a dividir entre los subprocesos en un equipo. Cada sección se ejecuta una vez por un subproceso en el equipo. La sintaxis de la `sections` directiva es como sigue:

```cpp
#pragma omp sections [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block ]
...
}
```

La cláusula es uno de los siguientes:

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `lastprivate(` *variable-list* `)`
- `reduction(` *operator* `:`  *variable-list* `)`
- `nowait`

Cada sección está precedido por un `section` directiva, aunque el `section` directiva es opcional para la primera sección. El `section` las directivas deben aparecer dentro de la extensión de léxico el `sections` directiva. Hay una barrera implícita al final de un `sections` construir, a menos que un `nowait` se especifica.

Restricciones para el `sections` directiva son los siguientes:

- Un `section` directiva no debe aparecer fuera de la extensión de léxico el `sections` directiva.

- Una sola `nowait` cláusula puede aparecer en un `sections` directiva.

#### <a name="cross-references"></a>Referencias cruzadas

- `private`, `firstprivate`, `lastprivate`, y `reduction` cláusulas ([sección 2.7.2](#272-data-sharing-attribute-clauses))

### <a name="243-single-construct"></a>2.4.3 single (construcción)

El `single` directiva identifica una construcción que especifica que se ejecuta el bloque estructurado asociado sólo un subproceso en el equipo (no necesariamente el subproceso principal). La sintaxis de la `single` directiva es como sigue:

```cpp
#pragma omp single [clause[[,] clause] ...] new-linestructured-block
```

La cláusula es uno de los siguientes:

- `private(` *variable-list* `)`
- `firstprivate(` *variable-list* `)`
- `copyprivate(` *variable-list* `)`
- `nowait`

Hay una barrera implícita después de la `single` construir a menos que un `nowait` se especifica la cláusula.

Restricciones para el `single` directiva son los siguientes:

- Una sola `nowait` cláusula puede aparecer en un `single` directiva.
- El `copyprivate` cláusula no debe usarse con el `nowait` cláusula.

#### <a name="cross-references"></a>Referencias cruzadas

- `private`, `firstprivate`, y `copyprivate` cláusulas ([sección 2.7.2](#272-data-sharing-attribute-clauses))

## <a name="25-combined-parallel-work-sharing-constructs"></a>2.5 combinado construcciones de uso compartido paralelas

Construcciones de uso compartido paralelas combinadas son accesos directos para especificar una región paralela que tiene solo una construcción de uso compartido. La semántica de estas directivas es lo mismo que especificar explícitamente un `parallel` directiva seguida por una única construcción de uso compartido.

Las secciones siguientes describen las construcciones de uso compartido paralelas combinadas:

- [paralelo para](#251-parallel-for-construct) directiva
- [las secciones en paralelo](#252-parallel-sections-construct) directiva

### <a name="251-parallel-for-construct"></a>2.5.1 parallel for (construcción)

El `parallel for` directiva es un acceso directo para un `parallel` región que contiene una sola `for` directiva. La sintaxis de la `parallel for` directiva es como sigue:

```cpp
#pragma omp parallel for [clause[[,] clause] ...] new-linefor-loop
```

Esta directiva permite que todas las cláusulas de la `parallel` directiva y la `for` la directiva, excepto el `nowait` cláusula con significados idénticos y restricciones. La semántica es lo mismo que especificar explícitamente un `parallel` directiva seguido inmediatamente por un `for` directiva.

#### <a name="cross-references"></a>Referencias cruzadas

- [paralelo](#23-parallel-construct) directiva
- [para](#241-for-construct) directiva
- [Cláusulas de atributos de datos](#272-data-sharing-attribute-clauses)

### <a name="252-parallel-sections-construct"></a>2.5.2 parallel secciones construcción

El `parallel sections` directiva proporciona un formulario de método abreviado para especificar un `parallel` región que tiene una sola `sections` directiva. La semántica es lo mismo que especificar explícitamente un `parallel` directiva seguido inmediatamente por un `sections` directiva. La sintaxis de la `parallel sections` directiva es como sigue:

```cpp
#pragma omp parallel sections  [clause[[,] clause] ...] new-line
   {
   [#pragma omp section new-line]
      structured-block
   [#pragma omp section new-linestructured-block  ]
   ...
}
```

El *cláusula* puede ser una de las cláusulas aceptadas por el `parallel` y `sections` directivas, excepto el `nowait` cláusula.

#### <a name="cross-references"></a>Referencias cruzadas

- [paralelo](#23-parallel-construct) directiva
- [las secciones](#242-sections-construct) directiva

## <a name="26-master-and-synchronization-directives"></a>2.6 directivas Master y sincronización

Las secciones siguientes describen:

- [maestro](#261-master-construct) construir
- [crítica](#262-critical-construct) construir
- [barrera](#263-barrier-directive) directiva
- [atomic](#264-atomic-construct) construir
- [Vaciar](#265-flush-directive) directiva
- [ordenar](#266-ordered-construct) construir

### <a name="261-master-construct"></a>2.6.1 master (construcción)

El `master` directiva identifica una construcción que especifica un bloque estructurado que se ejecuta el subproceso principal del equipo. La sintaxis de la `master` directiva es como sigue:

```cpp
#pragma omp master new-linestructured-block
```

Otros subprocesos en el equipo no ejecutan el bloque estructurado asociado. No hay ninguna barrera implícita ya sea en la entrada o salida de la construcción principal.

### <a name="262-critical-construct"></a>2.6.2 critical (construcción)

El `critical` directiva identifica una construcción que limita la ejecución del bloque estructurado asociado a un único subproceso cada vez. La sintaxis de la `critical` directiva es como sigue:

```cpp
#pragma omp critical [(name)]  new-linestructured-block
```

Opcional *nombre* puede utilizarse para identificar la región crítica. Los identificadores utilizados para identificar una región crítica tienen vinculación externa y se encuentran en un espacio de nombres es independiente de los espacios de nombres utilizados por etiquetas, etiquetas, miembros y los identificadores normales.

Un subproceso espera al principio de una región crítica hasta que ningún otro subproceso está ejecutando en una región crítica (en cualquier lugar en el programa) con el mismo nombre. Todo sin nombre `critical` asignan directivas en el mismo nombre no especificado.

### <a name="263-barrier-directive"></a>2.6.3 directiva barrier

El `barrier` directiva sincroniza todos los subprocesos en un equipo. Cuando encuentra, cada subproceso en el equipo espera hasta que todos los demás han alcanzado este punto. La sintaxis de la `barrier` directiva es como sigue:

```cpp
#pragma omp barrier new-line
```

Después de que todos los subprocesos en el equipo han detectado la barrera, cada subproceso en el equipo comienza a ejecutar las instrucciones después de la directiva de barrera en paralelo. Dado que el `barrier` directiva no tiene una instrucción del lenguaje C como parte de su sintaxis, hay algunas restricciones en su posición dentro de un programa. Para obtener más información sobre la gramática formal, consulte [Apéndice C](c-openmp-c-and-cpp-grammar.md). El ejemplo siguiente muestra estas restricciones.

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

### <a name="264-atomic-construct"></a>2.6.4 atomic (construcción)

El `atomic` Directiva garantiza que una ubicación de memoria específica se actualiza de forma atómica, en lugar de exponerlos a la posibilidad de múltiples simultáneas de escritura de subprocesos. La sintaxis de la `atomic` directiva es como sigue:

```cpp
#pragma omp atomic new-lineexpression-stmt
```

La instrucción de expresión debe tener una de las siguientes formas:

- *x binop* `=` *expr*
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

En las expresiones anteriores:

- *x* es una expresión de valor l con el tipo escalar.

- *Expr* es una expresión con tipo escalar, y no hace referencia el objeto designado por *x*.

- *binop* no es un operador sobrecargado y es uno de `+`, `*`, `-`, `/`, `&`, `^`, `|`, `<<`, o `>>`.

Aunque es definido por la implementación si una implementación reemplaza toda `atomic` directivas con `critical` directivas que tienen el mismo único *nombre*, el `atomic` directiva permite una mejor optimización . A menudo las instrucciones de hardware están disponibles que puede realizar la actualización atómica con la menor carga.

Solo la carga y el almacén del objeto designado por *x* son atómica; la evaluación de *expr* no es atómica. Para evitar condiciones de carrera, todas las actualizaciones de la ubicación en paralelo deben protegerse con el `atomic` la directiva, excepto los que se sabe que están libres de las condiciones de carrera.

Restricciones para el `atomic` directiva son los siguientes:

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

### <a name="265-flush-directive"></a>2.6.5 flush (directiva)

El `flush` directiva, ya sea explícita o implícita, especifica un punto de secuencia "entre subprocesos" en el que se requiere la implementación para asegurarse de que todos los subprocesos en un equipo tienen una vista coherente de ciertos objetos (especificadas a continuación) en la memoria. Esto significa que finalizan las evaluaciones anteriores de las expresiones que hacen referencia a esos objetos y las evaluaciones posteriores todavía no han comenzado. Por ejemplo, los compiladores deben restaurar los valores de los objetos de los registros a la memoria y hardware que deba vaciar los búferes de escritura a la memoria y volver a los valores de los objetos de la memoria.

La sintaxis de la `flush` directiva es como sigue:

```cpp
#pragma omp flush [(variable-list)]  new-line
```

Si los objetos que requieren sincronización pueden designarse por variables y, después, esas variables se pueden especificar en el elemento opcional *variable lista*. Si un puntero se encuentra en la *lista de variables*, el propio puntero se vacía, no el objeto hace referencia el puntero.

Un `flush` la directiva sin un *variable lista* sincroniza los objetos compartidos todo excepto los objetos inaccesibles con una duración de almacenamiento automático. (Esto es probable que tenga más sobrecarga que una `flush` con un *lista de variables*.) Un `flush` la directiva sin un *variable lista* está implícito en las siguientes directivas:

- `barrier`
- En la entrada y la salida de `critical`
- En la entrada y la salida de `ordered`
- En la entrada y la salida de `parallel`
- Al salir desde `for`
- Al salir desde `sections`
- Al salir desde `single`
- En la entrada y la salida de `parallel for`
- En la entrada y la salida de `parallel sections`

La directiva no afecta a si un `nowait` cláusula está presente. Se debe tener en cuenta que el `flush` directiva no es implícito para cualquiera de las siguientes acciones:

- En la entrada a `for`
- En la entrada o salida de `master`
- En la entrada a `sections`
- En la entrada a `single`

Una referencia que tiene acceso al valor de un objeto con un tipo calificado como volátil se comporta como si hubiera un `flush` Directiva especifique ese objeto en el momento de la secuencia anterior. Una referencia que modifica el valor de un objeto con un tipo calificado como volátil se comporta como si hubiera un `flush` Directiva especifique ese objeto en el momento de la secuencia.

Dado que el `flush` directiva no tiene una instrucción del lenguaje C como parte de su sintaxis, hay algunas restricciones en su posición dentro de un programa. Para obtener más información sobre la gramática formal, consulte [Apéndice C](c-openmp-c-and-cpp-grammar.md). El ejemplo siguiente muestra estas restricciones.

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

Restricciones para el `flush` directiva son los siguientes:

- Una variable especificada en un `flush` directiva no debe tener un tipo de referencia.

### <a name="266-ordered-construct"></a>2.6.6 construcción ordenada

El bloque estructurado que sigue un `ordered` directiva se ejecuta en el orden en el que se ejecutan en un bucle secuencial iteraciones. La sintaxis de la `ordered` directiva es como sigue:

```cpp
#pragma omp ordered new-linestructured-block
```

Un `ordered` directiva debe estar dentro de la extensión dinámica de un `for` o `parallel for` construir. El `for` o `parallel for` la directiva a la que el `ordered` construcción enlaza debe tener un `ordered` cláusula especificada como se describe en [sección 2.4.1](#241-for-construct). En la ejecución de un `for` o `parallel for` construir con un `ordered` cláusula, `ordered` construcciones se ejecutan de forma estricta en el orden en el que se ejecutaría en una ejecución secuencial del bucle.

Restricciones para el `ordered` directiva son los siguientes:

- Una iteración de un bucle con un `for` construcción no debe ejecutar la misma directiva ordered más de una vez y no debe ejecutar más de un `ordered` directiva.

## <a name="27-data-environment"></a>2.7 entorno de datos

En esta sección se presenta una directiva y varias cláusulas para controlar el entorno de datos durante la ejecución de las regiones en paralelo, como sigue:

- Un [threadprivate](#271-threadprivate-directive) directiva se proporciona para hacer que variables estáticas del ámbito de bloque, ámbito de espacio de nombres o ámbito de archivo local a un subproceso.

- Las cláusulas que se pueden especificar en las directivas para controlar los atributos de uso compartido de las variables de la duración de las construcciones paralelas o uso compartido se describen en [sección 2.7.2](#272-data-sharing-attribute-clauses).

### <a name="271-threadprivate-directive"></a>2.7.1 threadprivate (directiva)

El `threadprivate` directiva hace que el ámbito de archivo con nombre, ámbito de espacio de nombres o variables estáticas del ámbito de bloque especificadas en el *variable lista* privados de un subproceso. *lista de variables* es una lista separada por comas de variables que no tienen un tipo incompleto. La sintaxis de la `threadprivate` directiva es como sigue:

```cpp
#pragma omp threadprivate(variable-list) new-line
```

Cada copia de un `threadprivate` variable se inicializa una vez, en un punto especificado en el programa antes de la primera referencia a esa copia y de la forma habitual (es decir, como la copia maestra se inicializaría en una ejecución en serie del programa). Tenga en cuenta que si se hace referencia a un objeto en un inicializador explícito de un `threadprivate` variable y el valor del objeto se modifica antes de la primera referencia a una copia de la variable y, después, el comportamiento no está especificado.

Como con cualquier variable privada, un subproceso no debe hacer referencia a copia de otro subproceso de un `threadprivate` objeto. Durante la serie y regiones principales del programa, las referencias será copia del subproceso principal del objeto.

Una vez que se ejecuta la primera región paralela, los datos en el `threadprivate` se garantiza que los objetos para conservar solo si los subprocesos del mecanismo dinámico se ha deshabilitado, y si el número de subprocesos permanece sin cambios para todas las regiones en paralelo.

Las restricciones para el `threadprivate` directiva son los siguientes:

- Un `threadprivate` debe aparecer fuera de cualquier definición o declaración de directiva para las variables de ámbito de archivo o el ámbito de espacio de nombres y debe preceder léxicamente a todas las referencias a cualquiera de las variables en su lista.

- Cada variable en el *lista de variables* de un `threadprivate` directiva en el ámbito de archivo o espacio de nombres debe hacer referencia a una declaración de variable en el ámbito de archivo o espacio de nombres que precede léxicamente a la directiva.

- Un `threadprivate` directiva para las variables de ámbito de bloque estática debe aparecer en el ámbito de la variable y no en un ámbito anidado. La directiva debe preceder léxicamente a todas las referencias a cualquiera de las variables en su lista.

- Cada variable en el *lista de variables* de un `threadprivate` directiva en el ámbito de bloque debe hacer referencia a una declaración de variable en el mismo ámbito que precede léxicamente a la directiva. La declaración de variable debe usar el especificador de clase de almacenamiento estática.

- Si se especifica una variable en un `threadprivate` la directiva en una unidad de traducción, se debe especificar en una `threadprivate` la directiva en cada unidad de traducción en el que se declara.

- Un `threadprivate` variable no debe aparecer en cualquier cláusula excepto el `copyin`, `copyprivate`, `schedule`, `num_threads`, o el `if` cláusula.

- La dirección de un `threadprivate` variable no es una constante de dirección.

- Un `threadprivate` variable no debe tener un tipo incompleto ni un tipo de referencia.

- Un `threadprivate` variable con tipo de clase POD no debe tener un constructor de copias sea accesible y no ambigua, si se declara con un inicializador explícito.

El ejemplo siguiente muestra cómo modificar una variable que aparece en un inicializador puede provocar un comportamiento no especificado y cómo evitar este problema mediante el uso de un objeto auxiliar y un constructor de copias.

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
- [OMP_DYNAMIC](4-environment-variables.md#43-omp_dynamic) variable de entorno

### <a name="272-data-sharing-attribute-clauses"></a>2.7.2 cláusulas de atributos uso compartido de datos

Varias directivas aceptan las cláusulas que permitir que un usuario controlar los atributos de uso compartido de las variables de la duración de la región. Cláusulas de atributos de uso compartido sólo se aplican a las variables de la extensión léxica de la directiva en el que aparece la cláusula. Todas las cláusulas siguientes no se permiten en todas las directivas. La lista de cláusulas que son válidos en una directiva determinada se describen con la directiva.

Si una variable es visible cuando un paralelo o se encuentra la construcción de uso compartido y la variable no se especifica en una cláusula de atributos de uso compartido o `threadprivate` la directiva, a continuación, la variable se comparte. Las variables estáticas declaradas dentro de la extensión dinámica de una región paralela se comparten. Montón de memoria asignada (por ejemplo, mediante `malloc()` en C o C++ o la `new` operador de C++) se comparte. (El puntero a esta memoria, sin embargo, puede ser privados o compartidos.) Las variables con una duración de almacenamiento automática declarados dentro de la extensión de una región paralela dinámica son privadas.

La mayoría de las cláusulas de acepta un *lista de variables* argumento, que es una lista separada por comas de variables que están visibles. Si hace referencia una variable en una cláusula de atributos de uso compartido de datos tiene un tipo derivado de una plantilla y no hay ninguna otra referencia a esa variable en el programa, el comportamiento es indefinido.

Todas las variables que aparecen en las cláusulas de la Directiva deben estar visibles. Se pueden repetir las cláusulas según sea necesario, pero no hay ninguna variable puede especificarse en más de una cláusula, salvo que se puede especificar una variable en ambos un `firstprivate` y un `lastprivate` cláusula.

Las secciones siguientes describen las cláusulas de atributos de uso compartido de datos:

- [private](#2721-private)
- [firstprivate](#2722-firstprivate)
- [lastprivate](#2723-lastprivate)
- [shared](#2724-shared)
- [default](#2725-default)
- [reduction](#2726-reduction)
- [copyin](#2727-copyin)
- [copyprivate](#2728-copyprivate)

#### <a name="2721-private"></a>2.7.2.1 private

El `private` cláusula declara las variables en la lista de variables a ser privada para cada subproceso en un equipo. La sintaxis de la `private` cláusula es como sigue:

```cpp
private(variable-list)
```

El comportamiento de una variable especificada en un `private` es la siguiente cláusula. Se asigna un nuevo objeto con una duración de almacenamiento automática para la construcción. El tamaño y la alineación del nuevo objeto se determinan por el tipo de la variable. Esta asignación se produce una vez para cada subproceso en el equipo y se invoca un constructor predeterminado para un objeto de clase si es necesario; en caso contrario, el valor inicial es indeterminado.  El objeto original al que hace referencia la variable tiene un valor indeterminado al entrar en la construcción, no se debe modificar dentro de la extensión de la construcción dinámica y tiene un valor indeterminado al salir de la construcción.

En la medida léxica de la construcción de la directiva, el nuevo objeto privado asignado por el subproceso hace referencia a la variable.

Las restricciones para el `private` cláusula son los siguientes:

- Una variable con un tipo de clase que se especifica en un `private` cláusula debe tener un constructor predeterminado accesible y no ambigua.

- Una variable especificada en un `private` cláusula no debe tener un `const`-calificado tipo a menos que tenga una clase de tipo con un `mutable` miembro.

- Una variable especificada en un `private` cláusula no debe tener un tipo incompleto ni un tipo de referencia.

- Las variables que aparecen en la `reduction` cláusula de una `parallel` directiva no se puede especificar en un `private` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.

#### <a name="2722-firstprivate"></a>2.7.2.2 firstprivate

El `firstprivate` cláusula ofrece un superconjunto de la funcionalidad proporcionada por el `private` cláusula. La sintaxis de la `firstprivate` cláusula es como sigue:

```cpp
firstprivate(variable-list)
```

Las variables especificadas en *lista de variables* tiene `private` semántica de cláusula, como se describe en [sección 2.7.2.1](#2721-private). Se produce la inicialización o la construcción como si se lleva a cabo una vez por subproceso, antes de la ejecución del subproceso de la construcción. Para un `firstprivate` cláusula en una construcción paralela, el valor inicial del nuevo objeto privado es el valor del objeto original que existe inmediatamente antes de la construcción paralela para el subproceso que se encuentra. Para un `firstprivate` cláusula en una construcción de uso compartido, el valor inicial del nuevo objeto para cada subproceso que ejecuta la construcción de uso compartido privado es el valor del objeto original que existe antes del momento dado en el mismo subproceso encuentra el construcción de uso compartido. Además, para los objetos de C++, el nuevo objeto privado para cada subproceso está copiado a partir del objeto original.

Las restricciones para el `firstprivate` cláusula son los siguientes:

- Una variable especificada en un `firstprivate` cláusula no debe tener un tipo incompleto ni un tipo de referencia.

- Una variable con un tipo de clase que se especifica como `firstprivate` debe tener un constructor de copias sea accesible y no ambigua.

- Las variables que son privadas dentro de una región paralela o que aparecen en la `reduction` cláusula de una `parallel` directiva no se puede especificar en un `firstprivate` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.

#### <a name="2723-lastprivate"></a>2.7.2.3 lastprivate

El `lastprivate` cláusula ofrece un superconjunto de la funcionalidad proporcionada por el `private` cláusula. La sintaxis de la `lastprivate` cláusula es como sigue:

```cpp
lastprivate(variable-list)
```

Las variables especificadas en el *lista de variables* tiene `private` semántica de la cláusula. Cuando un `lastprivate` cláusula aparece en la directiva que identifica una construcción de uso compartido, el valor de cada `lastprivate` variable desde la última secuencialmente iteración de bucle asociado o la directiva de léxicamente última sección, se asigna a la objeto original de la variable. Las variables que no se le asigna un valor por la última iteración de la `for` o `parallel for`, o en la sección del última léxicamente el `sections` o `parallel sections` directiva, tienen valores indeterminados después de la construcción. Sin asignar subobjetos también tienen un valor indeterminado después de la construcción.

Las restricciones para el `lastprivate` cláusula son los siguientes:

- Todas las restricciones para `private` aplicar.

- Una variable con un tipo de clase que se especifica como `lastprivate` debe tener un operador de asignación de copia accesible y no ambigua.

- Las variables que son privadas dentro de una región paralela o que aparecen en la `reduction` cláusula de una `parallel` directiva no se puede especificar en un `lastprivate` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.

#### <a name="2724-shared"></a>2.7.2.4 shared

Esta cláusula comparte las variables que aparecen en la *variable lista* entre todos los subprocesos en un equipo. Todos los subprocesos dentro de un equipo obtener acceso a la misma área de almacenamiento para `shared` variables.

La sintaxis de la `shared` cláusula es como sigue:

```cpp
shared(variable-list)
```

#### <a name="2725-default"></a>2.7.2.5 default

El `default` cláusula permite al usuario que afectan a los atributos de uso compartido de datos de variables. La sintaxis de la `default` cláusula es como sigue:

```cpp
default(shared | none)
```

Especificar `default(shared)` es equivalente a enumerar explícitamente cada variable visible actualmente en un `shared` cláusula, a menos que sea `threadprivate` o `const`-completo. En ausencia de explícita `default` cláusula, el comportamiento predeterminado es el mismo que if `default(shared)` se han especificado.

Especificar `default(none)` requiere al menos uno de los siguientes debe ser true para todas las referencias a una variable de la extensión léxica de la construcción paralela:

- La variable se muestra explícitamente en una cláusula de atributos de uso compartido de datos de una construcción que contiene la referencia.

- La variable se declara dentro de la construcción paralela.

- La variable es `threadprivate`.

- La variable tiene un `const`-calificado de tipo.

- La variable es la variable de control de bucle para un `for` bucle que sigue inmediatamente a un `for` o `parallel for` directiva y la referencia de variable aparece dentro del bucle.

Especificar una variable en un `firstprivate`, `lastprivate`, o `reduction` cláusula de una directiva delimitada hace una referencia implícita a la variable en el contexto envolvente. Estas referencias implícitas también están sujetos a los requisitos mencionados anteriormente.

Una sola `default` cláusula se puede especificar en un `parallel` directiva.

Predeterminado de una variable se puede invalidar el atributo de uso compartido de datos mediante el uso de la `private`, `firstprivate`, `lastprivate`, `reduction`, y `shared` cláusulas, como se muestra en el ejemplo siguiente:

```cpp
#pragma  omp  parallel  for  default(shared)  firstprivate(i)\
   private(x)  private(r)  lastprivate(i)
```

#### <a name="2726-reduction"></a>2.7.2.6 reduction

Esta cláusula realiza una reducción en las variables escalares que aparecen en *lista de variables*, con el operador *op*. La sintaxis de la `reduction` cláusula es como sigue:

`reduction(` *OP* `:` *lista de variables* `)`

Una reducción se suele especificar para una instrucción con una de las formas siguientes:

- *x* `=` *x* *op* *expr*
- *x* *binop* `=` *expr*
- *x* `=` *expr* *op* *x* (excepto para la resta)
- *x* `++`
- `++` *x*
- *x* `--`
- `--` *x*

donde:

*x*<br/>
Una de las variables de reducción especificadas en la lista.

*variable-list*<br/>
Una lista separada por comas de variables de reducción escalar.

*expr*<br/>
Una expresión con tipo escalar que no hace referencia a *x*.

*op*<br/>
No es un operador sobrecargado, pero uno de `+`, `*`, `-`, `&`, `^`, `|`, `&&`, o `||`.

*binop*<br/>
No es un operador sobrecargado, pero uno de `+`, `*`, `-`, `&`, `^`, o `|`.

El siguiente es un ejemplo de la `reduction` cláusula:

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

Como se muestra en el ejemplo, un operador puede estar oculto dentro de una llamada de función. El usuario debe tener cuidado de que el operador especificado en el `reduction` cláusula coincide con la operación de reducción.

Aunque el operando derecho de la `||` operador tiene efectos secundarios en este ejemplo, están permitidos, pero deben usarse con cuidado. En este contexto, puede producirse un efecto secundario que garantiza que no se producen durante la ejecución secuencial del bucle durante la ejecución en paralelo. Esta diferencia puede producirse porque el orden de ejecución de las iteraciones es indeterminado.

El operador se utiliza para determinar el valor inicial de las variables privadas utilizadas por el compilador para la reducción y determinar el operador de finalización. Especificar explícitamente el operador permite la instrucción de reducción que pueden estar fuera de la extensión de la construcción de léxica. Cualquier número de `reduction` cláusulas se pueden especificar en la directiva, pero puede aparecer una variable en a lo sumo uno `reduction` cláusula para dicha directiva.

Una copia privada de cada variable en *lista de variables* se crean, uno para cada subproceso, como si el `private` cláusula hubiese utilizada. La copia privada se inicializa según el operador (consulte la tabla siguiente).

Al final de la región para el que el `reduction` se especificó la cláusula, el objeto original se actualiza para reflejar el resultado de combinar su valor original con el valor final de cada una de las copias privadas mediante el operador especificado. Los operadores de reducción son todas asociativos (excepto para la resta), y el compilador puede reasociar libremente el cálculo del valor final. (Los resultados parciales de una reducción de la resta se suman para formar el valor final).

El valor del objeto original se convierte en indeterminado cuando el primer subproceso llega a la cláusula contenedora y permanece así hasta que finalice el cálculo de reducción.  Normalmente, el cálculo se completará al final de la construcción; Sin embargo, si la `reduction` cláusula se usa en una construcción que `nowait` es también se aplica el valor del objeto original permanece indeterminado hasta que se ha realizado una sincronización de barrera para asegurarse de que todos los subprocesos han completado la `reduction`cláusula.

En la tabla siguiente se enumera los operadores que son válidos y sus valores de inicialización canónico. El valor de inicialización real será coherente con el tipo de datos de la variable de reducción.

|Operador|Inicialización|
|--------------|--------------------|
|`+`|0|
|`*`|1|
|`-`|0|
|`&`|~0|
|`|`|0|
|`^`|0|
|`&&`|1|
|`||`|0|

Las restricciones para el `reduction` cláusula son los siguientes:

- El tipo de las variables en el `reduction` cláusula debe ser válida para el operador de reducción, salvo que nunca se permiten los tipos de puntero y tipos de referencia.

- Una variable que se especifica en el `reduction` cláusula no debe ser `const`-completo.

- Las variables que son privadas dentro de una región paralela o que aparecen en la `reduction` cláusula de una `parallel` directiva no se puede especificar en un `reduction` cláusula en una directiva de uso compartido que se enlaza a la construcción paralela.

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

El `copyin` cláusula proporciona un mecanismo para asignar el mismo valor para `threadprivate` variables para cada subproceso en el equipo de ejecución de la región paralela. Para cada variable especificada en un `copyin` cláusula, el valor de la variable en el subproceso principal del equipo de copia, como si la asignación, en las copias de subprocesos privados al principio de la región paralela. La sintaxis de la `copyin` cláusula es como sigue:

```cpp

copyin(
variable-list
)
```

Las restricciones para el `copyin` cláusula son los siguientes:

- Una variable que se especifica en el `copyin` cláusula debe tener un operador de asignación de copia accesible y no ambigua.

- Una variable que se especifica en el `copyin` cláusula debe ser un `threadprivate` variable.

#### <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

El `copyprivate` cláusula proporciona un mecanismo para usar una variable privada para difundir un valor de un miembro de un equipo a los demás miembros. Es una alternativa al uso de una variable compartida para el valor al que proporciona este tipo de variable compartida puede ser difícil (por ejemplo, en una necesidad de una variable diferente en cada nivel de recursividad). El `copyprivate` cláusula solamente puede aparecer en el `single` directiva.

La sintaxis de la `copyprivate` cláusula es como sigue:

```cpp

copyprivate(
variable-list
)
```

El efecto de la `copyprivate` cláusula en una de las variables en su lista de variables que se produce después de la ejecución del bloque estructurado asociado con el `single` construir, y antes de que cualquiera de los subprocesos en el equipo ha dejado la barrera al final de la construcción. A continuación, en todos los demás subprocesos en el equipo de cada variable en el *lista de variables*, esa variable queda definida (como si de asignación) con el valor de la correspondiente estructurado de variable en el subproceso que ejecutó la construcción bloque.

Restricciones para el `copyprivate` cláusula son los siguientes:

- Una variable que se especifica en el `copyprivate` cláusula no debe aparecer en un `private` o `firstprivate` cláusula para el mismo `single` directiva.

- Si un `single` la directiva con un `copyprivate` cláusula se encuentra en la extensión dinámica de una región paralela, todas las variables que se especifica en el `copyprivate` cláusula debe ser privada en el contexto envolvente.

- Una variable que se especifica en el `copyprivate` cláusula debe tener un operador de asignación de copia no ambigua accesible.

## <a name="28-directive-binding"></a>2.8 enlace de directivas

Enlace dinámico de directivas debe cumplir las reglas siguientes:

- El `for`, `sections`, `single`, `master`, y `barrier` directivas enlazar a la inclusión dinámicamente `parallel`, si existe alguno, independientemente del valor de cualquier `if` cláusula que puede estar presente en el que Directiva. Si no hay ninguna región paralela se está ejecutando actualmente, las directivas se ejecutan por un equipo que se compone del subproceso principal.

- El `ordered` directiva se enlaza a la inclusión dinámicamente `for`.

- El `atomic` Directiva exige acceso exclusivo con respecto a `atomic` directivas en todos los subprocesos, no solo el equipo actual.

- El `critical` Directiva exige acceso exclusivo con respecto a `critical` directivas en todos los subprocesos, no solo el equipo actual.

- Una directiva nunca puede enlazar dinámicamente a cualquier directiva fuera lo más parecido posible inclusión `parallel`.

## <a name="29-directive-nesting"></a>2.9 anidamiento de directivas

Anidamiento dinámico de directivas debe cumplir las reglas siguientes:

- Un `parallel` directiva dinámicamente dentro de otra `parallel` lógicamente establece un nuevo equipo, que se compone del subproceso actual, a menos que anidada paralelismo está habilitado.

- `for`, `sections`, y `single` directivas que se enlazan a la misma `parallel` no pueden anidarse dentro de otros.

- `critical` no pueden anidarse dentro de otras directivas con el mismo nombre. Tenga en cuenta que esta restricción no es suficiente para evitar el interbloqueo.

- `for`, `sections`, y `single` no se permiten las directivas de la extensión dinámica de `critical`, `ordered`, y `master` regiones si las directivas se enlazan a la misma `parallel` como las regiones.

- `barrier` no se permiten las directivas de la extensión dinámica de `for`, `ordered`, `sections`, `single`, `master`, y `critical` regiones si las directivas se enlazan a la misma `parallel` como las regiones.

- `master` no se permiten las directivas de la extensión dinámica de `for`, `sections`, y `single` directivas si el `master` directivas enlazar al mismo `parallel` como las directivas de uso compartido.

- `ordered` no se permiten las directivas de la extensión dinámica de `critical` regiones si las directivas se enlazan a la misma `parallel` como las regiones.

- También se permite cualquier directiva que se permite cuando se ejecuta de forma dinámica dentro de una región paralela cuando se ejecuta fuera de una región paralela. Cuando se ejecuta dinámicamente fuera de una región paralela especificada por el usuario, la directiva se ejecuta por un equipo que se compone del subproceso principal.
