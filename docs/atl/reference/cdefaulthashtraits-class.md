---
title: CDefaultHashTraits (clase)
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: c8896ce27afc40ad095e02a2453628ffc05900da
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466149"
---
# <a name="cdefaulthashtraits-class"></a>CDefaultHashTraits (clase)

Esta clase proporciona una función estática para calcular los valores hash.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenará en la colección.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Estático) Llame a esta función para calcular un valor hash para un elemento determinado.|

## <a name="remarks"></a>Comentarios

Esta clase contiene una sola función estática que devuelve un valor hash para un elemento determinado. Esta clase se utiliza por la [CDefaultElementTraits (clase)](../../atl/reference/cdefaultelementtraits-class.md).

Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="hash"></a>  CDefaultHashTraits::Hash

Llame a esta función para calcular un valor hash para un elemento determinado.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Parámetros

*Elemento*<br/>
El elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor hash.

### <a name="remarks"></a>Comentarios

El algoritmo hash predeterminado es muy sencillo: el valor devuelto es el número de elemento. Reemplace esta función si es necesario un algoritmo más complicado.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
