---
title: Clase CSimpleMapEqualHelperFalse | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CSimpleMapEqualHelperFalse
- CSimpleMapEqualHelperFalse
- ATL.CSimpleMapEqualHelperFalse
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
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
ms.openlocfilehash: 68a08ffc0ba126c523a779e3d1a72217dead6235
ms.lasthandoff: 02/24/2017

---
# <a name="csimplemapequalhelperfalse-class"></a>Clase CSimpleMapEqualHelperFalse
Esta clase es una aplicación auxiliar para la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Estático) Comprueba la igualdad de dos claves.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Estático) Devuelve false.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un suplemento de la `CSimpleMap` clase. Proporciona un método para comparar dos elementos incluidos en la `CSimpleMap` objeto específicamente dos elementos de valor o dos elementos clave.  
  
 La comparación de valores siempre devolverá false y además, llamará a `ATLASSERT` con un argumento de false si nunca se hace referencia. En situaciones donde la prueba de igualdad no está suficientemente definida, esta clase permite a un mapa que contiene pares clave-valor para funcionar correctamente para la mayoría de los métodos, pero producirá un error de forma bien definida para los métodos que dependen de las comparaciones como [CSimpleMap::FindVal](../../atl/reference/csimplemap-class.md#findval).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
##  <a name="a-nameisequalkeya--csimplemapequalhelperfalseisequalkey"></a><a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey  
 Comprueba la igualdad de dos claves.  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>Parámetros  
 `k1`  
 La primera clave.  
  
 `k2`  
 La segunda clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si las claves de lo contrario, son iguales, false.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).  
  
##  <a name="a-nameisequalvaluea--csimplemapequalhelperfalseisequalvalue"></a><a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue  
 Devuelve false.  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método siempre devuelve false y llamará a `ATLASSERT` con un argumento de false si nunca se hace referencia. El propósito de `CSimpleMapEqualHelperFalse::IsEqualValue` es obligar a métodos mediante comparaciones de igualdad pruebas no se han definido correctamente errores de forma bien definida.  
  
## <a name="see-also"></a>Vea también  
 [Clase CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

