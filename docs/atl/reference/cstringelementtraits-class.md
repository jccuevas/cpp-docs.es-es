---
title: Clase CStringElementTraits
ms.date: 11/04/2016
f1_keywords:
- CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits
- CSTRINGT/ATL::CStringElementTraits::INARGTYPE
- CSTRINGT/ATL::CStringElementTraits::OUTARGTYPE
- CSTRINGT/ATL::CStringElementTraits::CompareElements
- CSTRINGT/ATL::CStringElementTraits::CompareElementsOrdered
- CSTRINGT/ATL::CStringElementTraits::CopyElements
- CSTRINGT/ATL::CStringElementTraits::Hash
- CSTRINGT/ATL::CStringElementTraits::RelocateElements
helpviewer_keywords:
- CStringElementTraits class
ms.assetid: 74d7134b-099d-4455-bf91-3e68ccbf95bc
ms.openlocfilehash: 078cfd5ff93bfcd8acc747904ea05e6a2e762bc1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330619"
---
# <a name="cstringelementtraits-class"></a>Clase CStringElementTraits

Esta clase proporciona funciones estáticas `CString` utilizadas por las clases de colección que almacenan objetos.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class CStringElementTraits
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la colección.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CStringElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CStringElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CStringElementTraits::CompareElements](#compareelements)|(Estático) Llame a esta función para comparar dos elementos de cadena para la igualdad.|
|[CStringElementTraits::CompareElementsOrdered](#compareelementsordered)|(Estático) Llame a esta función para comparar dos elementos de cadena.|
|[CStringElementTraits::CopyElements](#copyelements)|(Estático) Llame a esta `CString` función para copiar los elementos almacenados en un objeto de clase de colección.|
|[CStringElementTraits::Hash](#hash)|(Estático) Llame a esta función para calcular un valor hash para el elemento de cadena especificado.|
|[CStringElementTraits::RelocateElements](#relocateelements)|(Estático) Llame a esta `CString` función para reubicar los elementos almacenados en un objeto de clase de colección.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona funciones estáticas para copiar, mover y comparar cadenas y para crear un valor hash. Estas funciones son útiles cuando se usa una clase de colección para almacenar datos basados en cadenas. Utilice [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md) cuando se requieren comparaciones sin distinción entre mayúsculas y minúsculas. Utilice [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md) cuando los objetos de cadena se van a tratar como referencias.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** cstringt.h

## <a name="cstringelementtraitscompareelements"></a><a name="compareelements"></a>CStringElementTraits::CompareElements

Llame a esta función estática para comparar dos elementos de cadena para la igualdad.

```
static bool CompareElements(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer elemento de cadena.

*str2*<br/>
El segundo elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos son iguales, false en caso contrario.

## <a name="cstringelementtraitscompareelementsordered"></a><a name="compareelementsordered"></a>CStringElementTraits::CompareElementsOrdered

Llame a esta función estática para comparar dos elementos de cadena.

```
static int CompareElementsOrdered(INARGTYPE str1, INARGTYPE str2);
```

### <a name="parameters"></a>Parámetros

*str1*<br/>
El primer elemento de cadena.

*str2*<br/>
El segundo elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Cero si las cadenas son idénticas, < 0 si *str1* es menor que *str2*, o > 0 si *str1* es mayor que *str2*. El [CStringT::Compare](../../atl-mfc-shared/reference/cstringt-class.md#compare) método se utiliza para realizar las comparaciones.

## <a name="cstringelementtraitscopyelements"></a><a name="copyelements"></a>CStringElementTraits::CopyElements

Llame a esta `CString` función estática para copiar los elementos almacenados en un objeto de clase de colección.

```
static void CopyElements(
    T* pDest,
    const T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parámetros

*pDest*<br/>
Puntero al primer elemento que recibirá los datos copiados.

*pSrc*<br/>
Puntero al primer elemento que se va a copiar.

*nElementos*<br/>
Número de elementos que se van a copiar.

### <a name="remarks"></a>Observaciones

Los elementos de origen y destino no deben superponerse.

## <a name="cstringelementtraitshash"></a><a name="hash"></a>CStringElementTraits::Hash

Llame a esta función estática para calcular un valor hash para el elemento de cadena especificado.

```
static ULONG Hash(INARGTYPE str);
```

### <a name="parameters"></a>Parámetros

*Str*<br/>
El elemento de cadena.

### <a name="return-value"></a>Valor devuelto

Devuelve un valor hash, calculado con el contenido de la cadena.

## <a name="cstringelementtraitsinargtype"></a><a name="inargtype"></a>CStringElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef T::PCXSTR INARGTYPE;
```

## <a name="cstringelementtraitsoutargtype"></a><a name="outargtype"></a>CStringElementTraits::OUTARGTYPE

El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.

```
typedef T& OUTARGTYPE;
```

## <a name="cstringelementtraitsrelocateelements"></a><a name="relocateelements"></a>CStringElementTraits::RelocateElements

Llame a esta función estática para reubicar `CString` los elementos almacenados en un objeto de clase de colección.

```
static void RelocateElements(
    T* pDest,
    T* pSrc,
    size_t nElements);
```

### <a name="parameters"></a>Parámetros

*pDest*<br/>
Puntero al primer elemento que recibirá los datos reubicados.

*pSrc*<br/>
Puntero al primer elemento que se va a reubicar.

*nElementos*<br/>
El número de elementos que se van a reubicar.

### <a name="remarks"></a>Observaciones

Esta función estática llama a [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), que es suficiente para la mayoría de los tipos de datos. Si los objetos que se mueven contienen punteros a sus propios miembros, esta función estática tendrá que invalidarse.

## <a name="see-also"></a>Consulte también

[Clase CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)<br/>
[Clase CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
