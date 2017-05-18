---
title: Clase CSimpleArrayEqualHelper | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper
- ATLSIMPCOLL/ATL::CSimpleArrayEqualHelper::IsEqual
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelper class
ms.assetid: a2b55d89-78c9-42ef-842c-5304c6d20ad6
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 4a87879683257c66de5fe4e720dd29fa4c47031d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="csimplearrayequalhelper-class"></a>Clase CSimpleArrayEqualHelper
Esta clase es una aplicación auxiliar para la [CSimpleArray](../../atl/reference/csimplearray-class.md) clase.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class CSimpleArrayEqualHelper
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 Una clase derivada.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleArrayEqualHelper::IsEqual](#isequal)|(Estático) Comprueba si dos `CSimpleArray` elementos para la igualdad del objeto.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un suplemento de la `CSimpleArray` clase. Proporciona un método para comparar dos elementos almacenados en un `CSimpleArray` objeto. De forma predeterminada, los elementos se comparan mediante **operator=()**, pero si la matriz contiene los tipos de datos complejos que no tienen su propio operador de igualdad, será necesario invalidar esta clase.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
##  <a name="isequal"></a>CSimpleArrayEqualHelper::IsEqual  
 Comprueba si dos `CSimpleArray` elementos para la igualdad del objeto.  
  
```
static bool IsEqual(
    const T& t1,
    const T& t2);
```  
  
### <a name="parameters"></a>Parámetros  
 *T1*  
 Un objeto de tipo T.  
  
 *T2*  
 Un objeto de tipo T.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos de lo contrario, son iguales, false.  
  
## <a name="see-also"></a>Vea también  
 [Clase CSimpleArray](../../atl/reference/csimplearray-class.md)   
 [Clase CSimpleArrayEqualHelperFalse](../../atl/reference/csimplearrayequalhelperfalse-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

