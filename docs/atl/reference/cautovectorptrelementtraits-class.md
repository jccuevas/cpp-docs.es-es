---
title: CAutoVectorPtrElementTraits (clase)
ms.date: 11/04/2016
f1_keywords:
- CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CAutoVectorPtrElementTraits::OUTARGTYPE
helpviewer_keywords:
- CAutoVectorPtrElementTraits class
ms.assetid: 16b81a56-55fb-46ca-b376-66a1884231a6
ms.openlocfilehash: 168670709470d7b7fdd77edb3c29d5a9f4049ca3
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57280737"
---
# <a name="cautovectorptrelementtraits-class"></a>CAutoVectorPtrElementTraits (clase)

Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones con nuevo vector de punteros inteligentes y eliminar operadores.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

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

|Name|Descripción|
|----------|-----------------|
|[CAutoVectorPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CAutoVectorPtrElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona métodos, funciones estáticas y definiciones de tipo para la creación de objetos de clase de colección que contiene punteros inteligentes. A diferencia de [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md), esta clase usa nuevo de vector y eliminar operadores.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CAutoVectorPtrElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="inargtype"></a>  CAutoVectorPtrElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef CAutoVectorPtr<T>& INARGTYPE;
```

##  <a name="outargtype"></a>  CAutoVectorPtrElementTraits::OUTARGTYPE

El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.

```
typedef T*& OUTARGTYPE;
```

## <a name="see-also"></a>Vea también

[CDefaultElementTraits (clase)](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CAutoVectorPtr (clase)](../../atl/reference/cautovectorptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
