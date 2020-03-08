---
title: 4. Variables de entorno
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: b41829fd9cf2f90312f669ef991f56dda02947f7
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882875"
---
# <a name="4-environment-variables"></a>4. variables de entorno

En este capítulo se describen las variables C++ de entorno de OpenMP C y API (o mecanismos específicos de la plataforma similares) que controlan la ejecución de código paralelo.  Los nombres de las variables de entorno deben estar en mayúsculas. Los valores asignados a ellos no distinguen mayúsculas de minúsculas y pueden tener espacios en blanco iniciales y finales.  Se omiten las modificaciones de los valores después del inicio del programa.

Las variables de entorno son las siguientes:

- [OMP_SCHEDULE](#41-omp_schedule) establece el tipo de programación en tiempo de ejecución y el tamaño del fragmento.
- [OMP_NUM_THREADS](#42-omp_num_threads) establece el número de subprocesos que se van a usar durante la ejecución.
- [OMP_DYNAMIC](#43-omp_dynamic) habilita o deshabilita el ajuste dinámico del número de subprocesos.
- [OMP_NESTED](#44-omp_nested) habilita o deshabilita el paralelismo anidado.

Los ejemplos de este capítulo solo muestran cómo estas variables se pueden establecer en entornos de Shell C de UNIX (CSH). En el shell de Korn y en los entornos de DOS, las acciones son similares:

CSH  
`setenv OMP_SCHEDULE "dynamic"`

ksh  
`export OMP_SCHEDULE="dynamic"`

AUTHIP  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a>4,1 OMP_SCHEDULE

`OMP_SCHEDULE` solo se aplica a las directivas `for` y `parallel for` que tienen el tipo de programación `runtime`. El tipo de programación y el tamaño del fragmento se pueden establecer en tiempo de ejecución. Establezca esta variable de entorno en cualquier tipo de programación reconocido y en una *chunk_size*opcional.

En el caso de las directivas `for` y `parallel for` que tienen un tipo de programación distinto de `runtime`, `OMP_SCHEDULE` se omite. El valor predeterminado de esta variable de entorno está definido por la implementación. Si se establece el *chunk_size* opcional, el valor debe ser positivo. Si no se establece *chunk_size* , se supone un valor de 1, excepto cuando se `static`la programación. En el caso de una programación de `static`, el tamaño de fragmento predeterminado se establece en el espacio de iteración del bucle dividido entre el número de subprocesos aplicados al bucle.

Ejemplo:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Referencias cruzadas

- [for](2-directives.md#241-for-construct) (Directiva)
- [Parallel for](2-directives.md#251-parallel-for-construct) (Directiva)

## <a name="42-omp_num_threads"></a>4,2 OMP_NUM_THREADS

La variable de entorno `OMP_NUM_THREADS` establece el número predeterminado de subprocesos que se van a usar durante la ejecución. `OMP_NUM_THREADS` se omite si ese número se cambia explícitamente mediante una llamada a la rutina de biblioteca de `omp_set_num_threads`. También se omite si hay una cláusula `num_threads` explícita en una directiva `parallel`.

El valor de la variable de entorno `OMP_NUM_THREADS` debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para obtener un conjunto completo de reglas sobre la interacción entre el `OMP_NUM_THREADS` variable de entorno y el ajuste dinámico de subprocesos, consulte la [sección 2,3](2-directives.md#23-parallel-construct).

El número de subprocesos que se va a usar es definido por la implementación si:

- no se ha especificado la variable de entorno `OMP_NUM_THREADS`.
- el valor especificado no es un entero positivo o
- el valor es mayor que el número máximo de subprocesos que el sistema puede admitir.

Ejemplo:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Referencias cruzadas

- cláusula [num_threads](2-directives.md#23-parallel-construct)
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) función)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) función)

## <a name="43-omp_dynamic"></a>4,3 OMP_DYNAMIC

La variable de entorno `OMP_DYNAMIC` habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de regiones paralelas. `OMP_DYNAMIC` se omite cuando el ajuste dinámico está habilitado o deshabilitado explícitamente mediante una llamada a la rutina de biblioteca de `omp_set_dynamic`. Su valor debe ser `TRUE` o `FALSE`.

Si `OMP_DYNAMIC` se establece en `TRUE`, el entorno en tiempo de ejecución puede ajustar el número de subprocesos que se usan para ejecutar regiones paralelas para usar mejor los recursos del sistema.  Si `OMP_DYNAMIC` se establece en `FALSE`, se deshabilita el ajuste dinámico. La condición predeterminada está definida por la implementación.

Ejemplo:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Referencias cruzadas

- [Regiones paralelas](2-directives.md#23-parallel-construct)
- [omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function) función)

## <a name="44-omp_nested"></a>4,4 OMP_NESTED

La variable de entorno `OMP_NESTED` habilita o deshabilita el paralelismo anidado a menos que el paralelismo anidado esté habilitado o deshabilitado mediante una llamada a la rutina de biblioteca de `omp_set_nested`. Si `OMP_NESTED` se establece en `TRUE`, se habilita el paralelismo anidado. Si `OMP_NESTED` se establece en `FALSE`, se deshabilita el paralelismo anidado. El valor predeterminado es `FALSE`.

Ejemplo:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Referencia cruzada

- [omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function) función)
