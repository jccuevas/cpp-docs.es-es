---
title: CDefaultCompareTraits (clase)
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: c5f4ab3737838af11501c4a0f2037b57087939c9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57273600"
---
# <a name="cdefaultcomparetraits-class"></a>CDefaultCompareTraits (clase)

Esta clase proporciona funciones de comparación de elemento de predeterminado.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenará en la colección.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Estático) Llame a esta función para comparar la igualdad de dos elementos.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Estático) Llame a esta función para determinar el elemento mayor y menor.|

## <a name="remarks"></a>Comentarios

Esta clase contiene dos funciones estáticas para comparar los elementos almacenados en un objeto de clase de colección. Esta clase se utiliza por la [CDefaultElementTraits (clase)](../../atl/reference/cdefaultelementtraits-class.md).

Para obtener más información, consulte [clases de colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

##  <a name="compareelements"></a>  CDefaultCompareTraits::CompareElements

Llame a esta función para comparar la igualdad de dos elementos.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parámetros

*element1*<br/>
El primer elemento.

*element2*<br/>
El segundo elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos si no son iguales, es false.

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función es la igualdad (**==**) operador. Para objetos que no sean de tipos de datos simples, esta función es posible que deba reemplazarse.

##  <a name="compareelementsordered"></a>  CDefaultCompareTraits::CompareElementsOrdered

Llame a esta función para determinar el elemento mayor y menor.

```
static int CompareElementsOrdered(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parámetros

*element1*<br/>
El primer elemento.

*element2*<br/>
El segundo elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve un entero basado en la tabla siguiente:

|Condición|Valor devuelto|
|---------------|------------------|
|*element1* < *element2*|<0|
|*element1* == *element2*|0|
|*element1* > *element2*|>0|

### <a name="remarks"></a>Comentarios

La implementación predeterminada de esta función usa el **==**, **\<**, y **>** operadores. Para objetos que no sean de tipos de datos simples, esta función es posible que deba reemplazarse.

## <a name="see-also"></a>Vea también

[Información general de clases](../../atl/atl-class-overview.md)
