---
title: sync_none (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::sync_none
- allocators/stdext::sync_none::allocate
- allocators/stdext::sync_none::deallocate
- allocators/stdext::sync_none::equals
dev_langs:
- C++
helpviewer_keywords:
- stdext::sync_none
- stdext::sync_none [C++], allocate
- stdext::sync_none [C++], deallocate
- stdext::sync_none [C++], equals
ms.assetid: f7473cee-14f3-4fe1-88bc-68cd085e59e1
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 6cd96ec71098bed30fdbbb0fa84cfd7e61e33a7b
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="syncnone-class"></a>sync_none (Clase)
Describe un [filtro de sincronización](../standard-library/allocators-header.md) que no proporciona ninguna sincronización.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Cache>  
class sync_none
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[allocate](#allocate)|Asigna un bloque de memoria.|  
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocate"></a>  sync_none::allocate  
 Asigna un bloque de memoria.  
  
```
void *allocate(std::size_t count);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`count`|El número de elementos de la matriz que se van a asignar.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro devuelve `cache.allocate(count)`, donde `cache` es el objeto de caché.  
  
##  <a name="deallocate"></a>  sync_none::deallocate  
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
 La función miembro llama a `cache.deallocate(ptr, count)`, donde `cache` representa el objeto de caché.  
  
##  <a name="equals"></a>  sync_none::equals  
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
 La función miembro siempre devuelve `true`.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)




