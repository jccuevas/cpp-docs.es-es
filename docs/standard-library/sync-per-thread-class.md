---
title: sync_per_thread (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_per_thread
- allocators/stdext::sync_per_thread::allocate
- allocators/stdext::sync_per_thread::deallocate
- allocators/stdext::sync_per_thread::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_per_thread
- stdext::sync_per_thread [C++], allocate
- stdext::sync_per_thread [C++], deallocate
- stdext::sync_per_thread [C++], equals
ms.assetid: 47bf75f8-5b02-4760-b1d3-3099d08fe14c
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 817f52e11a39de64288c4433b5f29c48ae45ca22
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="syncperthread-class"></a>sync_per_thread (Clase)
Describe un [filtro de sincronización](../standard-library/allocators-header.md) que proporciona un objeto de caché independiente para cada subproceso.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Cache>  
class sync_per_thread
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|  
  
## <a name="remarks"></a>Comentarios  
 Los asignadores que usan `sync_per_thread` pueden ser iguales, aunque no se puede cancelar la asignación de bloques asignados en un subproceso desde otro subproceso. Cuando se usa uno de estos asignadores, los bloques de memoria asignados en un subproceso no deberían ser visibles para otros subprocesos. En la práctica, esto significa que un contenedor que usa uno de estos asignadores solo puede estar disponible para el acceso para un único subproceso.  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[allocate](#allocate)|Asigna un bloque de memoria.|  
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocate"></a>  sync_per_thread::allocate  
 Asigna un bloque de memoria.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`count`|El número de elementos de la matriz que se van a asignar.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve el resultado de una llamada a `cache::allocate(count)` en el objeto de caché que pertenece al subproceso actual. Si no se asignó ningún objeto de caché para el subproceso actual, primero asigna uno.  
  
##  <a name="deallocate"></a>  sync_per_thread::deallocate  
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
 La función miembro llama a `deallocate` en el objeto de caché que pertenece al subproceso actual. Si no se asignó ningún objeto de caché para el subproceso actual, primero asigna uno.  
  
##  <a name="equals"></a>  sync_per_thread::equals  
 Compara dos cachés para determinar si son iguales.  
  
```
bool equals(const sync<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El objeto de caché del filtro de sincronización.|  
|`Other`|El objeto de caché para comparar la igualdad.|  
  
### <a name="return-value"></a>Valor devuelto  
 `false` si no se asignó ningún objeto de caché para este objeto o para `Other` en el subproceso actual. De lo contrario, devuelve el resultado de aplicar `operator==` a los dos objetos de caché.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)




