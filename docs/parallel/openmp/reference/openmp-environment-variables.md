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
ms.openlocfilehash: 73fb11db14df22e5df95fdec556ccdfc16a935e5
ms.sourcegitcommit: 14b292596bc9b9b883a9c58cd3e366b282a1f7b3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2019
ms.locfileid: "60124972"
---
# <a name="openmp-environment-variables"></a>Variables de entorno de OpenMP

Proporciona vínculos a las variables de entorno que se utilizan en la API de OpenMP.

La implementación de Visual C++ del estándar OpenMP incluye las siguientes variables de entorno. Estas variables de entorno se leen al inicio del programa y se omiten las modificaciones en sus valores en tiempo de ejecución (por ejemplo, mediante [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

|Variable de entorno|Descripción|
|--------------------|-----------|
|[OMP_SCHEDULE](#omp-schedule)|Modifica el comportamiento de la [programación](openmp-clauses.md#schedule) cláusula cuando `schedule(runtime)` se especifica en un `for` o `parallel for` directiva.|
|[OMP_NUM_THREADS](#omp-num-threads)|Establece el número máximo de subprocesos en la región paralela, a menos que se reemplaza por [omp_set_num_threads ()](openmp-functions.md#omp-set-num-threads) o [num_threads](openmp-clauses.md#num-threads).|
|[OMP_DYNAMIC](#omp-dynamic)|Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.|
|[OMP_NESTED](#omp-nested)|Especifica si está habilitado paralelismo anidado, a menos que está habilitado o deshabilitado con paralelismo anidado `omp_set_nested`.|

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Comentarios

El `OMP_DYNAMIC` variable de entorno puede reemplazarse por la [omp_set_dynamic ()](openmp-functions.md#omp-set-dynamic) función.

El valor predeterminado de la implementación de Visual C++ del estándar OpenMP es `OMP_DYNAMIC=FALSE`.

Para obtener más información, consulte [OMP_DYNAMIC 4.3](../../../parallel/openmp/4-3-omp-dynamic.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la `OMP_DYNAMIC` variable de entorno en TRUE:

```
set OMP_DYNAMIC=TRUE
```

El comando siguiente muestra la configuración actual de la `OMP_DYNAMIC` variable de entorno:

```
set OMP_DYNAMIC
```

## <a name="omp-nested"></a>OMP_NESTED

Especifica si está habilitado paralelismo anidado, a menos que está habilitado o deshabilitado con paralelismo anidado `omp_set_nested`.

```
set OMP_NESTED[=TRUE | =FALSE]
```

### <a name="remarks"></a>Comentarios

El `OMP_NESTED` variable de entorno puede reemplazarse por la [omp_set_nested ()](openmp-functions.md#omp-set-nested) función.

El valor predeterminado de la implementación de Visual C++ del estándar OpenMP es `OMP_DYNAMIC=FALSE`.

Para obtener más información, consulte [OMP_NESTED 4.4](../../../parallel/openmp/4-4-omp-nested.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la `OMP_NESTED` variable de entorno en TRUE:

```
set OMP_NESTED=TRUE
```

El comando siguiente muestra la configuración actual de la `OMP_NESTED` variable de entorno:

```
set OMP_NESTED
```

## <a name="omp-num-threads"></a>OMP_NUM_THREADS

Establece el número máximo de subprocesos en la región paralela, a menos que se reemplaza por [omp_set_num_threads ()](openmp-functions.md#omp-set-num-threads) o [num_threads](openmp-clauses.md#num-threads).

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parámetros

*num*<br/>
El número máximo de subprocesos que desee en la región paralela, hasta 64 en la implementación de Visual C++.

### <a name="remarks"></a>Comentarios

El `OMP_NUM_THREADS` variable de entorno puede reemplazarse por la [omp_set_num_threads ()](openmp-functions.md#omp-set-num-threads) función o por [num_threads](openmp-clauses.md#num-threads).

El valor predeterminado de `num` en Visual C++ implementación del estándar OpenMP es el número de procesadores virtuales, incluidas las CPU de hyperthreading.

Para obtener más información, consulte [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la `OMP_NUM_THREADS` variable de entorno `16`:

```
set OMP_NUM_THREADS=16
```

El comando siguiente muestra la configuración actual de la `OMP_NUM_THREADS` variable de entorno:

```
set OMP_NUM_THREADS
```

## <a name="omp-schedule"></a>OMP_SCHEDULE

Modifica el comportamiento de la [programación](openmp-clauses.md#schedule) cláusula cuando `schedule(runtime)` se especifica en un `for` o `parallel for` directiva.

```
set OMP_SCHEDULE[=type[,size]]
```

### <a name="parameters"></a>Parámetros

*size*<br/>
(Opcional) Especifica el tamaño de las iteraciones. *tamaño* debe ser un entero positivo. El valor predeterminado es `1`, salvo cuando *tipo* es estático. No es válido cuando *tipo* es `runtime`.

*type*<br/>
El tipo de programación, ya sea `dynamic`, `guided`, `runtime`, o `static`.

### <a name="remarks"></a>Comentarios

El valor predeterminado de la implementación de Visual C++ del estándar OpenMP es `OMP_SCHEDULE=static,0`.

Para obtener más información, consulte [OMP_SCHEDULE 4.1](../../../parallel/openmp/4-1-omp-schedule.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la `OMP_SCHEDULE` variable de entorno:

```
set OMP_SCHEDULE="guided,2"
```

El comando siguiente muestra la configuración actual de la `OMP_SCHEDULE` variable de entorno:

```
set OMP_SCHEDULE
```
