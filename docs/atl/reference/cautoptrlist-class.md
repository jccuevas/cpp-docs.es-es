---
title: Clase CAutoPtrList
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList
- ATLCOLL/ATL::CAutoPtrList::CAutoPtrList
helpviewer_keywords:
- CAutoPtrList class
ms.assetid: 11de4aca-28b0-4ff2-a74a-cb602312ffbd
ms.openlocfilehash: 48c7ad6fe13c5f5fbbe5829c25ce1c27896841be
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318802"
---
# <a name="cautoptrlist-class"></a>Clase CAutoPtrList

Esta clase proporciona métodos útiles al construir una lista de punteros inteligentes.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<typename E>
class CAutoPtrList :
   public CAtlList<ATL::CAutoPtr<E>, CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Parámetros

*E*<br/>
El tipo de puntero.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtrList::CAutoPtrList](#cautoptrlist)|El constructor.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona un constructor y deriva métodos de [CAtlList](../../atl/reference/catllist-class.md) y [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) para ayudar a la creación de un objeto de lista que almacena punteros inteligentes. La clase [CAutoPtrArray](../../atl/reference/cautoptrarray-class.md) proporciona una función similar para un objeto de matriz.

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlList](../../atl/reference/catllist-class.md)

`CAutoPtrList`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cautoptrlistcautoptrlist"></a><a name="cautoptrlist"></a>CAutoPtrList::CAutoPtrList

El constructor.

```
CAutoPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
El tamaño del bloque, con un valor predeterminado de 10.

### <a name="remarks"></a>Observaciones

El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.

## <a name="see-also"></a>Consulte también

[Clase CAtlList](../../atl/reference/catllist-class.md)<br/>
[Clase CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
