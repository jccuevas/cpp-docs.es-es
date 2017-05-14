---
title: sync_shared (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sync_shared
- allocators/stdext::sync_shared
- stdext::sync_shared
- allocators/stdext::sync_shared::allocate
- allocators/stdext::sync_shared::deallocate
- allocators/stdext::sync_shared::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_shared class
ms.assetid: cab3af9e-3d1a-4f2c-8580-0f89e5687d8e
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: d3cfcde97a0f6c89b1f18c4026c6ab49db66fd96
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="syncshared-class"></a>sync_shared (Clase)
Describe un [filtro de sincronización](../standard-library/allocators-header.md) que usa una exclusión mutua para controlar el acceso a un objeto de caché compartido por todos los asignadores.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Cache>  
class sync_shared
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
  
##  <a name="allocate"></a>  sync_shared::allocate  
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
 La función miembro bloquea la exclusión mutua, llama a `cache.allocate(count)`, desbloquea la exclusión mutua y devuelve el resultado de la llamada anterior a `cache.allocate(count)`. `cache` representa el objeto de caché actual.  
  
##  <a name="deallocate"></a>  sync_shared::deallocate  
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
 Esta función miembro bloquea la exclusión mutua, llama a `cache.deallocate(ptr, count)`, donde `cache` representa el objeto de caché y, después, desbloquea la exclusión mutua.  
  
##  <a name="equals"></a>  sync_shared::equals  
 Compara dos cachés para determinar si son iguales.  
  
```
bool equals(const sync_shared<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización.|  
|`Other`|La caché para comparar la igualdad.|  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si el resultado de `cache.equals(Other.cache)`, donde `cache` representa el objeto de caché, en `true`. De lo contrario, es `false`.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)




