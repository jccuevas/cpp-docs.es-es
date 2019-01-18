---
title: 4. Variables de entorno
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: 5d08031c252d1f3c45fc45c021d24476b393fe33
ms.sourcegitcommit: 2ebbf8093fadb9a1b78a4381439bcd5c01a89267
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/18/2019
ms.locfileid: "54397334"
---
# <a name="4-environment-variables"></a>4. Variables de entorno

Este capítulo describe las variables de entorno de OpenMP C y C++ API (o mecanismos específicos de la plataforma similares) que controlan la ejecución de código paralelo.  Los nombres de variables de entorno deben estar en mayúsculas. Los valores asignados a ellos distinguen mayúsculas de minúsculas y pueden tener espacios en blanco iniciales y finales.  Se omiten las modificaciones en los valores de una vez iniciado el programa.

Las variables de entorno son los siguientes:

- [OMP_SCHEDULE](#41-omp_schedule) establece el tamaño de tipo y el fragmento de la programación de tiempo de ejecución.
- [OMP_NUM_THREADS](#42-omp_num_threads) establece el número de subprocesos que se utilizarán durante la ejecución.
- [OMP_DYNAMIC](#43-omp_dynamic) habilita o deshabilita el ajuste dinámico del número de subprocesos.
- [OMP_NESTED](#44-omp_nested) habilita o deshabilita el paralelismo anidado.

Los ejemplos de este capítulo solo muestran cómo se pueden establecer estas variables en entornos de shell (csh) de C Unix. En el shell de Korn y entornos de denegación de servicio, las acciones son similares:

csh:  
`setenv OMP_SCHEDULE "dynamic"`

ksh:  
`export OMP_SCHEDULE="dynamic"`

DENEGACIÓN DE SERVICIO:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-ompschedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE` solo se aplica a `for` y `parallel for` directivas que tienen el tipo de programación `runtime`. El tamaño de tipo y el fragmento de programación para todos los bucles de este tipo se puede establecer en tiempo de ejecución. Establezca esta variable de entorno para cualquier tipo de programación reconocido y opcional *chunk_size*.

Para `for` y `parallel for` directivas que tienen un tipo de programación distinto `runtime`, `OMP_SCHEDULE` se omite. El valor predeterminado de esta variable de entorno es definido por la implementación. Si el elemento opcional *chunk_size* se establece, el valor debe ser positivo. Si *chunk_size* no se ha establecido, se supone que un valor de 1, excepto cuando la programación está `static`. Para un `static` programación, el tamaño del fragmento predeterminado se establece en el espacio de iteración del bucle dividido por el número de subprocesos que se aplica al bucle.

Ejemplo:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Referencias cruzadas

- [para](2-4-1-for-construct.md) directiva
- [paralelo para](2-5-1-parallel-for-construct.md) directiva

## <a name="42-ompnumthreads"></a>4.2 OMP_NUM_THREADS

El `OMP_NUM_THREADS` variable de entorno establece el número predeterminado de subprocesos que se utilizarán durante la ejecución. `OMP_NUM_THREADS` se omite si dicho número se cambia explícitamente mediante una llamada a la `omp_set_num_threads` rutina de biblioteca. También se omite si no hay explícita `num_threads` cláusula en una `parallel` directiva.

El valor de la `OMP_NUM_THREADS` variable de entorno debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para un conjunto completo de reglas sobre la interacción entre el `OMP_NUM_THREADS` entorno ajuste dinámico y variable de subprocesos, vea la sección 2.3.

El número de subprocesos que desea utilizar está definido por la implementación si:

- el `OMP_NUM_THREADS` no se especifica la variable de entorno,
- el valor especificado no es un entero positivo, o
- el valor es mayor que el número máximo de subprocesos que puede admitir el sistema.

Ejemplo:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Referencias cruzadas

- [num_threads](2-3-parallel-construct.md) cláusula
- [omp_set_num_threads ()](3-1-1-omp-set-num-threads-function.md) (función)
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md) function

## <a name="43-ompdynamic"></a>4.3 OMP_DYNAMIC

El `OMP_DYNAMIC` variable de entorno se habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de las regiones en paralelo. `OMP_DYNAMIC` se omite al realizar un ajuste dinámico explícitamente está habilitado o deshabilitado mediante una llamada a la `omp_set_dynamic` rutina de biblioteca. Su valor debe ser `TRUE` o `FALSE`.

Si `OMP_DYNAMIC` está establecido en `TRUE`, el número de subprocesos que se utilizan para la ejecución de regiones en paralelo puede ser ajustado por el entorno en tiempo de ejecución son los mejores usos de los recursos del sistema.  Si `OMP_DYNAMIC` está establecido en `FALSE`, realizar un ajuste dinámico está deshabilitado. La condición predeterminada es definido por la implementación.

Ejemplo:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Referencias cruzadas

- [Regiones en paralelo](2-3-parallel-construct.md)
- [omp_set_dynamic](3-1-7-omp-set-dynamic-function.md) function

## <a name="44-ompnested"></a>4.4 OMP_NESTED

El `OMP_NESTED` variable de entorno habilita o deshabilita el paralelismo anidado a menos que el paralelismo anidado está habilitado o deshabilitado mediante una llamada a la `omp_set_nested` rutina de biblioteca. Si `OMP_NESTED` está establecido en `TRUE`, se habilita el paralelismo anidado. Si `OMP_NESTED` está establecido en `FALSE`anidado paralelismo está deshabilitado. El valor predeterminado es `FALSE`.

Ejemplo:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Referencia cruzada

- [omp_set_nested ()](3-1-9-omp-set-nested-function.md) (función)
