---
title: Clase CGlobalHeap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CGlobalHeap
- ATLMEM/ATL::CGlobalHeap
- ATLMEM/ATL::CGlobalHeap::Allocate
- ATLMEM/ATL::CGlobalHeap::Free
- ATLMEM/ATL::CGlobalHeap::GetSize
- ATLMEM/ATL::CGlobalHeap::Reallocate
dev_langs: C++
helpviewer_keywords: CGlobalHeap class
ms.assetid: e348d838-3aa7-4bee-a1b3-cd000c99f834
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 693a0ce139c35b804325e9ef5dcb7beb1e4da6a1
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="cglobalheap-class"></a>Clase CGlobalHeap
Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones del montón global Win32.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CGlobalHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Cglobalheap:: Allocate](#allocate)|Llame a este método para asignar un bloque de memoria.|  
|[Cglobalheap:: Free](#free)|Llamar a este método para liberar un bloque de memoria asignada por este administrador de memoria.|  
|[CGlobalHeap::GetSize](#getsize)|Llamar a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.|  
|[Cglobalheap:: ReAllocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|  
  
## <a name="remarks"></a>Comentarios  
 `CGlobalHeap`implementa las funciones de asignación de memoria mediante las funciones del montón global Win32.  
  
> [!NOTE]
>  Las funciones del montón global son más lentas que otras funciones de administración de memoria y no proporcionan tantas características. Por lo tanto, las aplicaciones nuevas deben utilizar el [funciones del montón](http://msdn.microsoft.com/library/windows/desktop/aa366711). Están disponibles en la [CWin32Heap](../../atl/reference/cwin32heap-class.md) clase. Funciones globales todavía se utilizan por DDE y las funciones del Portapapeles.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CGlobalHeap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlmem.h  
  
##  <a name="allocate"></a>Cglobalheap:: Allocate  
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
 Llame a [cglobalheap:: Free](#free) o [cglobalheap:: ReAllocate](#reallocate) para liberar la memoria asignada por este método.  
  
 Implementado mediante [GlobalAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366574) con un parámetro de marca de **GMEM_FIXED**.  
  
##  <a name="free"></a>Cglobalheap:: Free  
 Llamar a este método para liberar un bloque de memoria asignada por este administrador de memoria.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.  
  
### <a name="remarks"></a>Comentarios  
 Implementado mediante [GlobalFree](http://msdn.microsoft.com/library/windows/desktop/aa366579).  
  
##  <a name="getsize"></a>CGlobalHeap::GetSize  
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
 Implementado mediante [GlobalSize](http://msdn.microsoft.com/library/windows/desktop/aa366593).  
  
##  <a name="reallocate"></a>Cglobalheap:: ReAllocate  
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
 Llame a [cglobalheap:: Free](#free) para liberar la memoria asignada por este método.  
  
 Implementado mediante [GlobalReAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366590).  
  
## <a name="see-also"></a>Vea también  
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clase CComHeap](../../atl/reference/ccomheap-class.md)   
 [Clase de CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [Clase CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Clase CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)
