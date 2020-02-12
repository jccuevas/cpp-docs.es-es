---
title: ITopologyNode (estructura)
ms.date: 11/04/2016
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
ms.openlocfilehash: 1b4cb6a856d6da7b8eee7f9cba1ad51e375c024d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140056"
---
# <a name="itopologynode-structure"></a>ITopologyNode (estructura)

Una interfaz a un nodo de topología definido por el Administrador de recursos. Un nodo contiene uno o varios recursos de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Members

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ITopologyNode:: Getexecutionresourcecount (](#getexecutionresourcecount)|Devuelve el número de recursos de ejecución agrupados en este nodo.|
|[ITopologyNode:: Getfirstexecutionresource (](#getfirstexecutionresource)|Devuelve el primer recurso de ejecución agrupado bajo este nodo en el orden de la enumeración.|
|[ITopologyNode:: GetId](#getid)|Devuelve el identificador único del Administrador de recursos para este nodo.|
|[ITopologyNode:: GetNext](#getnext)|Devuelve una interfaz al nodo de la topología siguiente en el orden de la enumeración.|
|[ITopologyNode:: Getnumanode (](#getnumanode)|Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.|

## <a name="remarks"></a>Observaciones

Esta interfaz se utiliza normalmente para recorrer la topología del sistema como se observa en el Administrador de recursos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ITopologyNode`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm. h

**Espacio de nombres:** simultaneidad

## <a name="getexecutionresourcecount"></a>ITopologyNode:: Getexecutionresourcecount ((método)

Devuelve el número de recursos de ejecución agrupados en este nodo.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El número de recursos de ejecución agrupados en este nodo.

## <a name="getfirstexecutionresource"></a>ITopologyNode:: Getfirstexecutionresource ((método)

Devuelve el primer recurso de ejecución agrupado bajo este nodo en el orden de la enumeración.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Primer recurso de ejecución agrupado bajo este nodo en orden de enumeración.

## <a name="getid"></a>ITopologyNode:: GetId (método)

Devuelve el identificador único del Administrador de recursos para este nodo.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único del Administrador de recursos para este nodo.

### <a name="remarks"></a>Observaciones

El Runtime de simultaneidad representa los subprocesos de hardware en el sistema en grupos de nodos de procesador. Normalmente, los nodos se derivan de la topología de hardware del sistema. Por ejemplo, todos los procesadores de un socket específico o un nodo NUMA específico pueden pertenecer al mismo nodo del procesador. El Administrador de recursos asigna identificadores únicos a estos nodos a partir de `0` hasta e incluye `nodeCount - 1`, donde `nodeCount` representa el número total de nodos de procesador del sistema.

El recuento de nodos puede obtenerse a partir de la función [getprocessornodecount (](concurrency-namespace-functions.md).

## <a name="getnext"></a>ITopologyNode:: GetNext (método)

Devuelve una interfaz al nodo de la topología siguiente en el orden de la enumeración.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una interfaz al siguiente nodo en el orden de la enumeración. Si no hay más nodos en el orden de enumeración de la topología del sistema, este método devolverá el valor `NULL`.

## <a name="getnumanode"></a>ITopologyNode:: Getnumanode ((método)

Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.

### <a name="remarks"></a>Observaciones

Un proxy de subproceso que se ejecuta en una raíz del procesador virtual que pertenece a este nodo tendrá afinidad por lo menos al nivel del nodo NUMA para el nodo NUMA que devuelve este método.

## <a name="see-also"></a>Consulte también

[concurrency (espacio de nombres)](concurrency-namespace.md)
