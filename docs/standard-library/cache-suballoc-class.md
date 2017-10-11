---
title: cache_suballoc (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_suballoc
- allocators/stdext::cache_suballoc::allocate
- allocators/stdext::cache_suballoc::deallocate
dev_langs:
- C++
helpviewer_keywords:
- stdext::cache_suballoc
- stdext::cache_suballoc [C++], allocate
- stdext::cache_suballoc [C++], deallocate
ms.assetid: 9ea9c5e9-1dcc-45d0-b3a7-a56a93d88898
caps.latest.revision: 17
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 65f4e356ad0d46333b0d443d0fd6ac0b9f2b6f58
ms.openlocfilehash: ab861704bfb44546a3dcb5a4a3b2f4210dbe8774
ms.contentlocale: es-es
ms.lasthandoff: 10/03/2017

---
# <a name="cachesuballoc-class"></a>cache_suballoc (Clase)
Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <std::size_t Sz, size_t Nelts = 20>  
class cache_suballoc
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se van a asignar.|  
  
## <a name="remarks"></a>Comentarios  
 La clase de plantilla cache_suballoc almacena bloques de memoria desasignados en una lista libre con longitud ilimitada, mediante `freelist<sizeof(Type), max_unbounded>`, y subasigna bloques de memoria de un fragmento mayor asignado con `operator new` cuando la lista libre está vacía.  
  
 Cada fragmento contiene `Sz * Nelts` bytes de memoria utilizable y los datos que `operator new` y `operator delete` requieren. Nunca se liberarán los fragmentos asignados.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[cache_suballoc](#cache_suballoc)|Construye un objeto de tipo `cache_suballoc`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[allocate](#allocate)|Asigna un bloque de memoria.|  
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocate"></a>  cache_suballoc::allocate  
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
  
##  <a name="cache_suballoc"></a>  cache_suballoc::cache_suballoc  
 Construye un objeto de tipo `cache_suballoc`.  
  
```
cache_suballoc();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="deallocate"></a>  cache_suballoc::deallocate  
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




