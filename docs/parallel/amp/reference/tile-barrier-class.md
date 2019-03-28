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
ms.openlocfilehash: f0e742a0cc1a0809fc08b3862cadb7e3deb36fa8
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564988"
---
# <a name="tilebarrier-class"></a>tile_barrier (Clase)

Sincroniza la ejecución de subprocesos que se ejecutan en el grupo de subprocesos (el mosaico) mediante el uso de `wait` métodos. Solo el runtime puede crear instancias de esta clase.

### <a name="syntax"></a>Sintaxis

```
class tile_barrier;
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[tile_barrier (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `tile_barrier`.|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[wait](#wait)|Indica a todos los subprocesos del grupo de subprocesos (mosaico) para detener la ejecución hasta que todos los subprocesos del mosaico hayan terminado de esperar.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria y todos los subprocesos del mosaico hayan alcanzado esta llamada.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria global y todos los subprocesos del mosaico hayan alcanzado esta llamada.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos `tile_static` accesos a memoria se han completado y todos los subprocesos del mosaico hayan alcanzado esta llamada.|

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`tile_barrier`

## <a name="requirements"></a>Requisitos

**Encabezado:** amp.h

**Espacio de nombres**: simultaneidad

## <a name="ctor"></a>  tile_barrier (Constructor)

Inicializa una nueva instancia de la clase mediante la copia de uno existente.

### <a name="syntax"></a>Sintaxis

```
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parámetros

*_Other*<br/>
La `tile_barrier` objeto que se va a copiar.

## <a name="wait"></a>Espere

Indica a todos los subprocesos del grupo de subprocesos (mosaico) para detener la ejecución hasta que todos los subprocesos del mosaico hayan terminado de esperar.

### <a name="syntax"></a>Sintaxis

```
void wait() const restrict(amp);
```

## <a name="waitwithallmemoryfence"></a>wait_with_all_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria están visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden programado.

### <a name="syntax"></a>Sintaxis

```
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="waitwithglobalmemoryfence"></a>wait_with_global_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria globales están visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden programado.

### <a name="syntax"></a>Sintaxis

```
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="waitwithtilestaticmemoryfence"></a>wait_with_tile_static_memory_fence

Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que `tile_static` memoria accesos son visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden programado.

### <a name="syntax"></a>Sintaxis

```
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Vea también

[Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
