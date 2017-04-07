---
title: Clase CCRTAllocator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 5154a095409705e96dee6f52c67d7c23b0e6691f
ms.lasthandoff: 02/24/2017

---
# <a name="ccrtallocator-class"></a>Clase CCRTAllocator
Esta clase proporciona métodos para administrar la memoria mediante las rutinas de memoria de CRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class ATL::CCRTAllocator
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CCRTAllocator::Allocate](#allocate)|(Estático) Llamar a este método para asignar memoria.|  
|[CCRTAllocator::Free](#free)|(Estático) Llamar a este método para liberar memoria.|  
|[CCRTAllocator::Reallocate](#reallocate)|(Estático) Llamar a este método para volver a asignar memoria.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase es utilizada por [CHeapPtr](../../atl/reference/cheapptr-class.md) para proporcionar rutinas de asignación de la memoria de CRT. La clase equivalente, [CComAllocator](../../atl/reference/ccomallocator-class.md), proporciona los mismos métodos mediante rutinas COM.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="allocate"></a>CCRTAllocator::Allocate  
 Llame a esta función estática para asignar memoria.  
  
```
static __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 Número de bytes que se van a asignar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero void al espacio asignado, o NULL si no hay suficiente memoria disponible.  
  
### <a name="remarks"></a>Comentarios  
 Asigna memoria. Consulte [malloc](../../c-runtime-library/reference/malloc.md) para obtener más detalles.  
  
##  <a name="free"></a>CCRTAllocator::Free  
 Llame a esta función para liberar la memoria estática.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria asignada.  
  
### <a name="remarks"></a>Comentarios  
 Libera la memoria asignada. Consulte [libre](../../c-runtime-library/reference/free.md) para obtener más detalles.  
  
##  <a name="reallocate"></a>CCRTAllocator::Reallocate  
 Llame a esta función estática para reasignar memoria.  
  
```
static __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria asignada.  
  
 `nBytes`  
 El número de bytes para reasignar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero void al espacio asignado o NULL si no hay memoria suficiente.  
  
### <a name="remarks"></a>Comentarios  
 Cambia el tamaño de la cantidad de memoria asignada. Consulte [realloc](../../c-runtime-library/reference/realloc.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Clase CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Clase CComAllocator](../../atl/reference/ccomallocator-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

