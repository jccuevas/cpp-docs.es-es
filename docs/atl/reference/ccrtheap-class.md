---
title: Clase CCRTHeap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CCRTHeap
- ATLMEM/ATL::CCRTHeap
- ATLMEM/ATL::CCRTHeap::Allocate
- ATLMEM/ATL::CCRTHeap::Free
- ATLMEM/ATL::CCRTHeap::GetSize
- ATLMEM/ATL::CCRTHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CCRTHeap class
ms.assetid: 321bd6c5-1856-4ff7-8590-95044a1209f7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9864ce3522cf33927a3f6d3572e9d2e12187f5d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="ccrtheap-class"></a>Clase CCRTHeap
Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón de CRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CCRTHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[Ccrtheap:: Allocate](#allocate)|Llame a este método para asignar un bloque de memoria.|  
|[Ccrtheap:: Free](#free)|Llamar a este método para liberar un bloque de memoria asignada por este administrador de memoria.|  
|[CCRTHeap::GetSize](#getsize)|Llamar a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.|  
|[Ccrtheap:: ReAllocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|  
  
## <a name="remarks"></a>Comentarios  
 `CCRTHeap`implementa las funciones de asignación, el uso de CRT funciones, incluidas en el montón de memoria [malloc](../../c-runtime-library/reference/malloc.md), [libre](../../c-runtime-library/reference/free.md), [realloc](../../c-runtime-library/reference/realloc.md), y [_msize](../../c-runtime-library/reference/msize.md).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CCRTHeap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlmem.h  
  
##  <a name="allocate"></a>Ccrtheap:: Allocate  
 Llame a este método para asignar un bloque de memoria.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 Número de bytes solicitado en el nuevo bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al principio del bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [ccrtheap:: Free](#free) o [ccrtheap:: ReAllocate](#reallocate) para liberar la memoria asignada por este método.  
  
 Implementado mediante [malloc](../../c-runtime-library/reference/malloc.md).  
  
##  <a name="free"></a>Ccrtheap:: Free  
 Llamar a este método para liberar un bloque de memoria asignada por este administrador de memoria.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.  
  
### <a name="remarks"></a>Comentarios  
 Implementado mediante [libre](../../c-runtime-library/reference/free.md).  
  
##  <a name="getsize"></a>CCRTHeap::GetSize  
 Llamar a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria previamente asignada por este administrador de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño del bloque de memoria asignada en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Implementado mediante [_msize](../../c-runtime-library/reference/msize.md).  
  
##  <a name="reallocate"></a>Ccrtheap:: ReAllocate  
 Llame a este método para reasignar la memoria asignada por este administrador de memoria.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria previamente asignada por este administrador de memoria.  
  
 `nBytes`  
 Número de bytes solicitado en el nuevo bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al principio del bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [ccrtheap:: Free](#free) para liberar la memoria asignada por este método. Implementado mediante [realloc](../../c-runtime-library/reference/realloc.md).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clase CComHeap](../../atl/reference/ccomheap-class.md)   
 [Clase de CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Clase CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Clase CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)
