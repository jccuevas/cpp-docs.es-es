---
title: Clase CHeapPtrElementTraits
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
ms.openlocfilehash: f09da968b264463eba759372e4e0756397e9978e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326872"
---
# <a name="cheapptrelementtraits-class"></a>Clase CHeapPtrElementTraits

Esta clase proporciona métodos, funciones estáticas y typedefs útiles al crear colecciones de punteros de montón.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que se va a almacenar en la clase de colección.

*Asignador*<br/>
La clase de asignación de memoria que se va a utilizar. El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona métodos, funciones estáticas y typedefs para ayudar a la creación de objetos de clase de colección que contienen punteros de montón. La `CHeapPtrList` clase deriva `CHeapPtrElementTraits`de .

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cheapptrelementtraitsinargtype"></a><a name="inargtype"></a>CHeapPtrElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

## <a name="cheapptrelementtraitsoutargtype"></a><a name="outargtype"></a>CHeapPtrElementTraits::OUTARGTYPE

El tipo de datos que se va a utilizar para recuperar elementos del objeto de clase de colección.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Consulte también

[Clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[Clase CComHeapPtr](../../atl/reference/ccomheapptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
