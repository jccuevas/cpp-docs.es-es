---
title: Clase CAutoPtrArray
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: 11f39eac8b8d080fd840f6454f393e33ebcb9e1c
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82167668"
---
# <a name="cautoptrarray-class"></a>Clase CAutoPtrArray

Esta clase proporciona métodos útiles al construir una matriz de punteros inteligentes.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

### <a name="parameters"></a>Parámetros

*E:.*<br/>
Tipo de puntero.

## <a name="members"></a>Members

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|El constructor.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona un constructor y deriva métodos de [CAtlArray](../../atl/reference/catlarray-class.md) y [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) para ayudar a la creación de un objeto de clase de colección que almacena punteros inteligentes.

Para obtener más información, vea [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll. h

## <a name="cautoptrarraycautoptrarray"></a><a name="cautoptrarray"></a>CAutoPtrArray::CAutoPtrArray

El constructor.

```cpp
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Observaciones

Inicializa la matriz de puntero inteligente.

## <a name="see-also"></a>Consulte también

[CAtlArray (clase)](../../atl/reference/catlarray-class.md)<br/>
[Clase CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[Clase CAutoPtrList](../../atl/reference/cautoptrlist-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
