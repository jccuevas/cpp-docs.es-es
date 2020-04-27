---
title: Clase CAtlFileMapping
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: 7516349e4ec54d8cb90fa6ff23b0ded954aa043b
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168129"
---
# <a name="catlfilemapping-class"></a>Clase CAtlFileMapping

Esta clase representa un archivo asignado a la memoria, agregando un operador de conversión a los métodos de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en el Windows Runtime.

## <a name="syntax"></a>Sintaxis

```cpp
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos utilizado para el operador de conversión.

## <a name="members"></a>Members

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFileMapping:: Operator T *](#operator_t_star)|Permite la conversión implícita `CAtlFileMapping` de objetos `T*`en.|

## <a name="remarks"></a>Observaciones

Esta clase agrega un operador de conversión único para permitir la conversión `CAtlFileMapping` implícita de `T*`objetos a. La clase base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md), proporciona otros miembros.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile. h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping:: Operator T *

Permite la conversión implícita `CAtlFileMapping` de objetos `T*`en.

```cpp
operator T*() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve un `T*` puntero al principio del archivo asignado a la memoria.

### <a name="remarks"></a>Observaciones

Llama a [CAtlFileMappingBase:: GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) y reinterpreta el puntero devuelto como `T*` donde *T* es el tipo que se usa como parámetro de plantilla de esta clase.

## <a name="see-also"></a>Consulte también

[Clase CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
