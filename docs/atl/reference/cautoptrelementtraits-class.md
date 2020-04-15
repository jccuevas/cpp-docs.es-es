---
title: Clase CAutoPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits
- ATLCOLL/ATL::CAutoPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoPtrElementTraits class
ms.assetid: 777c1b14-6ab7-491f-b9a5-be149e71d4a2
ms.openlocfilehash: ac29116dc9beedf587c42cc0e52f8c9dbaf3d782
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318882"
---
# <a name="cautoptrelementtraits-class"></a>Clase CAutoPtrElementTraits

Esta clase proporciona métodos, funciones estáticas y typedefs útiles al crear colecciones de punteros inteligentes.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CAutoPtrElementTraits
    : public CDefaultElementTraits<ATL::CAutoPtr<T>>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de puntero.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CAutoPtrElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos, funciones estáticas y typedefs para ayudar a la creación de objetos de clase de colección que contienen punteros inteligentes. Las clases [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) y [CAutoPtrList](../../atl/reference/cautoptrlist-class.md) derivan de `CAutoPtrElementTraits`. Si crea una colección de punteros inteligentes que requiere vector new y delete operadores, utilice [CAutoVectorPtrElementTraits](../../atl/reference/cautovectorptrelementtraits-class.md) en su lugar.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoPtrElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cautoptrelementtraitsinargtype"></a><a name="inargtype"></a>CAutoPtrElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef CAutoPtr<T>& INARGTYPE;
```

## <a name="cautoptrelementtraitsoutargtype"></a><a name="outargtype"></a>CAutoPtrElementTraits::OUTARGTYPE

El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Consulte también

[Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
