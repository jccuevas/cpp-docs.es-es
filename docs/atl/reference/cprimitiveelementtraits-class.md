---
title: Clase CPrimitiveElementTraits
ms.date: 11/04/2016
f1_keywords:
- CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits
- ATLCOLL/ATL::CPrimitiveElementTraits::INARGTYPE
- ATLCOLL/ATL::CPrimitiveElementTraits::OUTARGTYPE
helpviewer_keywords:
- CPrimitiveElementTraits class
ms.assetid: 21c1cea8-2c5a-486c-b65c-85490f3ed4e6
ms.openlocfilehash: 6b45d93420d1832091cc451a3e6eb309f61d07a3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331434"
---
# <a name="cprimitiveelementtraits-class"></a>Clase CPrimitiveElementTraits

Esta clase proporciona métodos y funciones predeterminados para una clase de colección compuesta de tipos de datos primitivos.

## <a name="syntax"></a>Sintaxis

```
template <typename T>
class CPrimitiveElementTraits : public CDefaultElementTraits<T>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en el objeto de clase de colección.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CPrimitiveElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CPrimitiveElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona funciones estáticas predeterminadas y métodos para mover, copiar, comparar y aplicar hash a elementos de tipo de datos primitivos almacenados en un objeto de clase de colección.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CPrimitiveElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cprimitiveelementtraitsinargtype"></a><a name="inargtype"></a>CPrimitiveElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef T INARGTYPE;
```

## <a name="cprimitiveelementtraitsoutargtype"></a><a name="outargtype"></a>CPrimitiveElementTraits::OUTARGTYPE

El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.

```
typedef T& OUTARGTYPE;
```

## <a name="see-also"></a>Consulte también

[Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
