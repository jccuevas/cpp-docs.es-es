---
title: Clase max_unbounded | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::max_unbounded
- allocators/stdext::max_unbounded::allocated
- allocators/stdext::max_unbounded::deallocated
- allocators/stdext::max_unbounded::full
- allocators/stdext::max_unbounded::released
- allocators/stdext::max_unbounded::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_unbounded
- stdext::max_unbounded [C++], allocated
- stdext::max_unbounded [C++], deallocated
- stdext::max_unbounded [C++], full
- stdext::max_unbounded [C++], released
- stdext::max_unbounded [C++], saved
ms.assetid: e34627a9-c231-4031-a483-cbb0514fff46
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 96a4d8a295353f56f2c6b027f72e6353698afdf2
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="maxunbounded-class"></a>max_unbounded (Clase)
Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que no limita la longitud máxima de un objeto [freelist](../standard-library/freelist-class.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```
class max_unbounded
```  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[allocated](#allocated)|Aumenta el número de bloques de memoria asignada.|  
|[deallocated](#deallocated)|Reduce el número de bloques de memoria asignada.|  
|[full](#full)|Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.|  
|[released](#released)|Reduce el número de bloques de memoria de la lista libre.|  
|[saved](#saved)|Aumenta el número de bloques de memoria de la lista libre.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="allocated"></a>  max_unbounded::allocated  
 Aumenta el número de bloques de memoria asignada.  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Nx`|Valor de incremento.|  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no hace nada. Se llama después de cada vez que `cache_freelist::allocate` realiza una llamada correcta al operador `new`. El argumento `_Nx` es el número de bloques de memoria del fragmento asignado por el operador `new`.  
  
##  <a name="deallocated"></a>  max_unbounded::deallocated  
 Reduce el número de bloques de memoria asignada.  
  
```
void deallocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Nx`|Valor de incremento.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro no hace nada. Se llama a esta función miembro después de cada vez que `cache_freelist::deallocate` realiza una llamada al operador `delete`. El argumento `_Nx` es el número de bloques de memoria del fragmento desasignado por el operador `delete`.  
  
##  <a name="full"></a>  max_unbounded::full  
 Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro siempre devuelve `false`.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve `true`, `deallocate` coloca el bloque de memoria en la lista libre. Si devuelve False, `deallocate` llama al operador `delete` para que desasigne el bloque.  
  
##  <a name="released"></a>  max_unbounded::released  
 Reduce el número de bloques de memoria de la lista libre.  
  
```
void released();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no hace nada. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.  
  
##  <a name="saved"></a>  max_unbounded::saved  
 Aumenta el número de bloques de memoria de la lista libre.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no hace nada. Se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)



