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
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855927"
---
# <a name="tile_barrier-class"></a>tile_barrier (Clase)

Sincroniza la ejecución de subprocesos que se están ejecutando en el grupo de subprocesos (el icono) mediante métodos de `wait`. Solo el runtime puede crear instancias de esta clase.

## <a name="syntax"></a>Sintaxis

```cpp
class tile_barrier;
```

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[Constructor de tile_barrier](#ctor)|Inicializa una nueva instancia de la clase `tile_barrier`.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[currir](#wait)|Indica a todos los subprocesos del grupo de subprocesos (mosaico) que dejen de ejecutarse hasta que todos los subprocesos del mosaico hayan terminado de esperar.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a memoria y todos los subprocesos del mosaico hayan alcanzado esta llamada.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos a la memoria global y todos los subprocesos del mosaico hayan alcanzado esta llamada.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos `tile_static` memoria y todos los subprocesos del mosaico hayan alcanzado esta llamada.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tile_barrier`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres:** Concurrency

## <a name="ctor"></a>Constructor de tile_barrier

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

Indica a todos los subprocesos del grupo de subprocesos (mosaico) que detengan la ejecución hasta que todos los subprocesos del mosaico hayan terminado de esperar.

### <a name="syntax"></a>Sintaxis

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria están visibles para otros subprocesos en el mosaico de subprocesos y que se han ejecutado en el orden del programa.

### <a name="syntax"></a>Sintaxis

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria globales están visibles para otros subprocesos del mosaico de subprocesos y que se han ejecutado en el orden del programa.

### <a name="syntax"></a>Sintaxis

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que los accesos de memoria `tile_static` estén visibles para otros subprocesos en el mosaico de subprocesos y se hayan ejecutado en el orden del programa.

### <a name="syntax"></a>Sintaxis

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Consulte también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
