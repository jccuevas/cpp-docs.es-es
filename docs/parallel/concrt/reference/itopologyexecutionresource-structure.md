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
ms.openlocfilehash: 4bfb614d5ffd6a399fae33d38a50cee62f17c208
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57272859"
---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource (Estructura)

Una interfaz a un recurso de ejecución definido por el Administrador de recursos.

## <a name="syntax"></a>Sintaxis

```
struct ITopologyExecutionResource;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[ITopologyExecutionResource::GetId](#getid)|Devuelve el Administrador de recursos del identificador único para este recurso de ejecución.|
|[ITopologyExecutionResource::GetNext](#getnext)|Devuelve una interfaz para el siguiente recurso de ejecución en el orden de enumeración.|

## <a name="remarks"></a>Comentarios

Esta interfaz se utiliza normalmente para recorrer observado por el Administrador de recursos de la topología del sistema.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ITopologyExecutionResource`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

##  <a name="getid"></a>  Itopologyexecutionresource (método)

Devuelve el Administrador de recursos del identificador único para este recurso de ejecución.

```
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El Administrador de recursos del identificador único para este recurso de ejecución.

##  <a name="getnext"></a>  Itopologyexecutionresource (método)

Devuelve una interfaz para el siguiente recurso de ejecución en el orden de enumeración.

```
virtual ITopologyExecutionResource *GetNext() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Interfaz para el siguiente recurso de ejecución en el orden de enumeración. Si no hay ningún nodo más en orden de enumeración del nodo al que pertenece este recurso de ejecución, este método devolverá el valor `NULL`.

## <a name="see-also"></a>Vea también

[concurrency (espacio de nombres)](concurrency-namespace.md)
