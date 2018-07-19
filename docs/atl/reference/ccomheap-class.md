---
title: CComHeap (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComHeap
- ATLCOMMEM/ATL::CComHeap
- ATLCOMMEM/ATL::CComHeap::Allocate
- ATLCOMMEM/ATL::CComHeap::Free
- ATLCOMMEM/ATL::CComHeap::GetSize
- ATLCOMMEM/ATL::CComHeap::Reallocate
dev_langs:
- C++
helpviewer_keywords:
- CComHeap class
ms.assetid: c74183ce-98ae-46fb-b186-93ea4cf0222b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d45a999f777a2d497542544c2d3c7f079b7a32b0
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881609"
---
# <a name="ccomheap-class"></a>CComHeap (clase)
Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación de memoria COM.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CComHeap : public IAtlMemMgr
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CComHeap::Allocate](#allocate)|Llame a este método para asignar un bloque de memoria.|  
|[Ccomheap:: Free](#free)|Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.|  
|[CComHeap::GetSize](#getsize)|Llame a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.|  
|[Ccomheap:: ReAllocate](#reallocate)|Llame a este método para reasignar la memoria asignada por este administrador de memoria.|  
  
## <a name="remarks"></a>Comentarios  
 `CComHeap` implementa funciones de asignación de memoria mediante las funciones de asignación COM, incluidos [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727), [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722), [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226)y [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280). La cantidad máxima de memoria que se puede asignar es igual a bytes INT_MAX (2147483647).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CComHeap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ATLComMem.h  
  
##  <a name="allocate"></a>  CComHeap::Allocate  
 Llame a este método para asignar un bloque de memoria.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *nBytes*  
 Número de bytes solicitado en el nuevo bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al principio del bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [ccomheap:: Free](#free) o [ccomheap:: ReAllocate](#reallocate) para liberar la memoria asignada por este método.  
  
 Implementa mediante [CoTaskMemAlloc](http://msdn.microsoft.com/library/windows/desktop/ms692727).  
  
##  <a name="free"></a>  Ccomheap:: Free  
 Llame a este método para liberar un bloque de memoria asignada por este administrador de memoria.  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 Puntero a la memoria previamente asignada por este administrador de memoria. NULL es un valor válido y no hace nada.  
  
### <a name="remarks"></a>Comentarios  
 Implementa mediante [CoTaskMemFree](http://msdn.microsoft.com/library/windows/desktop/ms680722).  
  
##  <a name="getsize"></a>  CComHeap::GetSize  
 Llame a este método para obtener el tamaño de un bloque de memoria asignado por este administrador de memoria asignado.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 Puntero a la memoria previamente asignada por este administrador de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño del bloque de memoria asignada en bytes.  
  
### <a name="remarks"></a>Comentarios  
 Implementa mediante [IMalloc::GetSize](http://msdn.microsoft.com/library/windows/desktop/ms691226).  
  
##  <a name="reallocate"></a>  Ccomheap:: ReAllocate  
 Llame a este método para reasignar la memoria asignada por este administrador de memoria.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *p*  
 Puntero a la memoria previamente asignada por este administrador de memoria.  
  
 *nBytes*  
 Número de bytes solicitado en el nuevo bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al principio del bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [ccomheap:: Free](#free) para liberar la memoria asignada por este método.  
  
 Implementa mediante [CoTaskMemRealloc](http://msdn.microsoft.com/library/windows/desktop/ms687280).  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo DynamicConsumer](../../visual-cpp-samples.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clase de CWin32Heap](../../atl/reference/cwin32heap-class.md)   
 [CLocalHeap (clase)](../../atl/reference/clocalheap-class.md)   
 [CGlobalHeap (clase)](../../atl/reference/cglobalheap-class.md)   
 [CCRTHeap (clase)](../../atl/reference/ccrtheap-class.md)   
 [IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)
