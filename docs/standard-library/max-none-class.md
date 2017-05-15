---
title: Clase max_none | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- max_none
- stdext::max_none
- allocators/stdext::max_none
- allocators/stdext::max_none::allocated
- allocators/stdext::max_none::deallocated
- allocators/stdext::max_none::full
- allocators/stdext::max_none::released
- allocators/stdext::max_none::saved
dev_langs:
- C++
helpviewer_keywords:
- max_none class
ms.assetid: 12ab5376-412e-479c-86dc-2c3d6a3559b6
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
ms.openlocfilehash: a8d3380f89f3bd25be0c23e719dfa94df5539ae4
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="maxnone-class"></a>max_none (Clase)
Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima de cero.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <std::size_t Max>  
class max_none
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Max`|Clase máxima que determina el número máximo de elementos que se van a almacenar en `freelist`.|  
  
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
  
##  <a name="allocated"></a>  max_none::allocated  
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
  
##  <a name="deallocated"></a>  max_none::deallocated  
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
  
##  <a name="full"></a>  max_none::full  
 Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Esta función miembro siempre devuelve `true`.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve `true`, `deallocate` coloca el bloque de memoria en la lista libre. Si devuelve False, `deallocate` llama al operador `delete` para que desasigne el bloque.  
  
##  <a name="released"></a>  max_none::released  
 Reduce el número de bloques de memoria de la lista libre.  
  
```
void released();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no hace nada. La función miembro `released` de la clase máxima actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.  
  
##  <a name="saved"></a>  max_none::saved  
 Aumenta el número de bloques de memoria de la lista libre.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro no hace nada. Se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)




