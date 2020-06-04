---
title: tile_barrier (Clase)
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: c00f1e41e70e723be185959eeff176390def7647
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374722"
---
# <a name="tile_barrier-class"></a>tile_barrier (Clase)

Sincroniza la ejecución de subprocesos que se ejecutan en `wait` el grupo de subprocesos (el icono) mediante métodos. Solo el tiempo de ejecución puede crear instancias de esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
class tile_barrier;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor tile_barrier](#ctor)|Inicializa una nueva instancia de la clase `tile_barrier`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Esperar](#wait)|Indica a todos los subprocesos del grupo de subprocesos (teselas) que dejen de ejecutarse hasta que todos los subprocesos del icono hayan terminado de esperar.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloquea la ejecución de todos los subprocesos de un icono hasta que se hayan completado todos los accesos a la memoria y todos los subprocesos del icono hayan alcanzado esta llamada.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloquea la ejecución de todos los subprocesos de un icono hasta que se hayan completado todos los accesos de memoria global y todos los subprocesos del icono hayan alcanzado esta llamada.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloquea la ejecución de todos `tile_static` los subprocesos de un icono hasta que se hayan completado todos los accesos a la memoria y todos los subprocesos del icono hayan alcanzado esta llamada.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tile_barrier`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrencia

## <a name="tile_barrier-constructor"></a><a name="ctor"></a>Constructor tile_barrier

Inicializa una nueva instancia de la clase copiando una existente.

### <a name="syntax"></a>Sintaxis

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
El objeto `tile_barrier` que se va a copiar.

## <a name="wait"></a>wait

Indica a todos los subprocesos del grupo de subprocesos (teselas) que detengan la ejecución hasta que todos los subprocesos del icono hayan terminado de esperar.

### <a name="syntax"></a>Sintaxis

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a><a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Bloquea la ejecución de todos los subprocesos de un icono hasta que todos los subprocesos de un icono han alcanzado esta llamada. Esto garantiza que todos los accesos a la memoria sean visibles para otros subprocesos en el icono de subproceso y se hayan ejecutado en orden de programa.

### <a name="syntax"></a>Sintaxis

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence">wait_with_global_memory_fence

Bloquea la ejecución de todos los subprocesos de un icono hasta que todos los subprocesos de un icono han alcanzado esta llamada. Esto garantiza que todos los accesos a memoria global sean visibles para otros subprocesos en el icono de subproceso y se hayan ejecutado en orden de programa.

### <a name="syntax"></a>Sintaxis

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence">wait_with_tile_static_memory_fence

Bloquea la ejecución de todos los subprocesos de un icono hasta que todos los subprocesos de un icono han alcanzado esta llamada. Esto garantiza `tile_static` que los accesos a la memoria sean visibles para otros subprocesos en el icono de subproceso y se hayan ejecutado en orden de programa.

### <a name="syntax"></a>Sintaxis

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
