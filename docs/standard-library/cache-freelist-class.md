---
title: cache_freelist (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_freelist
- allocators/stdext::cache_freelist::allocate
- allocators/stdext::cache_freelist::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_freelist
- stdext::cache_freelist [C++], allocate
- stdext::cache_freelist [C++], deallocate
ms.assetid: 840694de-36ba-470f-8dae-2b723d5a8cd9
caps.latest.revision: 19
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: 53a5913390b0fb08912560672f8fead9f59c829f
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="cachefreelist-class"></a>cache_freelist (Clase)
Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <std::size_t Sz, class Max>  
class cache_freelist
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se van a asignar.|  
|`Max`|La clase máxima que representa el tamaño máximo de la lista libre. Esta puede ser [max_fixed_size](../standard-library/max-fixed-size-class.md), [max_none](../standard-library/max-none-class.md), [max_unbounded](../standard-library/max-unbounded-class.md) o [max_variable_size](../standard-library/max-variable-size-class.md).|  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla cache_freelist mantiene una lista libre de bloques de memoria de tamaño `Sz`. Cuando la lista libre está llena, usa `operator delete` para desasignar bloques de memoria. Cuando la lista libre está vacía, usa `operator new` para asignar nuevos bloques de memoria. El tamaño máximo de la lista libre viene determinado por la clase máxima que se ha pasado en el parámetro `Max`.  
  
 Cada bloque de memoria contiene `Sz` bytes de memoria utilizable y los datos que `operator new` y `operator delete` requieren.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[cache_freelist](#cache_freelist)|Construye un objeto de tipo `cache_freelist`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[allocate](#allocate)|Asigna un bloque de memoria.|  
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocate"></a>  cache_freelist::allocate  
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
  
##  <a name="cache_freelist"></a>  cache_freelist::cache_freelist  
 Construye un objeto de tipo `cache_freelist`.  
  
```
cache_freelist();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="deallocate"></a>  cache_freelist::deallocate  
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
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)




