---
title: Clase CDefaultHashTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits
- ATLCOLL/ATL::CDefaultHashTraits::Hash
helpviewer_keywords:
- CDefaultHashTraits class
ms.assetid: d8ec4b37-6d58-447b-a0c1-8580c5b1ab85
ms.openlocfilehash: 43932092621d44cfc8b07270df92e2765665f23f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327082"
---
# <a name="cdefaulthashtraits-class"></a>Clase CDefaultHashTraits

Esta clase proporciona una función estática para calcular valores hash.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CDefaultHashTraits
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la colección.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDefaultHashTraits::Hash](#hash)|(Estático) Llame a esta función para calcular un valor hash para un elemento determinado.|

## <a name="remarks"></a>Observaciones

Esta clase contiene una sola función estática que devuelve un valor hash para un elemento determinado. Esta clase es utilizada por la [clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cdefaulthashtraitshash"></a><a name="hash"></a>CDefaultHashTraits::Hash

Llame a esta función para calcular un valor hash para un elemento determinado.

```
static ULONG Hash(const T& element) throw();
```

### <a name="parameters"></a>Parámetros

*Elemento*<br/>
El elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve el valor hash.

### <a name="remarks"></a>Observaciones

El algoritmo hash predeterminado es muy simple: el valor devuelto es el número de elemento. Invalide esta función si se requiere un algoritmo más complicado.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
