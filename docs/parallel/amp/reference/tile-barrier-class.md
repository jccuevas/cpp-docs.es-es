---
title: tile_barrier (clase) | Documentos de Microsoft
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
ms.openlocfilehash: 62e81b7cab8d7e8774e6ac50c5de5f256d76b232
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686495"
---
# <a name="tilebarrier-class"></a>tile_barrier (Clase)
Sincroniza la ejecución de subprocesos que se ejecutan en el grupo de subprocesos (el mosaico) mediante el uso de `wait` métodos. Solo el tiempo de ejecución puede crear instancias de esta clase.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[tile_barrier Constructor](#ctor)|Inicializa una nueva instancia de la clase `tile_barrier`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[espera](#wait)|Indica a todos los subprocesos en el grupo de subprocesos (mosaico) para detener la ejecución hasta que todos los subprocesos del mosaico finaliza la espera.|  
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Bloquea la ejecución de todos los subprocesos en el icono y que todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria ha alcanzado esta llamada.|  
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria global y todos los subprocesos del mosaico han alcanzado esta llamada.|  
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los `tile_static` accesos a memoria que se ha completado y todos los subprocesos del mosaico han alcanzado esta llamada.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tile_barrier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="tile_barrier__ctor"></a>  tile_barrier Constructor  
 Inicializa una nueva instancia de la clase copiando uno ya existente.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `tile_barrier` objeto que se va a copiar.  

## <a name="wait"></a>  espera 
Indica a todos los subprocesos en el grupo de subprocesos (mosaico) para detener la ejecución hasta que todos los subprocesos del mosaico finaliza la espera.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>  wait_with_all_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico han alcanzado esta llamada. Esto garantiza que todos los accesos de memoria son visibles para otros subprocesos en el icono de subproceso y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>  wait_with_global_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico han alcanzado esta llamada. Esto garantiza que todos los accesos de memoria global están visibles para otros subprocesos en el icono de subproceso y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>  wait_with_tile_static_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico han alcanzado esta llamada. Esto garantiza que `tile_static` memoria accesos están visibles para otros subprocesos en el icono de subproceso y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)
