---
title: CAutoVectorPtrElementTraits (Clase)
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 956fe39c4d3ba89bb9def2f996dca59905753edb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318755"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits (Clase)

Esta clase proporciona métodos, funciones estáticas y typedefs útiles al crear colecciones de punteros inteligentes mediante vector new y delete operadores.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class CAutoVectorPtrElementTraits :
   public CDefaultElementTraits<ATL::CAutoVectorPtr<T>>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de puntero.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos, funciones estáticas y typedefs para ayudar a la creación de objetos de clase de colección que contienen punteros inteligentes. A diferencia de [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), esta clase utiliza vector new y delete operadores.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cautovectorptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoVectorPtrElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

## <a name="cautovectorptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoVectorPtrElementTraits::OUTARGTYPE

El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Consulte también

[Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Clase CAutoVectorPtr](../../atl/reference/cautovectorptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
