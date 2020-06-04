---
title: Clase CStringRefElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits
- ATLCOLL/ATL::CStringRefElementTraits::CompareElements
- ATLCOLL/ATL::CStringRefElementTraits::CompareElementsOrdered
- ATLCOLL/ATL::CStringRefElementTraits::Hash
helpviewer_keywords:
- CStringRefElementTraits class
ms.assetid: cc15062d-5627-46cc-ac2b-1744afdc2dbd
ms.openlocfilehash: b4dd76b9592b255a1553be3ca7a249f58fb2672e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330580"
---
# <a name="cstringrefelementtraits-class"></a>Clase CStringRefElementTraits

Esta clase proporciona funciones estáticas relacionadas con cadenas almacenadas en objetos de clase de colección. Los objetos de cadena se tratan como referencias.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class CStringRefElementTraits : public CElementTraitsBase<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la colección.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringRefElementTraits::CompareElements](#compareelements)|Llame a esta función estática para comparar dos elementos de cadena para la igualdad.|
|[CStringRefElementTraits::CompareElementsOrdered](#compareelementsordered)|Llame a esta función estática para comparar dos elementos de cadena.|
|[CStringRefElementTraits::Hash](#hash)|Llame a esta función estática para calcular un valor hash para el elemento de cadena especificado.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona funciones estáticas para comparar cadenas y crear un valor hash. Estas funciones son útiles cuando se usa una clase de colección para almacenar datos basados en cadenas. A diferencia de [CStringElementTraits](../../atl/reference/cstringelementtraits-class.md) y [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md), `CStringRefElementTraits` hace que `CString` los argumentos se pasen como referencias **const.** `CString&`

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

`CStringRefElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cstringrefelementtraitscompareelements"></a><a name="compareelements"></a>CStringRefElementTraits::CompareElements

Llame a esta función estática para comparar dos elementos de cadena para la igualdad.

```
static bool CompareElements(INARGTYPE element1, INARGTYPE element2) throw();
```

### <a name="parameters"></a>Parámetros

*element1*<br/>
El primer elemento de cadena.

*element2*<br/>
El segundo elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos son iguales, false en caso contrario.

## <a name="cstringrefelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringRefElementTraits::CompareElementsOrdered

Llame a esta función estática para comparar dos elementos de cadena.

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

## <a name="cstringrefelementtraitshash"></a><a name="hash"></a>CStringRefElementTraits::Hash

Llame a esta función estática para calcular un valor hash para el elemento de cadena especificado.

```
static ULONG Hash(INARGTYPE str) throw();
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
El elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor hash, calculado con el contenido de la cadena.

## <a name="see-also"></a>Consulte también

[Clase CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
