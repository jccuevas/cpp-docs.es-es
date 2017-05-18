---
title: Clase CComAllocator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComAllocator
- ATLBASE/ATL::CComAllocator
- ATLBASE/ATL::CComAllocator::Allocate
- ATLBASE/ATL::CComAllocator::Free
- ATLBASE/ATL::CComAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComAllocator class
ms.assetid: 0cd706fd-0c7b-42d3-9054-febe2966fc8e
caps.latest.revision: 19
author: mikeblome
ms.author: mblome
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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: d395d347e81b24462a41de5ae3b9d8791d7f82fd
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="ccomallocator-class"></a>Clase CComAllocator
Esta clase proporciona métodos para administrar la memoria mediante las rutinas de memoria COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComAllocator
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComAllocator::Allocate](#allocate)|Llame a este método estático para asignar memoria.|  
|[CComAllocator::Free](#free)|Llame a este método estático para liberar la memoria asignada.|  
|[CComAllocator::Reallocate](#reallocate)|Llame a este método estático para volver a asignar memoria.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es utilizada por [plantilla CComHeapPtr](../../atl/reference/ccomheapptr-class.md) para proporcionar rutinas de asignación de memoria COM. La clase equivalente, [CCRTAllocator](../../atl/reference/ccrtallocator-class.md), proporciona los mismos métodos con rutinas de CRT.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="allocate"></a>CComAllocator::Allocate  
 Llame a esta función estática para asignar memoria.  
  
```
static void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 Número de bytes que se van a asignar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero void al espacio asignado, o NULL si no hay suficiente memoria disponible.  
  
### <a name="remarks"></a>Comentarios  
 Asigna memoria. Consulte [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727) para obtener más detalles.  
  
##  <a name="free"></a>CComAllocator::Free  
 Llame a esta función estática para liberar la memoria asignada.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria asignada.  
  
### <a name="remarks"></a>Comentarios  
 Libera la memoria asignada. Consulte [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722) para obtener más detalles.  
  
##  <a name="reallocate"></a>CComAllocator::Reallocate  
 Llame a esta función estática para reasignar memoria.  
  
```
static void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria asignada.  
  
 `nBytes`  
 El número de bytes para reasignar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero void al espacio asignado, o NULL si no hay memoria suficiente  
  
### <a name="remarks"></a>Comentarios  
 Cambia el tamaño de la cantidad de memoria asignada. Consulte [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Clase de plantilla CComHeapPtr](../../atl/reference/ccomheapptr-class.md)   
 [Clase CCRTAllocator](../../atl/reference/ccrtallocator-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

