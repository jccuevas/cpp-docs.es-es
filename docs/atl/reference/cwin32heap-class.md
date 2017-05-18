---
title: Clase CWin32Heap | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CWin32Heap
- ATLMEM/ATL::CWin32Heap
- ATLMEM/ATL::CWin32Heap::CWin32Heap
- ATLMEM/ATL::CWin32Heap::Allocate
- ATLMEM/ATL::CWin32Heap::Attach
- ATLMEM/ATL::CWin32Heap::Detach
- ATLMEM/ATL::CWin32Heap::Free
- ATLMEM/ATL::CWin32Heap::GetSize
- ATLMEM/ATL::CWin32Heap::Reallocate
- ATLMEM/ATL::CWin32Heap::m_bOwnHeap
- ATLMEM/ATL::CWin32Heap::m_hHeap
dev_langs:
- C++
helpviewer_keywords:
- CWin32Heap class
ms.assetid: 69176022-ed98-4e3b-96d8-116b0c58ac95
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 407f777b52529a333251c7d00481fdbfb14db619
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="cwin32heap-class"></a>Clase CWin32Heap
Esta clase implementa [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md) mediante las funciones de asignación del montón de Win32.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CWin32Heap : public IAtlMemMgr
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWin32Heap::CWin32Heap](#cwin32heap)|El constructor.|  
|[CWin32Heap:: ~ CWin32Heap](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWin32Heap::Allocate](#allocate)|Asigna un bloque de memoria del objeto de montón.|  
|[CWin32Heap:: Attach](#attach)|El objeto del montón se asocia a un montón existente.|  
|[CWin32Heap::Detach](#detach)|Desasocia el objeto en el montón de un montón existente.|  
|[CWin32Heap::Free](#free)|Libera memoria previamente asignada desde el montón.|  
|[CWin32Heap::GetSize](#getsize)|Devuelve el tamaño de un bloque de memoria asignado desde el objeto del montón.|  
|[CWin32Heap::Reallocate](#reallocate)|Reasigna un bloque de memoria del objeto de montón.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CWin32Heap::m_bOwnHeap](#m_bownheap)|Un indicador que se utiliza para determinar la propiedad actual del identificador de montón.|  
|[CWin32Heap::m_hHeap](#m_hheap)|Identificador del objeto de montón.|  
  
## <a name="remarks"></a>Comentarios  
 `CWin32Heap`implementa los métodos de asignación de memoria mediante las funciones de asignación del montón de Win32, incluyendo [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597) y [HeapFree](http://msdn.microsoft.com/library/windows/desktop/aa366701). A diferencia de otras clases de montón `CWin32Heap` requiere proporcionar antes de que la memoria se asigna un identificador de montón válido: la otra clases utilizan de forma predeterminada el montón del proceso. El identificador se puede proporcionar al constructor o a la [CWin32Heap:: Attach](#attach) método. Consulte la [CWin32Heap::CWin32Heap](#cwin32heap) método para obtener más detalles.  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [IAtlMemMgr](../../atl/reference/iatlmemmgr-class.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `IAtlMemMgr`  
  
 `CWin32Heap`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlmem.h  
  
##  <a name="allocate"></a>CWin32Heap::Allocate  
 Asigna un bloque de memoria del objeto de montón.  
  
```
virtual __declspec(allocator) void* Allocate(size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `nBytes`  
 Número de bytes solicitado en el nuevo bloque de memoria.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Llame a [CWin32Heap::Free](#free) o [CWin32Heap::Reallocate](#reallocate) para liberar la memoria asignada por este método.  
  
 Implementa mediante [HeapAlloc](http://msdn.microsoft.com/library/windows/desktop/aa366597).  
  
##  <a name="attach"></a>CWin32Heap:: Attach  
 El objeto del montón se asocia a un montón existente.  
  
```
void Attach(HANDLE hHeap, bool bTakeOwnership) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hHeap`  
 Identificador de montón existente.  
  
 `bTakeOwnership`  
 Una que indica si marca la `CWin32Heap` objeto consiste en tomar posesión sobre los recursos del montón.  
  
### <a name="remarks"></a>Comentarios  
 Si `bTakeOwnership` es TRUE, la `CWin32Heap` objeto es responsable de eliminar el identificador del montón.  
  
##  <a name="cwin32heap"></a>CWin32Heap::CWin32Heap  
 El constructor.  
  
```
CWin32Heap() throw();
CWin32Heap( HANDLE  hHeap) throw();
CWin32Heap(
    DWORD  dwFlags,
    size_t nInitialSize,
    size_t nMaxSize = 0);
```  
  
### <a name="parameters"></a>Parámetros  
 `hHeap`  
 Objeto de montón existente.  
  
 `dwFlags`  
 Marcas utilizadas en la creación del montón.  
  
 *nInitialSize*  
 Tamaño inicial del montón.  
  
 `nMaxSize`  
 Tamaño máximo del montón.  
  
### <a name="remarks"></a>Comentarios  
 Antes de asignar memoria, es necesario proporcionar el objeto `CWin32Heap` con un identificador de montón válido. El modo más sencillo de hacerlo es usar el montón de procesos:  
  
 [!code-cpp[NVC_ATL_Utilities&#92;](../../atl/codesnippet/cpp/cwin32heap-class_1.cpp)]  
  
 También se puede proporcionar un identificador de montón existente al constructor, en cuyo caso el nuevo objeto no asumirá la propiedad del montón. El identificador del montón original seguirá siendo válido cuando se elimine el objeto `CWin32Heap`.  
  
 También se puede asociar un montón existente al nuevo objeto utilizando [CWin32Heap:: Attach](#attach).  
  
 Si se necesita un montón en las operaciones que se realizan en un único subproceso, la mejor manera de hacerlo es crear el objeto del modo siguiente:  
  
 [!code-cpp[NVC_ATL_Utilities&#93;](../../atl/codesnippet/cpp/cwin32heap-class_2.cpp)]  
  
 El parámetro **HEAP_NO_SERIALIZE** especifica que la exclusión mutua no se utilizará cuando las funciones del montón asignación y liberen memoria, con el correspondiente aumento de rendimiento.  
  
 El tercer parámetro se establece en 0 de forma predeterminada, lo que permite al montón crecer según sea necesario. Consulte [HeapCreate](http://msdn.microsoft.com/library/windows/desktop/aa366599\(v=vs.85\).aspx) para obtener una explicación de los tamaños de memoria y las marcas.  
  
##  <a name="dtor"></a>CWin32Heap:: ~ CWin32Heap  
 Destructor.  
  
```
~CWin32Heap() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Destruye el identificador del montón si la `CWin32Heap` objeto tiene la propiedad del montón.  
  
##  <a name="detach"></a>CWin32Heap::Detach  
 Desasocia el objeto en el montón de un montón existente.  
  
```
HANDLE Detach() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador del montón al que estaba conectado previamente el objeto.  
  
##  <a name="free"></a>CWin32Heap::Free  
 Libera memoria previamente asignada desde el montón por [CWin32Heap::Allocate](#allocate) o [CWin32Heap::Reallocate](#reallocate).  
  
```
virtual void Free(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero al bloque de memoria libre. NULL es un valor válido y no hace nada.  
  
##  <a name="getsize"></a>CWin32Heap::GetSize  
 Devuelve el tamaño de un bloque de memoria asignado desde el objeto del montón.  
  
```
virtual size_t GetSize(void* p) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero al bloque de memoria cuyo tamaño va a obtener el método. Se trata de un puntero devuelto por [CWin32Heap::Allocate](#allocate) o [CWin32Heap::Reallocate](#reallocate).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el tamaño, en bytes, del bloque de memoria asignado.  
  
##  <a name="m_bownheap"></a>CWin32Heap::m_bOwnHeap  
 Un indicador se utiliza para determinar la propiedad actual de almacena en el identificador del montón [m_hHeap](#m_hheap).  
  
```
bool m_bOwnHeap;
```  
  
##  <a name="m_hheap"></a>CWin32Heap::m_hHeap  
 Identificador del objeto de montón.  
  
```
HANDLE m_hHeap;
```  
  
### <a name="remarks"></a>Comentarios  
 Una variable que se utiliza para almacenar un identificador para el objeto del montón.  
  
##  <a name="reallocate"></a>CWin32Heap::Reallocate  
 Reasigna un bloque de memoria del objeto de montón.  
  
```
virtual __declspec(allocator) void* Reallocate(void* p, size_t nBytes) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `p`  
 Puntero al bloque de memoria que se va a reasignar.  
  
 `nBytes`  
 Nuevo tamaño en bytes del bloque asignado. El bloque se puede hacer mayor o menor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero al bloque de memoria recién asignado.  
  
### <a name="remarks"></a>Comentarios  
 Si `p` es NULL, se supone que el bloque de memoria no se ha asignado todavía y [CWin32Heap::Allocate](#allocate) se llama con un argumento de `nBytes`.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [IAtlMemMgr (clase)](../../atl/reference/iatlmemmgr-class.md)   
 [Clase CLocalHeap](../../atl/reference/clocalheap-class.md)   
 [Clase CGlobalHeap](../../atl/reference/cglobalheap-class.md)   
 [Clase CCRTHeap](../../atl/reference/ccrtheap-class.md)   
 [Clase CComHeap](../../atl/reference/ccomheap-class.md)

