---
title: Clase max_fixed_size | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- allocators/stdext::max_fixed_size
- allocators/stdext::max_fixed_size::allocated
- allocators/stdext::max_fixed_size::deallocated
- allocators/stdext::max_fixed_size::full
- allocators/stdext::max_fixed_size::released
- allocators/stdext::max_fixed_size::saved
dev_langs:
- C++
helpviewer_keywords:
- stdext::max_fixed_size
- stdext::max_fixed_size [C++], allocated
- stdext::max_fixed_size [C++], deallocated
- stdext::max_fixed_size [C++], full
- stdext::max_fixed_size [C++], released
- stdext::max_fixed_size [C++], saved
ms.assetid: 8c8f4588-37e9-4579-8168-ba3553800914
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6476e3e6ce9c08501be598facbc29b4a55386834
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="maxfixedsize-class"></a>max_fixed_size (Clase)
Describe un objeto de [clase máxima](../standard-library/allocators-header.md) que limita un objeto [freelist](../standard-library/freelist-class.md) a una longitud máxima fija.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <std::size_t Max>  
class max_fixed_size
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Max`|Clase máxima que determina el número máximo de elementos que se van a almacenar en `freelist`.|  
  
### <a name="constructors"></a>Constructores  
  
|||  
|-|-|  
|[max_fixed_size](#max_fixed_size)|Construye un objeto de tipo `max_fixed_size`.|  
  
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
  
##  <a name="allocated"></a>  max_fixed_size::allocated  
 Aumenta el número de bloques de memoria asignada.  
  
```
void allocated(std::size_t _Nx = 1);
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`_Nx`|Valor de incremento.|  
  
### <a name="remarks"></a>Comentarios  
 La función miembro no hace nada. Se llama a esta función miembro después de cada vez que `cache_freelist::allocate` realiza una llamada correcta al operador `new`. El argumento `_Nx` es el número de bloques de memoria del fragmento asignado por el operador `new`.  
  
##  <a name="deallocated"></a>  max_fixed_size::deallocated  
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
  
##  <a name="full"></a>  max_fixed_size::full  
 Devuelve un valor que especifica si se deben agregar más bloques de memoria a la lista libre.  
  
```
bool full();
```  
  
### <a name="return-value"></a>Valor devuelto  
 `true` si `Max <= _Nblocks`; de lo contrario, `false`.  
  
### <a name="remarks"></a>Comentarios  
 Se llama a esta función miembro mediante `cache_freelist::deallocate`. Si la llamada devuelve `true`, `deallocate` coloca el bloque de memoria en la lista libre. Si devuelve False, `deallocate` llama al operador `delete` para que desasigne el bloque.  
  
##  <a name="max_fixed_size"></a>  max_fixed_size::max_fixed_size  
 Construye un objeto de tipo `max_fixed_size`.  
  
```
max_fixed_size();
```  
  
### <a name="remarks"></a>Comentarios  
 Este constructor inicializa el valor almacenado `_Nblocks` en cero.  
  
##  <a name="released"></a>  max_fixed_size::released  
 Reduce el número de bloques de memoria de la lista libre.  
  
```
void released();
```  
  
### <a name="remarks"></a>Comentarios  
 Disminuye el valor almacenado `_Nblocks`. La función miembro `released` de la [clase máxima](../standard-library/allocators-header.md) actual se llama mediante `cache_freelist::allocate` cada vez que quita un bloque de memoria de la lista libre.  
  
##  <a name="saved"></a>  max_fixed_size::saved  
 Aumenta el número de bloques de memoria de la lista libre.  
  
```
void saved();
```  
  
### <a name="remarks"></a>Comentarios  
 Esta función miembro aumenta el valor almacenado `_Nblocks`. Esta función miembro se llama mediante `cache_freelist::deallocate` cada vez que coloca un bloque de memoria en la lista libre.  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)



