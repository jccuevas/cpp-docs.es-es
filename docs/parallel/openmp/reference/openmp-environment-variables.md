---
title: Las Variables de entorno de OpenMP | Microsoft Docs
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP environment variables
- OMP_DYNAMIC
- OMP_NESTED
- OMP_NUM_THREADS
- OMP_SCHEDULE
dev_langs:
- C++
helpviewer_keywords:
- OpenMP environment variables
- OMP_DYNAMIC OpenMP environment variable
- OMP_NESTED OpenMP environment variable
- OMP_NUM_THREADS OpenMP environment variable
- OMP_SCHEDULE OpenMP environment variable
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 395494431c3942832a64cf64c9c150f643389062
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990235"
---
# <a name="openmp-environment-variables"></a>Variables de entorno de OpenMP

Proporciona vínculos a las variables de entorno que se utilizan en la API de OpenMP.

La implementación de Visual C++ del estándar OpenMP incluye las siguientes variables de entorno. Estas variables de entorno se leen al inicio del programa y se omiten las modificaciones en sus valores en tiempo de ejecución (por ejemplo, mediante [_putenv, _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)).

Variable de entorno                | Descripción
----------------------------------- | -----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[OMP_DYNAMIC](#omp-dynamic)         | Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.
[OMP_NESTED](#omp-nested)           | Especifica si está habilitado paralelismo anidado, a menos que está habilitado o deshabilitado con paralelismo anidado `omp_set_nested`.
[OMP_NUM_THREADS](#omp-num-threads) | Establece el número máximo de subprocesos en la región paralela, a menos que se reemplaza por [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) o [num_threads](openmp-clauses.md#num-threads).
[OMP_SCHEDULE](#omp-schedule)       | Modifica el comportamiento de la [programación](openmp-clauses.md#schedule) cláusula cuando `schedule(runtime)` se especifica en un `for` o `parallel for` directiva.

## <a name="omp-dynamic"></a>OMP_DYNAMIC

Especifica si el tiempo de ejecución de OpenMP puede ajustar el número de subprocesos en una región paralela.

```
set OMP_DYNAMIC[=TRUE | =FALSE]
```

### <a name="remarks"></a>Comentarios

El `OMP_DYNAMIC` variable de entorno puede reemplazarse por la [omp_set_dynamic ()](../../../parallel/openmp/reference/omp-set-dynamic.md) función.

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

El `OMP_NESTED` variable de entorno puede reemplazarse por la [omp_set_nested ()](../../../parallel/openmp/reference/omp-set-nested.md) función.

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

Establece el número máximo de subprocesos en la región paralela, a menos que se reemplaza por [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) o [num_threads](openmp-clauses.md#num-threads).

```
set OMP_NUM_THREADS[=num]
```

### <a name="parameters"></a>Parámetros

*num*<br/>
El número máximo de subprocesos que desee en la región paralela, hasta 64 en la implementación de Visual C++.

### <a name="remarks"></a>Comentarios

El `OMP_NUM_THREADS` variable de entorno puede reemplazarse por la [omp_set_num_threads ()](../../../parallel/openmp/reference/omp-set-num-threads.md) función o por [num_threads](openmp-clauses.md#num-threads).

El valor predeterminado de `num` en Visual C++ implementación del estándar OpenMP es el número de procesadores virtuales, incluidas las CPU de hyperthreading.

Para obtener más información, consulte [4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md).

### <a name="example"></a>Ejemplo

El comando siguiente establece la `OMP_NUM_THREADS` variable de entorno a 16:

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
(Opcional) Especifica el tamaño de las iteraciones. `size` Debe ser un entero positivo. El valor predeterminado es 1, excepto cuando `type` es estático. No es válido cuando `type` es `runtime`.

*type*<br/>
El tipo de programación:

- `dynamic`
- `guided`
- `runtime`
- `static`

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
