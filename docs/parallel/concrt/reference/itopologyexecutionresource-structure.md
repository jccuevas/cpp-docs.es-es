---
title: ITopologyExecutionResource (estructura)
ms.date: 11/04/2016
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
ms.openlocfilehash: 82193a9b592cded96f3726cbabd6cf646eaa27c8
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140066"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource (estructura)

Una interfaz a un recurso de ejecución definido por el Administrador de recursos.

## <a name="syntax"></a>Sintaxis

```cpp
struct ITopologyExecutionResource;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[Itopologyexecutionresource (:: GetId](#getid)|Devuelve el identificador único del Administrador de recursos para este recurso de ejecución.|
|[Itopologyexecutionresource (:: GetNext](#getnext)|Devuelve una interfaz al siguiente recurso de ejecución en el orden de la enumeración.|

## <a name="remarks"></a>Observaciones

Esta interfaz se utiliza normalmente para recorrer la topología del sistema como se observa en el Administrador de recursos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ITopologyExecutionResource`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="getid"></a>Itopologyexecutionresource (:: GetId (método)

Devuelve el identificador único del Administrador de recursos para este recurso de ejecución.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único del Administrador de recursos para este recurso de ejecución.

## <a name="getnext"></a>Itopologyexecutionresource (:: GetNext (método)

Devuelve una interfaz al siguiente recurso de ejecución en el orden de la enumeración.

```cpp
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una interfaz al siguiente recurso de ejecución en orden de enumeración. Si no hay más nodos en el orden de enumeración del nodo al que pertenece este recurso de ejecución, este método devolverá el valor `NULL`.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
