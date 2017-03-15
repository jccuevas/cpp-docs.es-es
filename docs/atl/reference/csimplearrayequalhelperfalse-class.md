---
title: Clase CSimpleArrayEqualHelperFalse | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CSimpleArrayEqualHelperFalse<T>
- ATL::CSimpleArrayEqualHelperFalse
- ATL.CSimpleArrayEqualHelperFalse
- ATL::CSimpleArrayEqualHelperFalse<T>
- CSimpleArrayEqualHelperFalse
dev_langs:
- C++
helpviewer_keywords:
- CSimpleArrayEqualHelperFalse class
ms.assetid: 6918af6f-d23d-49eb-8482-c44272f5ffeb
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
ms.openlocfilehash: cd5ed7058194880ef1ceaebe788e3deb60d4ac8e
ms.lasthandoff: 02/24/2017

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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CSimpleArrayEqualHelperFalse::IsEqual](#isequal)|(Estático) Devuelve false.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase de rasgos es un complemento para el `CSimpleArray` clase. TI siempre devuelve false y además, volverá a llamar `ATLASSERT` con un argumento de false si nunca se hace referencia. En situaciones donde la prueba de igualdad no está suficientemente definida, esta clase permite a una matriz que contiene elementos para funcionar correctamente para la mayoría de los métodos, pero producirá un error de forma bien definida para los métodos que dependen de las comparaciones como [CSimpleArray::Find](../../atl/reference/csimplearray-class.md#find).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlsimpcoll.h  
  
##  <a name="a-nameisequala--csimplearrayequalhelperfalseisequal"></a><a name="isequal"></a>CSimpleArrayEqualHelperFalse::IsEqual  
 Devuelve false.  
  
```
static bool IsEqual(const T&, const T&);
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve false.  
  
### <a name="remarks"></a>Comentarios  
 Este método siempre devuelve false y llamará a `ATLASSERT` con un argumento de false si se hace referencia. El propósito de `CSimpleArrayEqualHelperFalse::IsEqual` es obligar a métodos mediante comparaciones de igualdad pruebas no se han definido correctamente errores de forma bien definida.  
  
## <a name="see-also"></a>Vea también  
 [Clase CSimpleArrayEqualHelper](../../atl/reference/csimplearrayequalhelper-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

