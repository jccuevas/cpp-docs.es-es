---
title: tile_barrier (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- amp/Concurrency::tile_barrier
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
translationtype: Machine Translation
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: 7ace6bb366881f9e5a9678b3a005f3079542c9cd
ms.lasthandoff: 02/24/2017

---
# <a name="tilebarrier-class"></a>tile_barrier (Clase)
Sincroniza la ejecución de subprocesos que se ejecutan en el grupo de subprocesos (mosaico) mediante el uso de `wait` métodos. Sólo el tiempo de ejecución puede crear instancias de esta clase.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
class tile_barrier;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[tile_barrier (Constructor)](#ctor)|Inicializa una nueva instancia de la clase `tile_barrier`.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Wait (método)](#wait)|Indica a todos los subprocesos en el grupo de subprocesos (mosaico) para detener la ejecución hasta que han terminado todos los subprocesos del mosaico de espera.|  
|[wait_with_all_memory_fence (método)](#wait_with_all_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria y todos los subprocesos del mosaico ha llegado esta llamada.|  
|[wait_with_global_memory_fence (método)](#wait_with_global_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que se hayan completado todos los accesos de memoria global y todos los subprocesos del mosaico han alcanzado esta llamada.|  
|[wait_with_tile_static_memory_fence (método)](#wait_with_tile_static_memory_fence)|Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los `tile_static` accesos a memoria se ha completado y todos los subprocesos del mosaico han alcanzado esta llamada.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `tile_barrier`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** amp.h  
  
 **Espacio de nombres:** Concurrency  

## <a name="a-nametilebarrierctora--tilebarrier-constructor"></a><a name="tile_barrier__ctor"></a>tile_barrier (Constructor)  
 Inicializa una nueva instancia de la clase copiando una existente.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
tile_barrier(  
    const tile_barrier& _Other ) restrict(amp,cpu);  
```  
  
### <a name="parameters"></a>Parámetros  
 `_Other`  
 La `tile_barrier` objeto que se va a copiar.  

## <a name="a-namewaita--wait"></a><a name="wait"></a>esperar 
Indica a todos los subprocesos en el grupo de subprocesos (mosaico) para detener la ejecución hasta que han terminado todos los subprocesos del mosaico de espera.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait() const restrict(amp);  
```    

## <a name="a-namewaitwithallmemoryfencea--waitwithallmemoryfence"></a><a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria son visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_all_memory_fence() const restrict(amp);  
```  
  

## <a name="a-namewaitwithglobalmemoryfencea--waitwithglobalmemoryfence"></a><a name="wait_with_global_memory_fence"></a>wait_with_global_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que todos los accesos de memoria global están visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_global_memory_fence() const  restrict(amp);  
```

## <a name="a-namewaitwithtilestaticmemoryfencea--waitwithtilestaticmemoryfence"></a><a name="wait_with_tile_static_memory_fence"></a>wait_with_tile_static_memory_fence   
Bloquea la ejecución de todos los subprocesos de un mosaico hasta que todos los subprocesos de un mosaico hayan alcanzado esta llamada. Esto garantiza que `tile_static`memoria accesos son visibles para otros subprocesos del mosaico de subprocesos y se han ejecutado en el orden del programa.  
  
### <a name="syntax"></a>Sintaxis 
  
```  
void wait_with_tile_static_memory_fence() const restrict(amp);  
```  
  
## <a name="see-also"></a>Vea también  
 [Namespace de simultaneidad (C++ AMP)](concurrency-namespace-cpp-amp.md)

