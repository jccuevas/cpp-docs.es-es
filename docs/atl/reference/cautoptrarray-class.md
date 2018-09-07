---
title: CAutoPtrArray (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray
- ATLCOLL/ATL::CAutoPtrArray::CAutoPtrArray
dev_langs:
- C++
helpviewer_keywords:
- CAutoPtrArray class
ms.assetid: 880a70da-8c81-4427-8ac6-49aa8d424244
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d83f98de4f1d07fbebdd07186729453d2ef1d3b2
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/07/2018
ms.locfileid: "44108738"
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

[CAtlArray (clase)](../../atl/reference/catlarray-class.md)   
[CAutoPtrElementTraits (clase)](../../atl/reference/cautoptrelementtraits-class.md)   
[CAutoPtrList (clase)](../../atl/reference/cautoptrlist-class.md)   
[Información general de clases](../../atl/atl-class-overview.md)
