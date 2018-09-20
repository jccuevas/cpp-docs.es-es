---
title: ITopologyExecutionResource (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs:
- C++
helpviewer_keywords:
- ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 60a0097aded73e3e0251d38daf5da71197668d3a
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46383797"
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
|[Itopologyexecutionresource](#getid)|Devuelve el Administrador de recursos del identificador único para este recurso de ejecución.|
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
