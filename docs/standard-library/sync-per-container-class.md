---
title: sync_per_container (Clase) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sync_per_container
- stdext::sync_per_container
- allocators/stdext::sync_per_container
- allocators/stdext::sync_per_container::equals
dev_langs:
- C++
helpviewer_keywords:
- sync_per_container class
ms.assetid: 0b4b2904-b668-4d94-a422-d4f919cbffab
caps.latest.revision: 21
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
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
ms.openlocfilehash: 80e119d2d7ee913b691bffe6f9943a28599dc1e5
ms.contentlocale: es-es
ms.lasthandoff: 04/29/2017

---
# <a name="syncpercontainer-class"></a>sync_per_container (Clase)
Describe un [filtro de sincronización](../standard-library/allocators-header.md) que proporciona un objeto de caché independiente para cada objeto de asignador.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class Cache>  
class sync_per_container
 : public Cache
```  
  
#### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El tipo de caché asociado al filtro de sincronización. Puede ser [cache_chunklist](../standard-library/cache-chunklist-class.md), [cache_freelist](../standard-library/cache-freelist-class.md) o [cache_suballoc](../standard-library/cache-suballoc-class.md).|  
  
### <a name="member-functions"></a>Funciones miembro  
  
|||  
|-|-|  
|[equals](#equals)|Compara dos cachés para determinar si son iguales.|  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** \<allocators>  
  
 **Espacio de nombres:** stdext  
  
##  <a name="equals"></a>  sync_per_container::equals  
 Compara dos cachés para determinar si son iguales.  
  
```
bool equals(const sync_per_container<Cache>& Other) const;
```  
  
### <a name="parameters"></a>Parámetros  
  
|Parámetro|Descripción|  
|---------------|-----------------|  
|`Cache`|El objeto de caché del filtro de sincronización.|  
|`Other`|El objeto de caché para comparar la igualdad.|  
  
### <a name="return-value"></a>Valor devuelto  
 La función miembro siempre devuelve `false`.  
  
### <a name="remarks"></a>Comentarios  
  
## <a name="see-also"></a>Vea también  
 [\<allocators>](../standard-library/allocators-header.md)




