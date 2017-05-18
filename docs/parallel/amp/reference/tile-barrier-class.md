---
title: tile_barrier (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 17
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a82768750e6a7837bb81edd8a51847f83c294c20
ms.openlocfilehash: 4bacc84c4e267ffca14290186750ae1d3bdf899f
ms.contentlocale: es-es
ms.lasthandoff: 04/04/2017

---
# <a name="tilebarrier-class"></a>tile_barrier (Clase)
Sincroniza la ejecución de subprocesos que se ejecutan en el grupo de subprocesos (el mosaico) mediante el uso de `wait` métodos. Solo el tiempo de ejecución puede crear instancias de esta clase.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[tile_barrier Constructor](#ctor)|Inicializa una nueva instancia de la clase `tile_barrier`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
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

## <a name="tile_barrier__ctor"></a>tile_barrier Constructor  
 Inicializa una nueva instancia de la clase copiando uno ya existente.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `tile_barrier` objeto que se va a copiar.  

## <a name="wait"></a>espera 
Indica a todos los subprocesos en el grupo de subprocesos (mosaico) para detener la ejecución hasta que todos los subprocesos del mosaico finaliza la espera.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait() const restrict(amp);  
```    

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico han alcanzado esta llamada. Esto garantiza que todos los accesos de memoria son visibles para otros subprocesos en el icono de subproceso y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="wait_with_global_memory_fence"></a>wait_with_global_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico han alcanzado esta llamada. Esto garantiza que todos los accesos de memoria global están visibles para otros subprocesos en el icono de subproceso y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="wait_with_tile_static_memory_fence"></a>wait_with_tile_static_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico han alcanzado esta llamada. Esto garantiza que `tile_static` memoria accesos están visibles para otros subprocesos en el icono de subproceso y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>Vea también  
 [Espacio de nombres de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

