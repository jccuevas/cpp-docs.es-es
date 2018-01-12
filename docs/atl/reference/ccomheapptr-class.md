---
title: Clase de plantilla CComHeapPtr | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComHeapPtr
- ATLBASE/ATL::CComHeapPtr
- ATLBASE/ATL::CComHeapPtr::CComHeapPtr
dev_langs: C++
helpviewer_keywords: CComHeapPtr class
ms.assetid: bd08b53d-da2b-43ab-a79c-e7c8dbbc5994
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8619c050ecc356e1445991b625da00c04f462848
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CComHeapPtr::CComHeapPtr](#ccomheapptr)|El constructor.|  
  
## <a name="remarks"></a>Comentarios  
 `CComHeapPtr`se deriva de `CHeapPtr`, pero utiliza [CComAllocator](../../atl/reference/ccomallocator-class.md) para asignar memoria que usa las rutinas de COM. Vea [CHeapPtr](../../atl/reference/cheapptr-class.md) y [CHeapPtrBase](../../atl/reference/cheapptrbase-class.md) para los métodos disponibles.  
  
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
 El puntero del montón, opcionalmente, puede crearse con una existente `CComHeapPtr` objeto. Si es así, el nuevo `CComHeapPtr` objeto asume la responsabilidad de administrar los recursos y el nuevo puntero.  
  
## <a name="see-also"></a>Vea también  
 [Clase CHeapPtr](../../atl/reference/cheapptr-class.md)   
 [Clase CHeapPtrBase](../../atl/reference/cheapptrbase-class.md)   
 [Clase CComAllocator](../../atl/reference/ccomallocator-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
