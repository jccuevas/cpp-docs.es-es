---
title: Clase CSimpleMapEqualHelper | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
caps.latest.revision: 20
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
ms.openlocfilehash: ddb793889748446b9613c91ce6fcefe28da32eb3
ms.lasthandoff: 02/24/2017

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
 El elemento clave.  
  
 `TVal`  
 El elemento de valor.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleMapEqualHelper::IsEqualKey](#isequalkey)|(Estático) Comprueba la igualdad de dos claves.|  
|[CSimpleMapEqualHelper::IsEqualValue](#isequalvalue)|(Estático) Comprueba la igualdad de dos valores.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un suplemento de la `CSimpleMap` clase. Proporciona métodos para comparar dos `CSimpleMap` elementos (en concreto, los componentes clave y valor) para la igualdad del objeto. De forma predeterminada, las claves y valores se comparan mediante `operator==()`, pero si el mapa contiene tipos de datos complejos que no tienen su propio operador de igualdad, se puede invalidar esta clase para proporcionar la funcionalidad adicional necesaria.  
  
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
 Devuelve true si las claves de lo contrario, son iguales, false.  
  
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
 Devuelve true si los valores equivalen, false en caso contrario.  
  
## <a name="see-also"></a>Vea también  
 [Clase CSimpleMapEqualHelperFalse](../../atl/reference/csimplemapequalhelperfalse-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

