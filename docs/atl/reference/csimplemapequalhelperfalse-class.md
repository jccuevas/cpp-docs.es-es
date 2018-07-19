---
title: CSimpleMapEqualHelperFalse (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 70cea341e7f78032cdaca260e3c891f4c762e0b6
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37882629"
---
# <a name="csimplemapequalhelperfalse-class"></a>CSimpleMapEqualHelperFalse (clase)
Esta clase es una aplicación auxiliar para el [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelperFalse
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Estático) Comprueba la igualdad de dos claves.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Estático) Devuelve "false".|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un complemento para el `CSimpleMap` clase. Proporciona un método para comparar dos elementos que contiene el `CSimpleMap` objeto específicamente dos elementos de valor o dos elementos clave.  
  
 La comparación de valor siempre devolverá false y, además, se llamará a `ATLASSERT` con el argumento false si nunca se hace referencia. En situaciones donde no se define lo suficientemente la prueba de igualdad, esta clase permite que un mapa que contiene pares de clave/valor para funcionar correctamente para la mayoría de los métodos, pero producirá un error de forma bien definida para los métodos que dependen de las comparaciones como [CSimpleMap:: FindVal](../../atl/reference/csimplemap-class.md#findval).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>  CSimpleMapEqualHelperFalse::IsEqualKey  
 Comprueba la igualdad de dos claves.  
  
```
static bool IsEqualKey(const TKey& k1, const TKey& k2);
```  
  
### <a name="parameters"></a>Parámetros  
 *k1*  
 La primera clave.  
  
 *k2*  
 La segunda clave.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si las claves si no son iguales, es false.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).  
  
##  <a name="isequalvalue"></a>  CSimpleMapEqualHelperFalse::IsEqualValue  
 Devuelve false.  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método siempre devuelve false y llamará a `ATLASSERT` con el argumento false si nunca se hace referencia. El propósito de `CSimpleMapEqualHelperFalse::IsEqualValue` es forzar a métodos mediante comparaciones genere un error de una manera bien definida cuando las pruebas de igualdad no se han definido correctamente.  
  
## <a name="see-also"></a>Vea también  
 [CSimpleMapEqualHelper (clase)](../../atl/reference/csimplemapequalhelper-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
