---
title: cache_chunklist (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- allocators/stdext::cache_chunklist
- allocators/stdext::cache_chunklist::allocate
- allocators/stdext::cache_chunklist::deallocate
dev_langs: C++
helpviewer_keywords:
- stdext::cache_chunklist
- stdext::cache_chunklist [C++], allocate
- stdext::cache_chunklist [C++], deallocate
ms.assetid: af19eccc-4ae7-4a34-bbb2-81e397424cb9
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 13d81e3eab6e93a138ac55ca53cbf8e61f195507
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cachechunklist-class"></a>cache_chunklist (Clase)
Define un [asignador de bloques](../standard-library/allocators-header.md) que asigna y desasigna bloques de memoria de un tamaño único.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <std::size_t Sz, std::size_t Nelts = 20>  
class cache_chunklist
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Sz`|El número de elementos de la matriz que se van a asignar.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de plantilla usa `operator new` para asignar fragmentos de memoria binaria, subasignando bloques para asignar almacenamiento para un bloque de memoria cuando sea necesario; almacena bloques de memoria desasignados en una lista libre independiente para cada fragmento y usa `operator delete` para desasignar un fragmento cuando ninguno de los bloques de memoria está en uso.  
  
 Cada bloque de memoria contiene `Sz` bytes de memoria utilizable y un puntero al fragmento al que pertenece. Cada fragmento contiene `Nelts` bloques de memoria, tres punteros, un int y los datos que requieren `operator new` y `operator delete`.  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[cache_chunklist](#cache_chunklist)|Construye un objeto de tipo `cache_chunklist`.|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[allocate](#allocate)|Asigna un bloque de memoria.|  
|[deallocate](#deallocate)|Libera un número especificado de objetos del almacenamiento, a partir de la posición especificada.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocate"></a>  cache_chunklist::allocate  
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
  
##  <a name="cache_chunklist"></a>  cache_chunklist::cache_chunklist  
 Construye un objeto de tipo `cache_chunklist`.  
  
```
cache_chunklist();
```  
  
### <a name="remarks"></a>Comentarios  
  
##  <a name="deallocate"></a>  cache_chunklist::deallocate  
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



