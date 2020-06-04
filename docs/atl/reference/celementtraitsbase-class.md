---
title: Clase CElementTraitsBase
ms.date: 11/04/2016
f1_keywords:
- CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase
- ATLCOLL/ATL::CElementTraitsBase::INARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::OUTARGTYPE
- ATLCOLL/ATL::CElementTraitsBase::CopyElements
- ATLCOLL/ATL::CElementTraitsBase::RelocateElements
helpviewer_keywords:
- CElementTraitsBase class
ms.assetid: 75284caf-347e-4355-a7d8-efc708dd514a
ms.openlocfilehash: 5a29e8778cf2f3400df25b55574950a005bad995
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327002"
---
# <a name="celementtraitsbase-class"></a>Clase CElementTraitsBase

Esta clase proporciona métodos de copia y movimiento predeterminados para una clase de colección.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CElementTraitsBase
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la colección.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CElementTraitsBase::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CElementTraitsBase::OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CElementTraitsBase::CopyElements](#copyelements)|Llame a este método para copiar los elementos almacenados en un objeto de clase de colección.|
|[CElementTraitsBase::RelocateElements](#relocateelements)|Llame a este método para reubicar los elementos almacenados en un objeto de clase de colección.|

## <a name="remarks"></a>Observaciones

Esta clase base define métodos para copiar y reubicar elementos en una clase de colección. Es utilizado por las clases [CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md), [CStringRefElementTraits](../../atl/reference/cstringrefelementtraits-class.md)y [CStringElementTraitsI](../../atl/reference/cstringelementtraitsi-class.md).

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="celementtraitsbasecopyelements"></a><a name="copyelements"></a>CElementTraitsBase::CopyElements

Llame a este método para copiar los elementos almacenados en un objeto de clase de colección.

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

## <a name="celementtraitsbaseinargtype"></a><a name="inargtype"></a>CElementTraitsBase::INARGTYPE

El tipo de datos que se usará para agregar elementos a la colección.

```
typedef const T& INARGTYPE;
```

## <a name="celementtraitsbaseoutargtype"></a><a name="outargtype"></a>CElementTraitsBase::OUTARGTYPE

El tipo de datos que se usará para recuperar elementos de la colección.

```
typedef T& OUTARGTYPE;
```

## <a name="celementtraitsbaserelocateelements"></a><a name="relocateelements"></a>CElementTraitsBase::RelocateElements

Llame a este método para reubicar los elementos almacenados en un objeto de clase de colección.

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

Este método llama a [memmove](../../c-runtime-library/reference/memmove-wmemmove.md), que es suficiente para la mayoría de los tipos de datos. Si los objetos que se mueven contienen punteros a sus propios miembros, este método tendrá que reemplazarse.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
