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
ms.openlocfilehash: 838427320fcb68cedb97b36156fc18002ed962d8
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78882924"
---
# <a name="openmp-environment-variables"></a>Variables de entorno de OpenMP

Proporciona vínculos a las variables de entorno que se utilizan en la API de OpenMP.

La implementación C++ visual del estándar de OpenMP incluye las siguientes variables de entorno. Estas variables de entorno se leen en el inicio del programa y las modificaciones de sus valores se omiten en tiempo de ejecución (por ejemplo, mediante [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Variable de entorno|Descripción|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modifica el comportamiento de la cláusula [Schedule](openmp-clauses.md#schedule) cuando se especifica `schedule(runtime)` en una directiva `for` o `parallel for`.|
|[OMP_NUM_THREADS](#omp-num-threads)|Establece el número máximo de subprocesos de la región paralela, a menos que se invalide por [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) o [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos de una región paralela.|
|[OMP_NESTED](#omp-nested)|Especifica si está habilitado el paralelismo anidado, a menos que el paralelismo anidado esté habilitado o deshabilitado con `omp_set_nested`.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos de una región paralela.

```cmd
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Observaciones

La función [omp_set_dynamic](openmp-functions.md#omp-set-dynamic) puede invalidar la variable de entorno `OMP_DYNAMIC`.

El valor predeterminado de la implementación C++ visual del estándar de OpenMP es `OMP_DYNAMIC=FALSE`.

Para obtener más información, consulte [4,3 OMP_DYNAMIC](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la variable de entorno `OMP_DYNAMIC` en TRUE:

```cmd
set OMP_DYNAMIC=TRUE
```

El siguiente comando muestra la configuración actual de la variable de entorno `OMP_DYNAMIC`:

```cmd
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Especifica si está habilitado el paralelismo anidado, a menos que el paralelismo anidado esté habilitado o deshabilitado con `omp_set_nested`.

```cmd
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Observaciones

La función [omp_set_nested](openmp-functions.md#omp-set-nested) puede invalidar la variable de entorno `OMP_NESTED`.

El valor predeterminado de la implementación C++ visual del estándar de OpenMP es `OMP_DYNAMIC=FALSE`.

Para obtener más información, consulte [4,4 OMP_NESTED](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la variable de entorno `OMP_NESTED` en TRUE:

```cmd
set OMP_NESTED=TRUE
```

El siguiente comando muestra la configuración actual de la variable de entorno `OMP_NESTED`:

```cmd
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Establece el número máximo de subprocesos de la región paralela, a menos que se invalide por [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) o [num_threads](openmp-clauses.md#num-threads).

```cmd
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parámetros

*num*<br/>
El número máximo de subprocesos que desea en la región paralela, hasta 64 en la C++ implementación visual.

### <a name="remarks"></a>Observaciones

La función [omp_set_num_threads](openmp-functions.md#omp-set-num-threads) o [num_threads](openmp-clauses.md#num-threads)puede invalidar la variable de entorno `OMP_NUM_THREADS`.

El valor predeterminado de `num` en la implementación C++ visual del estándar de OpenMP es el número de procesadores virtuales, incluidas las CPU de hiperthreading.

Para obtener más información, consulte [4,2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la variable de entorno `OMP_NUM_THREADS` en `16`:

```cmd
set OMP_NUM_THREADS=16
```

El siguiente comando muestra la configuración actual de la variable de entorno `OMP_NUM_THREADS`:

```cmd
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Modifica el comportamiento de la cláusula [Schedule](openmp-clauses.md#schedule) cuando se especifica `schedule(runtime)` en una directiva `for` o `parallel for`.

```cmd
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parámetros

*size*<br/>
Opta Especifica el tamaño de las iteraciones. *el tamaño* debe ser un entero positivo. El valor predeterminado es `1`, excepto cuando el *tipo* es estático. No es válido cuando el *tipo* es `runtime`.

*type*<br/>
El tipo de programación, ya sea `dynamic`, `guided`, `runtime`o `static`.

### <a name="remarks"></a>Observaciones

El valor predeterminado de la implementación C++ visual del estándar de OpenMP es `OMP_SCHEDULE=static,0`.

Para obtener más información, consulte [4,1 OMP_SCHEDULE](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la variable de entorno `OMP_SCHEDULE`:

```cmd
set OMP_SCHEDULE="guided,2"
```

El siguiente comando muestra la configuración actual de la variable de entorno `OMP_SCHEDULE`:

```cmd
set OMP_SCHEDULE
```
