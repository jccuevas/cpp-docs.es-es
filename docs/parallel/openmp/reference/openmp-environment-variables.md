---
title: Variables de entorno de OpenMP
ms.date: 03/20/2019
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
ms.openlocfilehash: bee9b0fbdf147ee962ff92d0b3b9ff57d4209f84
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363883"
---
# <a name="openmp-environment-variables"></a>Variables de entorno de OpenMP

Proporciona vínculos a variables de entorno utilizadas en la API de OpenMP.

La implementación de Visual C++ del estándar OpenMP incluye las siguientes variables de entorno. Estas variables de entorno se leen al inicio del programa y las modificaciones de sus valores se omiten en tiempo de ejecución (por ejemplo, mediante [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Variable de entorno|Descripción|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modifica el comportamiento [schedule](openmp-clauses.md#schedule) de la `schedule(runtime)` cláusula schedule `for` cuando `parallel for` se especifica en una directiva o.|
|[OMP_NUM_THREADS](#omp-num-threads)|Establece el número máximo de subprocesos en la región paralela, a menos que se invalide por [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) o [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.|
|[OMP_NESTED](#omp-nested)|Especifica si el paralelismo anidado está habilitado, a menos `omp_set_nested`que el paralelismo anidado esté habilitado o deshabilitado con .|

## <a name="omp_dynamic"></a><a name="omp-dynamic"></a>OMP_DYNAMIC

Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Observaciones

La `OMP_DYNAMIC` variable de entorno se puede invalidar mediante la función [omp_set_dynamic.](openmp-functions.md#omp-set-dynamic)

El valor predeterminado en la implementación de Visual `OMP_DYNAMIC=FALSE`C++ del estándar OpenMP es .

Para obtener más información, consulte [4.3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Ejemplo

El siguiente comando `OMP_DYNAMIC` establece la variable de entorno en TRUE:

```cmd
set OMP_DYNAMIC=TRUE
```

El siguiente comando muestra la `OMP_DYNAMIC` configuración actual de la variable de entorno:

```cmd
set OMP_DYNAMIC
```

## <a name="omp_nested"></a><a name="omp-nested"></a>OMP_NESTED

Especifica si el paralelismo anidado está habilitado, a menos `omp_set_nested`que el paralelismo anidado esté habilitado o deshabilitado con .

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Observaciones

La `OMP_NESTED` variable de entorno se puede invalidar mediante la función [omp_set_nested.](openmp-functions.md#omp-set-nested)

El valor predeterminado en la implementación de Visual `OMP_DYNAMIC=FALSE`C++ del estándar OpenMP es .

Para obtener más información, consulte [4.4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Ejemplo

El siguiente comando `OMP_NESTED` establece la variable de entorno en TRUE:

```cmd
set OMP_NESTED=TRUE
```

El siguiente comando muestra la `OMP_NESTED` configuración actual de la variable de entorno:

```cmd
set OMP_NESTED
```

## <a name="omp_num_threads"></a><a name="omp-num-threads"></a>OMP_NUM_THREADS

Establece el número máximo de subprocesos en la región paralela, a menos que se invalide por [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) o [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parámetros

*num*<br/>
El número máximo de subprocesos que desea en la región paralela, hasta 64 en la implementación de Visual C++.

### <a name="remarks"></a>Observaciones

La `OMP_NUM_THREADS` variable de entorno se puede invalidar mediante la función [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) o por [num_threads](openmp-clauses.md#num-threads).

El valor `num` predeterminado de la implementación de Visual C++ del estándar OpenMP es el número de procesadores virtuales, incluidas las CPU de hiperproceso.

Para obtener más información, consulte [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Ejemplo

El siguiente comando `OMP_NUM_THREADS` establece `16`la variable de entorno en:

```cmd
set OMP_NUM_THREADS=16
```

El siguiente comando muestra la `OMP_NUM_THREADS` configuración actual de la variable de entorno:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp_schedule"></a><a name="omp-schedule"></a>OMP_SCHEDULE

Modifica el comportamiento [schedule](openmp-clauses.md#schedule) de la `schedule(runtime)` cláusula schedule `for` cuando `parallel for` se especifica en una directiva o.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parámetros

*Tamaño*<br/>
(Opcional) Especifica el tamaño de las iteraciones. *tamaño* debe ser un entero positivo. El valor `1`predeterminado es , excepto cuando *type* es static. No es válido `runtime`cuando el *tipo* es .

*type*<br/>
El tipo de `dynamic`programación, ya sea , `guided`, `runtime`, o `static`.

### <a name="remarks"></a>Observaciones

El valor predeterminado en la implementación de Visual `OMP_SCHEDULE=static,0`C++ del estándar OpenMP es .

Para obtener más información, consulte [4.1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Ejemplo

El siguiente comando `OMP_SCHEDULE` establece la variable de entorno:

```cmd
set OMP_SCHEDULE="guided,2"
```

El siguiente comando muestra la `OMP_SCHEDULE` configuración actual de la variable de entorno:

```cmd
set OMP_SCHEDULE
```
