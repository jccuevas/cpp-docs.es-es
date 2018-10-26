---
title: CHeapPtrElementTraits (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits
- ATLCOLL/ATL::CHeapPtrElementTraits::INARGTYPE
- ATLCOLL/ATL::CHeapPtrElementTraits::OUTARGTYPE
dev_langs:
- C++
helpviewer_keywords:
- CHeapPtrElementTraits class
ms.assetid: 910e0e06-3c8b-4242-bf00-b57eb74fbc77
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 55217fa64c5fd28bf0839704307a0976bc647e5f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50077730"
---
# <a name="cheapptrelementtraits-class"></a>CHeapPtrElementTraits (clase)

Esta clase proporciona métodos, funciones estáticas y definiciones de tipos útiles al crear colecciones de punteros del montón.

> [!IMPORTANT]
>  Esta clase y sus miembros no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.

## <a name="syntax"></a>Sintaxis

```
template<typename T, class Allocator = ATL::CCRTAllocator>
class CHeapPtrElementTraits :
   public CDefaultElementTraits<ATL::CHeapPtr<T, Allocator>>
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de objeto que se almacenará en la clase de colección.

*Asignador*<br/>
La clase de asignación de memoria que utilice. El valor predeterminado es [CCRTAllocator](../../atl/reference/ccrtallocator-class.md).

## <a name="members"></a>Miembros

### <a name="public-typedefs"></a>Definiciones de tipos públicas

|Name|Descripción|
|----------|-----------------|
|[CHeapPtrElementTraits::INARGTYPE](#inargtype)|El tipo de datos que se usará para agregar elementos al objeto de clase de colección.|
|[CHeapPtrElementTraits::OUTARGTYPE](#outargtype)|El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.|

## <a name="remarks"></a>Comentarios

Esta clase proporciona métodos, funciones estáticas y definiciones de tipo para la creación de objetos de clase de colección que contiene los punteros de montón. La clase `CHeapPtrList` deriva `CHeapPtrElementTraits`.

Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CDefaultCompareTraits](../../atl/reference/cdefaultcomparetraits-class.md)

[CDefaultHashTraits](../../atl/reference/cdefaulthashtraits-class.md)

[CElementTraitsBase](../../atl/reference/celementtraitsbase-class.md)

[CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md)

`CHeapPtrElementTraits`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="inargtype"></a>  CHeapPtrElementTraits::INARGTYPE

El tipo de datos que se usará para agregar elementos al objeto de clase de colección.

```
typedef CHeapPtr<T, Allocator>& INARGTYPE;
```

##  <a name="outargtype"></a>  CHeapPtrElementTraits::OUTARGTYPE

El tipo de datos que se usará para recuperar los elementos de objeto de la clase de colección.

```
typedef T *& OUTARGTYPE;
```

## <a name="see-also"></a>Vea también

[CDefaultElementTraits (clase)](../../atl/reference/cdefaultelementtraits-class.md)<br/>
[CComHeapPtr (clase)](../../atl/reference/ccomheapptr-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
