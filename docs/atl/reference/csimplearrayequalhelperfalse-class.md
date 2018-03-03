---
title: Clase CSimpleArrayEqualHelperFalse | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelperFalse::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 28d43b6a83842373c2fc169ce43022f1912c4e0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="csimplearrayequalhelperfalse-class"></a>Clase CSimpleArrayEqualHelperFalse
Esta clase es una aplicación auxiliar para la [CSimpleArray](../../atl/reference/csimplearray-class.md) clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class CSimpleArrayEqualHelperFalse
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Estático) Devuelve false.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un complemento para el `CSimpleArray` clase. TI siempre devuelve false y además, volverá a llamar `ATLASSERT` con un argumento de false si alguna vez se hace referencia. En situaciones donde no se define lo suficientemente la prueba de igualdad, esta clase permite que una matriz que contiene elementos para funcionar correctamente para la mayoría de los métodos, pero producirá un error de una manera bien definida para los métodos que dependen de las comparaciones como [CSimpleArray:: Buscar](../../atl/reference/csimplearray-class.md#find).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual  
 Devuelve false.  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método siempre devuelve false y llamará a `ATLASSERT` con un argumento de false si se hace referencia. El propósito de `CSimpleArrayEqualHelperFalse::IsEqual` es forzar métodos usar comparaciones genere un error de una manera bien definida cuando no se han definido adecuadamente pruebas de igualdad.  
  
## <a name="see-also"></a>Vea también  
 [Clase CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
