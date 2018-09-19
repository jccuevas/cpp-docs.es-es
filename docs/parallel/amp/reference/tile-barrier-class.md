---
title: tile_barrier (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
dev_langs:
- C++
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a91cbb816deb18d9c4cf7356faa879c09a9d276c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46025209"
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
|[Espere](#wait)|Indica a todos los subprocesos del grupo de subprocesos (mosaico) para detener la ejecución hasta que todos los subprocesos del mosaico hayan terminado de esperar.|  
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria y todos los subprocesos del mosaico hayan alcanzado esta llamada.|  
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria global y todos los subprocesos del mosaico hayan alcanzado esta llamada.|  
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos `tile_static` accesos a memoria se han completado y todos los subprocesos del mosaico hayan alcanzado esta llamada.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tile_barrier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="tile_barrier__ctor"></a>  tile_barrier (Constructor)  
 Inicializa una nueva instancia de la clase mediante la copia de uno existente.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
*_Otro*<br/>
La `tile_barrier` objeto que se va a copiar.  

## <a name="wait"></a>  Espere 
Indica a todos los subprocesos del grupo de subprocesos (mosaico) para detener la ejecución hasta que todos los subprocesos del mosaico hayan terminado de esperar.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>  wait_with_all_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria están visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden programado.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>  wait_with_global_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria globales están visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden programado.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>  wait_with_tile_static_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que `tile_static` memoria accesos son visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden programado.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
