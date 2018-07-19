---
title: Clase CStringRefElementTraits | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
dev_langs:
- C++
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e8746bf216be417fb569aae58421b272c983914b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32360692"
---
# <a name="cstringrefelementtraits-class"></a>Clase CStringRefElementTraits
Esta clase proporciona funciones estáticas relacionadas con las cadenas almacenadas en objetos de clase de colección. Los objetos de cadena se tratan como referencias.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CStringRefElementTraits : public CElementTraitsBase<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|Llame a esta función estática para comparar dos elementos de cadena para la igualdad.|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Llame a esta función estática para comparar dos elementos de cadena.|  
|[CStringRefElementTraits::Hash](#hash)|Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones estáticas para comparar cadenas y para crear un valor hash. Estas funciones son útiles cuando se usa una clase de colección para almacenar los datos de cadena. A diferencia de [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) y [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` hace que el `CString` argumentos que se pasarán como **const CString &** hace referencia.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="compareelements"></a>  CStringRefElementTraits::CompareElements  
 Llame a esta función estática para comparar dos elementos de cadena para la igualdad.  
  
```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `element1`  
 El primer elemento de cadena.  
  
 `element2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos en caso contrario, son iguales, false.  
  
##  <a name="compareelementsordered"></a>  CStringRefElementTraits::CompareElementsOrdered  
 Llame a esta función estática para comparar dos elementos de cadena.  
  
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
  
##  <a name="hash"></a>  CStringRefElementTraits::Hash  
 Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 El elemento de la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de hash, que se calcula con el contenido de la cadena.  
  
## <a name="see-also"></a>Vea también  
 [Clase CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)
