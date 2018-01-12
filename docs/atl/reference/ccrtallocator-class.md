---
title: Clase CCRTAllocator | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTAllocator
- ATLCORE/ATL::CCRTAllocator
- ATLCORE/ATL::CCRTAllocator::Allocate
- ATLCORE/ATL::CCRTAllocator::Free
- ATLCORE/ATL::CCRTAllocator::Reallocate
dev_langs: C++
helpviewer_keywords: CCRTAllocator class
ms.assetid: 3e1b8cb0-859a-41ab-8e93-6f0b5ceca49d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 84c8f800e0b68e23fe33ca0a7e1c1d977bcc344e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccrtallocator-class"></a>CCRTAllocator (clase)
Esta clase proporciona métodos para administrar la memoria con rutinas de memoria de CRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class ATL::CCRTAllocator
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Ccrtallocator:: Allocate](#allocate)|(Estático) Llamar a este método para asignar memoria.|  
|[Ccrtallocator:: Free](#free)|(Estático) Llamar a este método para liberar memoria.|  
|[Ccrtallocator:: ReAllocate](#reallocate)|(Estático) Llamar a este método para volver a asignar memoria.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase se utiliza por [CHeapPtr](../../atl/reference/cheapptr-class.md) para proporcionar rutinas de asignación de la memoria de CRT. La clase equivalente, [CComAllocator](../../atl/reference/ccomallocator-class.md), proporciona los mismos métodos de usar las rutinas de COM.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="allocate"></a>Ccrtallocator:: Allocate  
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
 Asigna memoria. Vea [malloc](../../c-runtime-library/reference/malloc.md) para obtener más detalles.  
  
##  <a name="free"></a>Ccrtallocator:: Free  
 Llame a esta función estática para liberar memoria.  
  
```
static void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria asignada.  
  
### <a name="remarks"></a>Comentarios  
 Libera la memoria asignada. Vea [libre](../../c-runtime-library/reference/free.md) para obtener más detalles.  
  
##  <a name="reallocate"></a>Ccrtallocator:: ReAllocate  
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
 Cambia el tamaño de la cantidad de memoria asignada. Vea [realloc](../../c-runtime-library/reference/realloc.md) para obtener más detalles.  
  
## <a name="see-also"></a>Vea también  
 [Clase CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Clase CComAllocator](../../atl/reference/ccomallocator-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
