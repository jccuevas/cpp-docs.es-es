---
title: Clase CHeapPtrList
ms.date: 11/04/2016
f1_keywords:
- CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList
- ATLCOLL/ATL::CHeapPtrList::CHeapPtrList
helpviewer_keywords:
- CHeapPtrList class
ms.assetid: cc70e585-362a-4007-81db-c705eb181226
ms.openlocfilehash: 0500ab8f76049aeaf1c89355ea5450a93243b734
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326856"
---
# <a name="cheapptrlist-class"></a>Clase CHeapPtrList

Esta clase proporciona métodos útiles al construir una lista de punteros de montón.

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template<typename E, class Allocator = ATL::CCRTAllocator>
class CHeapPtrList
   : public CAtlList<ATL::CHeapPtr<E, Allocator>,
                     CHeapPtrElementTraits<E, Allocator>>
```

#### <a name="parameters"></a>Parámetros

*E*<br/>
El tipo de objeto que se va a almacenar en la clase de colección.

*Asignador*<br/>
La clase de asignación de memoria que se va a utilizar. El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CHeapPtrList::CHeapPtrList](#cheapptrlist)|El constructor.|

## <a name="remarks"></a>Observaciones

Esta clase proporciona un constructor y deriva métodos de [CAtlList](../../atl/reference/catllist-class.md) y [CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md) para ayudar a la creación de un objeto de clase de colección que almacena punteros de montón.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlList](../../atl/reference/catllist-class.md)

`CHeapPtrList`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cheapptrlistcheapptrlist"></a><a name="cheapptrlist"></a>CHeapPtrList::CHeapPtrList

El constructor.

```
CHeapPtrList(UINT nBlockSize = 10) throw();
```

### <a name="parameters"></a>Parámetros

*nBlockSize*<br/>
Tamaño de bloque.

### <a name="remarks"></a>Observaciones

El tamaño de bloque es una medida de la cantidad de memoria asignada cuando se requiere un nuevo elemento. Los tamaños de bloque más grandes reducen las llamadas a rutinas de asignación de memoria, pero usan más recursos.

## <a name="see-also"></a>Consulte también

[Clase CAtlList](../../atl/reference/catllist-class.md)<br/>
[Clase CHeapPtr](../../atl/reference/cheapptr-class.md)<br/>
[Clase CHeapPtrElementTraits](../../atl/reference/cheapptrelementtraits-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
