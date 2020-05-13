---
title: Clase CComQIPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits
- ATLCOLL/ATL::CComQIPtrElementTraits::INARGTYPE
helpviewer_keywords:
- CComQIPtrElementTraits class
ms.assetid: 9df9250a-5413-4362-b133-332932a597c4
ms.openlocfilehash: 19f2669c157310be02f746672b22f6c0ed005075
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327410"
---
# <a name="ccomqiptrelementtraits-class"></a>Clase CComQIPtrElementTraits

Esta clase proporciona métodos, funciones estáticas y typedefs útiles al crear colecciones de punteros de interfaz COM.

## <a name="syntax"></a>Sintaxis

```
template<typename I, const IID* piid=& __uuidof(I)>
class CComQIPtrElementTraits :
   public CDefaultElementTraits<ATL::CComQIPtr<I, piid>>
```

#### <a name="parameters"></a>Parámetros

*Ⅰ*<br/>
Interfaz COM que especifica el tipo de puntero que se va a almacenar.

*piid*<br/>
Un puntero al IID de *I*.

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CComQIPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|

## <a name="remarks"></a>Observaciones

Esta clase deriva métodos y proporciona un typedef útil al crear una clase de colección de [CComQIPtr](../../atl/reference/ccomqiptr-class.md) COM objetos de puntero de interfaz. Esta clase es utilizada por las clases [CInterfaceArray](../../atl/reference/cinterfacearray-class.md) y [CInterfaceList.](../../atl/reference/cinterfacelist-class.md)

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CComQIPtrElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="ccomqiptrelementtraitsinargtype"></a><a name="inargtype"></a>CComQIPtrElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef I* INARGTYPE;
```

## <a name="see-also"></a>Consulte también

[Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
