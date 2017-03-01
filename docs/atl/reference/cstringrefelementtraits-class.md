---
title: Clase CStringRefElementTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CStringRefElementTraits
- ATL.CStringRefElementTraits
- ATL::CStringRefElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
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
ms.openlocfilehash: 3709a5d4aac02651e5b6fafd441499fea1f8eabc
ms.lasthandoff: 02/24/2017

---
# <a name="cstringrefelementtraits-class"></a>Clase CStringRefElementTraits
Esta clase proporciona funciones estáticas relacionadas con las cadenas almacenadas en objetos de la clase de colección. Los objetos de cadena se tratan como referencias.  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStringRefElementTraits::CompareElements](#compareelements)|Llame a esta función para comparar dos elementos de cadena de igualdad estática.|  
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Llame a esta función para comparar dos elementos de cadena estática.|  
|[CStringRefElementTraits::Hash](#hash)|Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones estáticas para comparar cadenas y para crear un valor hash. Estas funciones son útiles cuando se utiliza una clase de colección para almacenar datos de cadena. A diferencia de [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) y [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` hace que el `CString` argumentos que se pasarán como **const CString aspecto** referencias.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringRefElementTraits`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="a-namecompareelementsa--cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements  
 Llame a esta función para comparar dos elementos de cadena de igualdad estática.  
  
```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `element1`  
 El primer elemento de cadena.  
  
 `element2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos de lo contrario, son iguales, false.  
  
##  <a name="a-namecompareelementsordereda--cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered  
 Llame a esta función para comparar dos elementos de cadena estática.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `str1`  
 El primer elemento de cadena.  
  
 `str2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si las cadenas son idénticas, < 0="" if=""> `str1` es menor que `str2`, o 0 > si `str1` es mayor que `str2`. El [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) método se usa para realizar las comparaciones.  
  
##  <a name="a-namehasha--cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits::Hash  
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
 [Información general de la clase](../../atl/atl-class-overview.md)

