---
title: Clase CStringElementTraitsI | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7803d85c7adf346a06f87d35aba7f42e47f77b2a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="cstringelementtraitsi-class"></a>Clase CStringElementTraitsI
Esta clase proporciona funciones estáticas relacionadas con las cadenas almacenadas en objetos de clase de colección. Es similar a [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), pero realiza comparaciones entre mayúsculas y minúsculas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>  
class CStringElementTraitsI : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringElementTraitsI::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|  
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringElementTraitsI::CompareElements](#compareelements)|Llame a esta función estática para comparar dos elementos de cadena para la igualdad, pasando por alto las diferencias en los casos.|  
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Llame a esta función estática para comparar dos elementos de cadena, se omitirá las diferencias en los casos.|  
|[CStringElementTraitsI::Hash](#hash)|Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones estáticas para comparar cadenas y para crear un valor hash. Estas funciones son útiles cuando se usa una clase de colección para almacenar los datos de cadena. Use [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena deben con abordarse como referencias.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="compareelements"></a>CStringElementTraitsI::CompareElements  
 Llame a esta función estática para comparar dos elementos de cadena para la igualdad, pasando por alto las diferencias en los casos.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `str1`  
 El primer elemento de cadena.  
  
 `str2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos en caso contrario, son iguales, false.  
  
### <a name="remarks"></a>Comentarios  
 Las comparaciones distinguen entre mayúsculas y minúsculas.  
  
##  <a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered  
 Llame a esta función estática para comparar dos elementos de cadena, se omitirá las diferencias en los casos.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `str1`  
 El primer elemento de cadena.  
  
 `str2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si las cadenas son idénticas, < 0 si `str1` es menor que `str2`, o 0 > Si `str1` es mayor que `str2`. El [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) método se usa para realizar las comparaciones.  

  
### <a name="remarks"></a>Comentarios  
 Las comparaciones distinguen entre mayúsculas y minúsculas.  
  
##  <a name="hash"></a>CStringElementTraitsI::Hash  
 Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 El elemento de la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de hash, que se calcula con el contenido de la cadena.  
  
##  <a name="inargtype"></a>CStringElementTraitsI::INARGTYPE  
 El tipo de datos que se usará para agregar elementos al objeto de clase de colección.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [Clase CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CStringElementTraits (clase)](../../atl/reference/cstringelementtraits-class.md)
