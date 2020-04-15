---
title: CAtlFileMapping Clase
ms.date: 11/04/2016
f1_keywords:
- CAtlFileMapping
- atlfile/ATL::CAtlFileMapping
helpviewer_keywords:
- CAtlFileMapping class
ms.assetid: 899fc058-e05e-48b5-aca9-340403bb9e26
ms.openlocfilehash: ca46ccdacf5ea24f1de26cdc75bf808c4ecfaa40
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318955"
---
# <a name="catlfilemapping-class"></a>CAtlFileMapping Clase

Esta clase representa un archivo asignado a memoria, agregando un operador de conversión a los métodos de [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md).

> [!IMPORTANT]
> Esta clase y sus miembros no se pueden usar en aplicaciones que se ejecutan en Windows Runtime.

## <a name="syntax"></a>Sintaxis

```
template <typename T = char>
class CAtlFileMapping : public CAtlFileMappingBase
```

#### <a name="parameters"></a>Parámetros

*T*<br/>
El tipo de datos utilizado para el operador de conversión.

## <a name="members"></a>Miembros

### <a name="public-operators"></a>Operadores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CAtlFileMapping::operator T*](#operator_t_star)|Permite la `CAtlFileMapping` conversión `T*`implícita de objetos a .|

## <a name="remarks"></a>Observaciones

Esta clase agrega un único operador de `CAtlFileMapping` conversión para permitir la conversión implícita de objetos a `T*`. La clase base, [CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md), proporciona otros miembros.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

[CAtlFileMappingBase](../../atl/reference/catlfilemappingbase-class.md)

`CAtlFileMapping`

## <a name="requirements"></a>Requisitos

**Encabezado:** atlfile.h

## <a name="catlfilemappingoperator-t"></a><a name="operator_t_star"></a>CAtlFileMapping::operator T*

Permite la `CAtlFileMapping` conversión `T*`implícita de objetos a .

```
operator T*() const throw();
```

### <a name="return-value"></a>Valor devuelto

Devuelve `T*` un puntero al inicio del archivo asignado a memoria.

### <a name="remarks"></a>Observaciones

Llama a [CAtlFileMappingBase::GetData](../../atl/reference/catlfilemappingbase-class.md#getdata) y reinterpreta `T*` el puntero devuelto como un donde *T* es el tipo utilizado como el parámetro de plantilla de esta clase.

## <a name="see-also"></a>Consulte también

[CAtlFileMappingBase (clase)](../../atl/reference/catlfilemappingbase-class.md)<br/>
[Información general de clases](../../atl/atl-class-overview.md)
