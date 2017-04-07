---
title: Clase de plantilla CComHeapPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs:
- C++
helpviewer_keywords:
- CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 0e5196a98b8fd76b2e7e791fd2cd9549099a1cc9
ms.lasthandoff: 02/24/2017

---
# <a name="ccomheapptr-class"></a>Clase de plantilla CComHeapPtr
Una clase de puntero inteligente para administrar los punteros del montón.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CComHeapPtr : public CHeapPtr<T, CComAllocator>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de objeto que se almacenará en el montón.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|El constructor.|  
  
## <a name="remarks"></a>Comentarios  
 `CComHeapPtr`se deriva de `CHeapPtr`, pero utiliza [CComAllocator](../../atl/reference/ccomallocator-class.md) para asignar memoria mediante rutinas COM. Consulte [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) para los métodos disponibles.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)  
  
 [CHeapPtr](../../atl/reference/cheapptr-class.md)  
  
 `CComHeapPtr`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="ccomheapptr"></a>CComHeapPtr::CComHeapPtr  
 El constructor.  
  
```
CComHeapPtr() throw();
explicit CComHeapPtr(T* pData) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `pData`  
 Objeto `CComHeapPtr` existente.  
  
### <a name="remarks"></a>Comentarios  
 El puntero de pila, opcionalmente, puede crearse con existente `CComHeapPtr` objeto. Si es así, la nueva `CComHeapPtr` objeto asume la responsabilidad de administrar el nuevo puntero y recursos.  
  
## <a name="see-also"></a>Vea también  
 [Clase CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Clase CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)   
 [Clase CComAllocator](../../atl/reference/ccomallocator-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

