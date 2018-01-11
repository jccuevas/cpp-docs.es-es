---
title: rts_alloc (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::rts_alloc
- allocators/stdext::rts_alloc::allocate
- allocators/stdext::rts_alloc::deallocate
- allocators/stdext::rts_alloc::equals
dev_langs: C++
helpviewer_keywords:
- stdext::rts_alloc
- stdext::rts_alloc [C++], allocate
- stdext::rts_alloc [C++], deallocate
- stdext::rts_alloc [C++], equals
ms.assetid: ab41bffa-83d1-4a1c-87b9-5707d516931f
caps.latest.revision: "19"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 2e4870edc0b54a92307ddf88d58dd96ca3fd331e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="rtsalloc-class"></a>rts_alloc (Clase)
La clase de plantilla rts_alloc describe un [filtro](../standard-library/allocators-header.md) que contiene una matriz de instancias de caché y determina la instancia que se va a usar para la asignación y la desasignación en tiempo de ejecución, y no en tiempo de compilación.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Cache>  
class rts_alloc
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de instancias de caché contenido en la matriz. Puede ser [cache_chunklist (Clase)](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md)|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de plantilla contiene varias instancias del asignador de bloques y determina la instancia que se va a usar para la asignación o desasignación en tiempo de ejecución, y no en tiempo de compilación. Se usa con los compiladores que no se pueden reenlazar mediante compilación.  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[allocate](#allocate)|Asigna un bloque de memoria.|  
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocate"></a>  rts_alloc::allocate  
 Asigna un bloque de memoria.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`count`|El número de elementos de la matriz que se van a asignar.|  
  
### <a name="return-value"></a>Valor devuelto  
 Un puntero al objeto asignado.  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `caches[_IDX].allocate(count)`, donde el índice `_IDX` viene determinado por el tamaño de bloque solicitado `count`, o bien, si `count` es demasiado grande, devuelve `operator new(count)`. `cache`, que representa el objeto de caché.  
  
##  <a name="deallocate"></a>  rts_alloc::deallocate  
 Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.  
  
```
void deallocate(void* ptr, std::size_t count);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`ptr`|Un puntero al primer objeto que se va a desasignar del almacenamiento.|  
|`count`|El número de objetos que se van a desasignar del almacenamiento.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro llama a `caches[_IDX].deallocate(ptr, count)`, donde el índice `_IDX` viene determinado por el tamaño de bloque solicitado `count`, o bien, si `count` es demasiado grande, devuelve `operator delete(ptr)`.  
  
##  <a name="equals"></a>  rts_alloc::equals  
 Compara dos cachés para determinar si son iguales.  
  
```
bool equals(const sync<_Cache>& _Other) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Cache`|El objeto de caché asociado con el filtro.|  
|`_Other`|El objeto de caché para comparar la igualdad.|  
  
### <a name="remarks"></a>Comentarios  
 `true` si el resultado de `caches[0].equals(other.caches[0])`; en caso contrario, `false`. `caches` representa la matriz de objetos de caché.  
  
## <a name="see-also"></a>Vea también  
 [ALLOCATOR_DECL](../standard-library/allocators-functions.md#allocator_decl)   
 [\<allocators>](../standard-library/allocators-header.md)



