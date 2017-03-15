---
title: Clase CStringElementTraitsI | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CStringElementTraitsI
- CStringElementTraitsI
- ATL.CStringElementTraitsI
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
caps.latest.revision: 18
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
ms.openlocfilehash: 995c4798f92db3b3f065bf2176ab52ff53d282b0
ms.lasthandoff: 02/24/2017

---
# <a name="cstringelementtraitsi-class"></a>Clase CStringElementTraitsI
Esta clase proporciona funciones estáticas relacionadas con las cadenas almacenadas en objetos de la clase de colección. Es similar a [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), pero realiza comparaciones entre mayúsculas y minúsculas.  
  
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
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStringElementTraitsI::INARGTYPE](#inargtype)|Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.|  
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStringElementTraitsI::CompareElements](#compareelements)|Llame a esta función estática para comparar dos elementos de cadena para la igualdad, omitiendo las diferencias en el caso.|  
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Llame a esta función estática para comparar dos elementos de cadena, omitiendo las diferencias en el caso.|  
|[CStringElementTraitsI::Hash](#hash)|Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones estáticas para comparar cadenas y para crear un valor hash. Estas funciones son útiles cuando se utiliza una clase de colección para almacenar datos de cadena. Utilice [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena son con considerarse como referencias.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)  
  
 `CStringElementTraitsI`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcoll.h  
  
##  <a name="a-namecompareelementsa--cstringelementtraitsicompareelements"></a><a name="compareelements"></a>CStringElementTraitsI::CompareElements  
 Llame a esta función estática para comparar dos elementos de cadena para la igualdad, omitiendo las diferencias en el caso.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `str1`  
 El primer elemento de cadena.  
  
 `str2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos de lo contrario, son iguales, false.  
  
### <a name="remarks"></a>Comentarios  
 Las comparaciones distinguen entre mayúsculas y minúsculas.  
  
##  <a name="a-namecompareelementsordereda--cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered  
 Llame a esta función estática para comparar dos elementos de cadena, omitiendo las diferencias en el caso.  
  
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

  
### <a name="remarks"></a>Comentarios  
 Las comparaciones distinguen entre mayúsculas y minúsculas.  
  
##  <a name="a-namehasha--cstringelementtraitsihash"></a><a name="hash"></a>CStringElementTraitsI::Hash  
 Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.  
  
```
static ULONG Hash(INARGTYPE str) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 El elemento de la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de hash, que se calcula con el contenido de la cadena.  
  
##  <a name="a-nameinargtypea--cstringelementtraitsiinargtype"></a><a name="inargtype"></a>CStringElementTraitsI::INARGTYPE  
 Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="a-nameoutargtypea--cstringelementtraitsioutargtype"></a><a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
## <a name="see-also"></a>Vea también  
 [Clase CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clase CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)

