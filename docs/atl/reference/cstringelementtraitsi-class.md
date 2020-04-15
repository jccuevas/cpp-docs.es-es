---
title: Clase CStringElementTraitsI
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI
- ATLCOLL/ATL::CStringElementTraitsI::INARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::OUTARGTYPE
- ATLCOLL/ATL::CStringElementTraitsI::CompareElements
- ATLCOLL/ATL::CStringElementTraitsI::CompareElementsOrdered
- ATLCOLL/ATL::CStringElementTraitsI::Hash
helpviewer_keywords:
- CStringElementTraitsI class
ms.assetid: c23f92b1-91e5-400f-96ed-258b02622b7a
ms.openlocfilehash: 32980e19443cb17a3a688c85ff21195c60ed2124
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330588"
---
# <a name="cstringelementtraitsi-class"></a>Clase CStringElementTraitsI

Esta clase proporciona funciones estáticas relacionadas con cadenas almacenadas en objetos de clase de colección. Es similar a [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md), pero realiza comparaciones sin distinción entre mayúsculas y minúsculas.

## <a name="syntax"></a>Sintaxis

```
template <typename T, class CharTraits = CDefaultCharTraits<T ::XCHAR>>
class CStringElementTraitsI : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la colección.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CStringElementTraitsI::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CStringElementTraitsI::OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringElementTraitsI::CompareElements](#compareelements)|Llame a esta función estática para comparar dos elementos de cadena para la igualdad, ignorando las diferencias en caso.|
|[CStringElementTraitsI::CompareElementsOrdered](#compareelementsordered)|Llame a esta función estática para comparar dos elementos de cadena, ignorando las diferencias en caso.|
|[CStringElementTraitsI::Hash](#hash)|Llame a esta función estática para calcular un valor hash para el elemento de cadena especificado.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona funciones estáticas para comparar cadenas y crear un valor hash. Estas funciones son útiles cuando se usa una clase de colección para almacenar datos basados en cadenas. Utilice [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena se van a tratar como referencias.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringElementTraitsI`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cstringelementtraitsicompareelements"></a><a name="compareelements"></a>CStringElementTraitsI::CompareElements

Llame a esta función estática para comparar dos elementos de cadena para la igualdad, ignorando las diferencias en caso.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer elemento de cadena.

*str2*<br/>
El segundo elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos son iguales, false en caso contrario.

### <a name="remarks"></a>Observaciones

Las comparaciones no distinguen mayúsculas de minúsculas.

## <a name="cstringelementtraitsicompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraitsI::CompareElementsOrdered

Llame a esta función estática para comparar dos elementos de cadena, ignorando las diferencias en caso.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2) throw();
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer elemento de cadena.

*str2*<br/>
El segundo elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas, < 0 si *str1* es menor que *str2*, o > 0 si *str1* es mayor que *str2*. El [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) método se utiliza para realizar las comparaciones.

### <a name="remarks"></a>Observaciones

Las comparaciones no distinguen mayúsculas de minúsculas.

## <a name="cstringelementtraitsihash"></a><a name="hash"></a>CStringElementTraitsI::Hash

Llame a esta función estática para calcular un valor hash para el elemento de cadena especificado.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
El elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor hash, calculado con el contenido de la cadena.

## <a name="cstringelementtraitsiinargtype"></a><a name="inargtype"></a>CStringElementTraitsI::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsioutargtype"></a><a name="outargtype"></a>CStringElementTraitsI::OUTARGTYPE

El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Consulte también

[Clase CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)<br/>
[Clase CStringElementTraits](../../atl/reference/cstringelementtraits-class.md)
