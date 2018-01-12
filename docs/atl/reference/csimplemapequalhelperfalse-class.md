---
title: Clase CSimpleMapEqualHelperFalse | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelperFalse::IsEqualValue
dev_langs: C++
helpviewer_keywords: CSimpleMapEqualHelperFalse class
ms.assetid: a873eea3-e130-45cc-a476-61ee79511c3b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c1418114233b59112fcffb58ef4ae7c437af5ab3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMapEqualHelperFalse::IsEqualKey](#isequalkey)|(Estático) Comprueba la igualdad de dos claves.|  
|[CSimpleMapEqualHelperFalse::IsEqualValue](#isequalvalue)|(Estático) Devuelve false.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un complemento para el `CSimpleMap` clase. Proporciona un método para comparar dos elementos incluidos en la `CSimpleMap` objeto, específicamente dos elementos de valor o dos elementos clave.  
  
 La comparación de valores siempre devolverá false y además, llamará a `ATLASSERT` con un argumento de false si alguna vez se hace referencia. En situaciones donde no se define lo suficientemente la prueba de igualdad, esta clase permite a un mapa que contiene pares de clave/valor para funcionar correctamente para la mayoría de los métodos, pero producirá un error de una manera bien definida para los métodos que dependen de las comparaciones como [CSimpleMap:: FindVal](../../atl/reference/csimplemap-class.md#findval).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>CSimpleMapEqualHelperFalse::IsEqualKey  
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
 Devuelve true si las claves en caso contrario, son iguales, false.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md).  
  
##  <a name="isequalvalue"></a>CSimpleMapEqualHelperFalse::IsEqualValue  
 Devuelve false.  
  
```
static bool IsEqualValue(const TVal&, const TVal&);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método siempre devuelve false y llamará a `ATLASSERT` con un argumento de false si alguna vez se hace referencia. El propósito de `CSimpleMapEqualHelperFalse::IsEqualValue` es forzar métodos usar comparaciones genere un error de una manera bien definida cuando no se han definido adecuadamente pruebas de igualdad.  
  
## <a name="see-also"></a>Vea también  
 [Clase CSimpleMapEqualHelper](../../atl/reference/csimplemapequalhelper-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
