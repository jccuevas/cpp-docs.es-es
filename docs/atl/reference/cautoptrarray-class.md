---
title: CAutoPtrArray (clase)
ms.date: 11/04/2016
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
ms.openlocfilehash: c7a2a7e9592b120204582334f69e27e72cd7364f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50677947"
---
# <a name="cautoptrarray-class"></a>CAutoPtrArray (clase)

Esta clase proporciona métodos útiles al construir una matriz de punteros inteligentes.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template <typename E>
class CAutoPtrArray : public CAtlArray<
                        ATL::CAutoPtr<E>,
                        CAutoPtrElementTraits<E>>
```

#### <a name="parameters"></a>Parámetros

*E*<br/>
El tipo de puntero.

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CAutoPtrArray::CAutoPtrArray](#cautoptrarray)|El constructor.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona un constructor y se deriva de los métodos de [CAtlArray](../../atl/reference/catlarray-class.md) y [CAutoPtrElementTraits](../../atl/reference/cautoptrelementtraits-class.md) para facilitar la creación de un objeto de clase de colección almacenar punteros inteligentes.

Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`CAtlArray`

`CAutoPtrArray`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="cautoptrarray"></a>  CAutoPtrArray::CAutoPtrArray

El constructor.

```
CAutoPtrArray() throw();
```

### <a name="remarks"></a>Comentarios

Inicializa la matriz de puntero inteligente.

## <a name="see-also"></a>Vea también

[CAtlArray (clase)](../../atl/reference/catlarray-class.md)<br/>
[CAutoPtrElementTraits (clase)](../../atl/reference/cautoptrelementtraits-class.md)<br/>
[CAutoPtrList (clase)](../../atl/reference/cautoptrlist-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
