---
title: Clase CDefaultCompareTraits
ms.date: 11/04/2016
f1_keywords:
- CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElements
- ATLCOLL/ATL::CDefaultCompareTraits::CompareElementsOrdered
helpviewer_keywords:
- CDefaultCompareTraits class
ms.assetid: a17e2740-e7b4-48f2-aeb7-c80ce84b63f7
ms.openlocfilehash: 8262800ef613424c37c53931d97dd4b1b1a71321
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327072"
---
# <a name="cdefaultcomparetraits-class"></a>Clase CDefaultCompareTraits

Esta clase proporciona funciones de comparación de elementos predeterminadas.

## <a name="syntax"></a>Sintaxis

```
template<typename T>
class CDefaultCompareTraits
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos que se almacenarán en la colección.

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDefaultCompareTraits::CompareElements](#compareelements)|(Estático) Llame a esta función para comparar dos elementos para la igualdad.|
|[CDefaultCompareTraits::CompareElementsOrdered](#compareelementsordered)|(Estático) Llame a esta función para determinar el elemento mayor y menor.|

## <a name="remarks"></a>Observaciones

Esta clase contiene dos funciones estáticas para comparar elementos almacenados en un objeto de clase de colección. Esta clase es utilizada por la [clase CDefaultElementTraits](../../atl/reference/cdefaultelementtraits-class.md).

Para obtener más información, vea Clases de [colección ATL](../../atl/atl-collection-classes.md).

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcoll.h

## <a name="cdefaultcomparetraitscompareelements"></a><a name="compareelements"></a>CDefaultCompareTraits::CompareElements

Llame a esta función para comparar dos elementos para la igualdad.

```
static bool CompareElements(const T& element1, const T& element2);
```

### <a name="parameters"></a>Parámetros

*element1*<br/>
El primer elemento.

*element2*<br/>
El segundo elemento.

### <a name="return-value"></a>Valor devuelto

Devuelve true si los elementos son iguales, false en caso contrario.

### <a name="remarks"></a>Observaciones

La implementación predeterminada de esta**==** función es el operador de igualdad ( ). Para objetos que no sean tipos de datos simples, es posible que sea necesario invalidar esta función.

## <a name="cdefaultcomparetraitscompareelementsordered"></a><a name="compareelementsordered"></a>CDefaultCompareTraits::CompareElementsOrdered

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

### <a name="remarks"></a>Observaciones

La implementación predeterminada de **==** **\<** esta **>** función utiliza los operadores , , y . Para objetos que no sean tipos de datos simples, es posible que sea necesario invalidar esta función.

## <a name="see-also"></a>Consulte también

[Información general de clases](../../atl/atl-class-overview.md)
