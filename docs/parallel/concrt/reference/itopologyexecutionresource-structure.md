---
title: ITopologyExecutionResource (Estructura)
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 2c9221cab1ac2d48bd099a769188e4bee797823c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368144"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource (Estructura)

Una interfaz a un recurso de ejecución definido por el Administrador de recursos.

## <a name="syntax"></a>Sintaxis

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ITopologyExecutionResource::GetId](#getid)|Devuelve el identificador único de Resource Manager para este recurso de ejecución.|
|[ITopologyExecutionResource::GetNext](#getnext)|Devuelve una interfaz al siguiente recurso de ejecución en orden de enumeración.|

## <a name="remarks"></a>Observaciones

Esta interfaz se utiliza normalmente para recorrer la topología del sistema según lo observado por el Administrador de recursos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ITopologyExecutionResource`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="itopologyexecutionresourcegetid-method"></a><a name="getid"></a>ITopologyExecutionResource::GetId Método

Devuelve el identificador único de Resource Manager para este recurso de ejecución.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único del Administrador de recursos para este recurso de ejecución.

## <a name="itopologyexecutionresourcegetnext-method"></a><a name="getnext"></a>ITopologyExecutionResource::GetNext Método

Devuelve una interfaz al siguiente recurso de ejecución en orden de enumeración.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una interfaz para el siguiente recurso de ejecución en orden de enumeración. Si no hay más nodos en orden de enumeración del nodo al que `NULL`pertenece este recurso de ejecución, este método devolverá el valor .

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
