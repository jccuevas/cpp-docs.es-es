---
title: Clase CSimpleMapEqualHelper | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualKey
- ATLSIMPCOLL/ATL::CSimpleMapEqualHelper::IsEqualValue
dev_langs:
- C++
helpviewer_keywords:
- CSimpleMapEqualHelper class
ms.assetid: 9bb2968a-d609-405c-8272-ff3b42df6164
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ecc32dc8e6e9b249b0b8b334ec3d08bf26cbd1ed
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="csimplemapequalhelper-class"></a>Clase CSimpleMapEqualHelper
Esta clase es una aplicación auxiliar para la [CSimpleMap](../../atl/reference/csimplemap-class.md) clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class TKey, class TVal>  
class CSimpleMapEqualHelper
```  
  
#### <a name="parameters"></a>Parámetros  
 `TKey`  
 El elemento key.  
  
 `TVal`  
 El elemento de valor.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Estático) Comprueba la igualdad de dos claves.|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Estático) Comprueba la igualdad de dos valores.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un complemento para el `CSimpleMap` clase. Proporciona métodos para comparar dos `CSimpleMap` elementos (en concreto, los componentes clave y valor) para la igualdad de objetos. De forma predeterminada, los valores y claves se comparan mediante `operator==()`, pero si el objeto map contiene tipos de datos complejos que no tienen su propio operador de igualdad, se puede invalidar esta clase para proporcionar la funcionalidad adicional necesaria.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
##  <a name="isequalkey"></a>CSimpleMapEqualHelper::IsEqualKey  
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
  
##  <a name="isequalvalue"></a>CSimpleMapEqualHelper::IsEqualValue  
 Comprueba la igualdad de dos valores.  
  
```
static bool IsEqualValue(const TVal& v1, const TVal& v2);
```  
  
### <a name="parameters"></a>Parámetros  
 *V1*  
 Primer valor.  
  
 *v2*  
 Segundo valor.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los valores en caso contrario, son iguales, false.  
  
## <a name="see-also"></a>Vea también  
 [Clase CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
