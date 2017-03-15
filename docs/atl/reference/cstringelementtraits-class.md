---
title: Clase CStringElementTraits | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL.CStringElementTraits<T>
- ATL::CStringElementTraits<T>
- CStringElementTraits
- ATL.CStringElementTraits
- ATL::CStringElementTraits
dev_langs:
- C++
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
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
ms.openlocfilehash: f46ff072bcd0f772dac1bba52b114d82ee433112
ms.lasthandoff: 02/24/2017

---
# <a name="cstringelementtraits-class"></a>Clase CStringElementTraits
Esta clase proporciona funciones estáticas que se utilizan las clases de colección almacenar `CString` objetos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <typename T>  
class CStringElementTraits
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 El tipo de datos que se almacenará en la colección.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-typedefs"></a>Definiciones de tipos públicas  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStringElementTraits::INARGTYPE](#inargtype)|Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.|  
|[CStringElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CStringElementTraits::CompareElements](#compareelements)|(Estático) Llame a esta función para comparar dos elementos de cadena son iguales.|  
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Estático) Llame a esta función para comparar dos elementos de cadena.|  
|[CStringElementTraits::CopyElements](#copyelements)|(Estático) Llame a esta función para copiar `CString` elementos almacenados en un objeto de clase de colección.|  
|[CStringElementTraits::Hash](#hash)|(Estático) Llame a esta función para calcular un valor hash para el elemento de la cadena especificada.|  
|[CStringElementTraits::RelocateElements](#relocateelements)|(Estático) Llame a esta función para reubicar `CString` elementos almacenados en un objeto de clase de colección.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona funciones estáticas para copiar, pasar y comparar cadenas y para crear un valor hash. Estas funciones son útiles cuando se utiliza una clase de colección para almacenar datos de cadena. Utilice [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) cuando sean necesarias comparaciones entre mayúsculas y minúsculas. Utilice [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena deben tratarse como referencias.  
  
 Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** cstringt.h  
  
##  <a name="a-namecompareelementsa--cstringelementtraitscompareelements"></a><a name="compareelements"></a>CStringElementTraits::CompareElements  
 Llame a esta función para comparar dos elementos de cadena de igualdad estática.  
  
```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Parámetros  
 `str1`  
 El primer elemento de cadena.  
  
 `str2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si los elementos de lo contrario, son iguales, false.  
  
##  <a name="a-namecompareelementsordereda--cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered  
 Llame a esta función para comparar dos elementos de cadena estática.  
  
```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```  
  
### <a name="parameters"></a>Parámetros  
 `str1`  
 El primer elemento de cadena.  
  
 `str2`  
 El segundo elemento de cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Cero si las cadenas son idénticas, < 0="" if=""> `str1` es menor que `str2`, o 0 > si `str1` es mayor que `str2`. El [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) método se usa para realizar las comparaciones.  

  
##  <a name="a-namecopyelementsa--cstringelementtraitscopyelements"></a><a name="copyelements"></a>CStringElementTraits::CopyElements  
 Llame a esta función estática para copiar `CString` elementos almacenados en un objeto de clase de colección.  
  
```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDest`  
 Puntero al primer elemento que va a recibir los datos copiados.  
  
 `pSrc`  
 Puntero para el primer elemento que se va a copiar.  
  
 `nElements`  
 Número de elementos que se van a copiar.  
  
### <a name="remarks"></a>Comentarios  
 Los elementos de origen y de destino no deben superponerse.  
  
##  <a name="a-namehasha--cstringelementtraitshash"></a><a name="hash"></a>CStringElementTraits::Hash  
 Llame a esta función estática para calcular un valor hash para el elemento de la cadena especificada.  
  
```
static ULONG Hash(INARGTYPE str);
```  
  
### <a name="parameters"></a>Parámetros  
 `str`  
 El elemento de la cadena.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un valor de hash, que se calcula con el contenido de la cadena.  
  
##  <a name="a-nameinargtypea--cstringelementtraitsinargtype"></a><a name="inargtype"></a>CStringElementTraits::INARGTYPE  
 Tipo de datos que se va a usar para agregar elementos al objeto de la clase de colección.  
  
```
typedef T::PCXSTR INARGTYPE;
```  
  
##  <a name="a-nameoutargtypea--cstringelementtraitsoutargtype"></a><a name="outargtype"></a>CStringElementTraits::OUTARGTYPE  
 El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.  
  
```
typedef T& OUTARGTYPE;
```  
  
##  <a name="a-namerelocateelementsa--cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>CStringElementTraits::RelocateElements  
 Llame a esta función estática para reubicar `CString` elementos almacenados en un objeto de clase de colección.  
  
```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```  
  
### <a name="parameters"></a>Parámetros  
 `pDest`  
 Puntero al primer elemento que va a recibir los datos trasladados.  
  
 `pSrc`  
 Puntero al primer elemento para cambiar de posición.  
  
 `nElements`  
 El número de elementos que se va a cambiar la posición.  
  
### <a name="remarks"></a>Comentarios  
 Llama a esta función estática [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), que es suficiente para la mayoría de los tipos de datos. Si los objetos que se mueven contienen punteros a sus propios miembros, necesitará reemplazar esta función estática.  
  
## <a name="see-also"></a>Vea también  
 [Clase CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)   
 [Clase CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)

