---
title: 4. Variables de entorno
ms.date: 01/16/2019
ms.assetid: 4ec7ed81-e9ca-46a1-84f8-8f9ce4587346
ms.openlocfilehash: e93c59654c17ed6dbfb7483ac2dce716ce24b52a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370264"
---
# <a name="4-environment-variables"></a>4. Variables de entorno

En este capítulo se describen las variables de entorno de API de OpenMP C y C++ (o mecanismos específicos de plataforma similares) que controlan la ejecución de código paralelo.  Los nombres de las variables de entorno deben estar en mayúsculas. Los valores asignados a ellos no distinguen mayúsculas de minúsculas y pueden tener espacios en blanco iniciales y finales.  Se omiten las modificaciones de los valores después de que se haya iniciado el programa.

Las variables de entorno son las siguientes:

- [OMP_SCHEDULE](#41-omp_schedule) establece el tipo de programación en tiempo de ejecución y el tamaño del fragmento.
- [OMP_NUM_THREADS](#42-omp_num_threads) establece el número de subprocesos que se van a utilizar durante la ejecución.
- [OMP_DYNAMIC](#43-omp_dynamic) habilita o deshabilita el ajuste dinámico del número de subprocesos.
- [OMP_NESTED](#44-omp_nested) habilita o deshabilita el paralelismo anidado.

Los ejemplos de este capítulo solo muestran cómo se pueden establecer estas variables en entornos de shell de Unix C (csh). En los entornos de shell Korn y DOS, las acciones son similares:

Csh:  
`setenv OMP_SCHEDULE "dynamic"`

Ksh:  
`export OMP_SCHEDULE="dynamic"`

DOS:  
`set OMP_SCHEDULE="dynamic"`

## <a name="41-omp_schedule"></a><a name="41-omp_schedule"></a>4.1 OMP_SCHEDULE

`OMP_SCHEDULE`se aplica `for` `parallel for` únicamente a las `runtime`directivas y directivas que tienen el tipo de programación. El tipo de programación y el tamaño del fragmento para todos estos bucles se pueden establecer en tiempo de ejecución. Establezca esta variable de entorno en cualquier tipo de programación reconocido y en un *chunk_size*opcional.

Se `for` `parallel for` omite For y las directivas que tienen un tipo de programación distinto de `runtime`, `OMP_SCHEDULE` . El valor predeterminado de esta variable de entorno está definido por la implementación. Si se establece el *chunk_size* opcional, el valor debe ser positivo. Si no se establece *chunk_size,* se asume un valor `static`de 1, excepto cuando la programación es . Para `static` una programación, el tamaño de fragmento predeterminado se establece en el espacio de iteración del bucle dividido por el número de subprocesos aplicados al bucle.

Ejemplo:

```csh
setenv OMP_SCHEDULE "guided,4"
setenv OMP_SCHEDULE "dynamic"
```

### <a name="cross-references"></a>Referencias cruzadas

- [para](2-directives.md#241-for-construct) la directiva
- [paralelo para la](2-directives.md#251-parallel-for-construct) directiva

## <a name="42-omp_num_threads"></a><a name="42-omp_num_threads"></a>4.2 OMP_NUM_THREADS

La `OMP_NUM_THREADS` variable de entorno establece el número predeterminado de subprocesos que se van a utilizar durante la ejecución. `OMP_NUM_THREADS`se omite si ese número se `omp_set_num_threads` cambia explícitamente llamando a la rutina de biblioteca. También se omite si hay una `num_threads` cláusula `parallel` explícita en una directiva.

El valor `OMP_NUM_THREADS` de la variable de entorno debe ser un entero positivo. Su efecto depende de si está habilitado el ajuste dinámico del número de subprocesos. Para obtener un conjunto completo de `OMP_NUM_THREADS` reglas sobre la interacción entre la variable de entorno y el ajuste dinámico de subprocesos, consulte [la sección 2.3](2-directives.md#23-parallel-construct).

El número de subprocesos que se van a utilizar está definido por la implementación si:

- no `OMP_NUM_THREADS` se especifica la variable de entorno,
- el valor especificado no es un entero positivo, o
- el valor es mayor que el número máximo de subprocesos que el sistema puede admitir.

Ejemplo:

```csh
setenv OMP_NUM_THREADS 16
```

### <a name="cross-references"></a>Referencias cruzadas

- [cláusula num_threads](2-directives.md#23-parallel-construct)
- [omp_set_num_threads](3-run-time-library-functions.md#311-omp_set_num_threads-function) función
- [función omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)

## <a name="43-omp_dynamic"></a><a name="43-omp_dynamic"></a>4.3 OMP_DYNAMIC

La `OMP_DYNAMIC` variable de entorno habilita o deshabilita el ajuste dinámico del número de subprocesos disponibles para la ejecución de regiones paralelas. `OMP_DYNAMIC`se omite cuando el ajuste dinámico se habilita `omp_set_dynamic` o deshabilita explícitamente llamando a la rutina de biblioteca. Su valor `TRUE` debe `FALSE`ser o .

Si `OMP_DYNAMIC` se `TRUE`establece en , el entorno de tiempo de ejecución puede ajustar el número de subprocesos que se utilizan para ejecutar regiones paralelas para utilizar mejor los recursos del sistema.  Si `OMP_DYNAMIC` se `FALSE`establece en , el ajuste dinámico está deshabilitado. La condición predeterminada está definida por la implementación.

Ejemplo:

```csh
setenv OMP_DYNAMIC TRUE
```

### <a name="cross-references"></a>Referencias cruzadas

- [Regiones paralelas](2-directives.md#23-parallel-construct)
- [función omp_set_dynamic](3-run-time-library-functions.md#317-omp_set_dynamic-function)

## <a name="44-omp_nested"></a><a name="44-omp_nested"></a>4.4 OMP_NESTED

La `OMP_NESTED` variable de entorno habilita o deshabilita el paralelismo anidado a `omp_set_nested` menos que se habilite o deshabilite el paralelismo anidado llamando a la rutina de biblioteca. Si `OMP_NESTED` se `TRUE`establece en , se habilita el paralelismo anidado. Si `OMP_NESTED` se `FALSE`establece en , el paralelismo anidado está deshabilitado. El valor predeterminado es `FALSE`.

Ejemplo:

```csh
setenv OMP_NESTED TRUE
```

### <a name="cross-reference"></a>Referencia cruzada

- [función omp_set_nested](3-run-time-library-functions.md#319-omp_set_nested-function)
