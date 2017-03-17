---
title: Clase CDefaultCompareTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
dev_langs:
- C++
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
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
ms.openlocfilehash: 1d1253b7a7d69024465627cc9fb37fcd2afba693
ms.lasthandoff: 02/24/2017

---
# <a name="cdefaultcomparetraits-class"></a>Clase CDefaultCompareTraits
Esta clase proporciona las funciones de comparación de elemento de predeterminado.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template<typename T>  
class CDefaultCompareTraits
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Estático) Llame a esta función para comparar dos elementos son iguales.|  
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Estático) Llame a esta función para determinar el elemento mayor y menor.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase contiene dos funciones estáticas para comparar los elementos almacenados en un objeto de clase de colección. Esta clase es utilizada por el [CDefaultElementTraits clase](../../atl/reference/cdefaultelementtraits-class.md).  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="compareelements"></a>CDefaultCompareTraits::CompareElements  
 Llame a esta función para comparar dos elementos son iguales.  
  
```
static bool CompareElements(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>Parámetros  
 `element1`  
 El primer elemento.  
  
 `element2`  
 El segundo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos de lo contrario, son iguales, false.  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función es la igualdad ( `==`) (operador). Para objetos distintos tipos de datos simples, esta función necesite reemplazar.  
  
##  <a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered  
 Llame a esta función para determinar el elemento mayor y menor.  
  
```
static int CompareElementsOrdered(const T& element1, const T& element2);
```  
  
### <a name="parameters"></a>Parámetros  
 `element1`  
 El primer elemento.  
  
 `element2`  
 El segundo elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un entero basado en la tabla siguiente:  
  
|Condición|Valor devuelto|  
|---------------|------------------|  
|`element1` < `element2`|<0|  
|`element1` == `element2`|0|  
|`element1` > `element2`|>0|  
  
### <a name="remarks"></a>Comentarios  
 La implementación predeterminada de esta función usa el `==`, ** \< **, y ** > ** operadores. Para objetos distintos tipos de datos simples, esta función necesite reemplazar.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)

