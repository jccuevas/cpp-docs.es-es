---
title: CStringElementTraitsI (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d523c882754a69239ebbbfad1adcb0e91c0c4ca6
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37879893"
---
# <a name="cstringelementtraitsi-class"></a>CStringElementTraitsI (clase)
Esta clase proporciona funciones estáticas relacionados con las cadenas almacenadas en objetos de clase de colección. Es similar a [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), pero realiza comparaciones entre mayúsculas y minúsculas.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>  
class CStringElementTraitsI : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
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
|[CStringElementTraitsI::CompareElements](#compareelements)|Llame a esta función estática para comparar dos elementos de cadena para la igualdad, omitiendo las diferencias en el caso.|  
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Llame a esta función estática para comparar dos elementos de cadena, se omitirá las diferencias en el caso.|  
|[CStringElementTraitsI::Hash](#hash)|Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones estáticas para comparar cadenas y para crear un valor hash. Estas funciones son útiles cuando se usa una clase de colección para almacenar los datos basados en cadena. Use [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena son para con tratarse como referencias.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringElementTraitsI::CompareElements  
 Llame a esta función estática para comparar dos elementos de cadena para la igualdad, omitiendo las diferencias en el caso.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *str1*  
 El primer elemento de cadena.  
  
 *str2*  
 La segunda cadena de elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos si no son iguales, es false.  
  
### <a name="remarks"></a>Comentarios  
 Las comparaciones distinguen entre mayúsculas y minúsculas.  
  
##  <a name="compareelementsordered"></a>  CStringElementTraitsI::CompareElementsOrdered  
 Llame a esta función estática para comparar dos elementos de cadena, se omitirá las diferencias en el caso.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *str1*  
 El primer elemento de cadena.  
  
 *str2*  
 La segunda cadena de elemento.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si las cadenas son idénticas, < 0 si *str1* es menor que *str2*, o 0 > Si *str1* es mayor que *str2*. El [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) método se usa para realizar las comparaciones.  

  
### <a name="remarks"></a>Comentarios  
 Las comparaciones distinguen entre mayúsculas y minúsculas.  
  
##  <a name="hash"></a>  CStringElementTraitsI::Hash  
 Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *str*  
 El elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de hash, calculado con contenido de la cadena.  
  
##  <a name="inargtype"></a>  CStringElementTraitsI::INARGTYPE  
 El tipo de datos que se usará para agregar elementos al objeto de clase de colección.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="outargtype"></a>  CStringElementTraitsI::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [CElementTraitsBase (clase)](../../atl/reference/celementtraitsbase-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [CStringElementTraits (clase)](../../atl/reference/cstringelementtraits-class.md)
