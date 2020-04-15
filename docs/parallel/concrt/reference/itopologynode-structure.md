---
title: ITopologyNode (Estructura)
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
ms.openlocfilehash: 7cb815c4f7dc5ad09e8d352abc3f3375b8d9e205
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368100"
---
# <a name="itopologynode-structure"></a>ITopologyNode (Estructura)

Una interfaz a un nodo de topología definido por el Administrador de recursos. Un nodo contiene uno o varios recursos de ejecución.

## <a name="syntax"></a>Sintaxis

```cpp
struct ITopologyNode;
```

## <a name="members"></a>Miembros

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Devuelve el número de recursos de ejecución agrupados en este nodo.|
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Devuelve el primer recurso de ejecución agrupado bajo este nodo en orden de enumeración.|
|[ITopologyNode::GetId](#getid)|Devuelve el identificador único de Resource Manager para este nodo.|
|[ITopologyNode::GetNext](#getnext)|Devuelve una interfaz al siguiente nodo de topología en orden de enumeración.|
|[ITopologyNode::GetNumaNode](#getnumanode)|Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.|

## <a name="remarks"></a>Observaciones

Esta interfaz se utiliza normalmente para recorrer la topología del sistema según lo observado por el Administrador de recursos.

## <a name="inheritance-hierarchy"></a>Jerarquía de herencia

`ITopologyNode`

## <a name="requirements"></a>Requisitos

**Encabezado:** concrtrm.h

**Espacio de nombres:** simultaneidad

## <a name="itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>Método ITopologyNode::GetExecutionResourceCount

Devuelve el número de recursos de ejecución agrupados en este nodo.

```cpp
virtual unsigned int GetExecutionResourceCount() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El número de recursos de ejecución agrupados en este nodo.

## <a name="itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>Método ITopologyNode::GetFirstExecutionResource

Devuelve el primer recurso de ejecución agrupado bajo este nodo en orden de enumeración.

```cpp
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```

### <a name="return-value"></a>Valor devuelto

El primer recurso de ejecución agrupado bajo este nodo en orden de enumeración.

## <a name="itopologynodegetid-method"></a><a name="getid"></a>ITopologyNode::GetId Método

Devuelve el identificador único de Resource Manager para este nodo.

```cpp
virtual unsigned int GetId() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Identificador único del Administrador de recursos para este nodo.

### <a name="remarks"></a>Observaciones

El Runtime de simultaneidad representa subprocesos de hardware en el sistema en grupos de nodos de procesador. Los nodos se derivan generalmente de la topología de hardware del sistema. Por ejemplo, todos los procesadores de un socket específico o un nodo NUMA específico pueden pertenecer al mismo nodo de procesador. Resource Manager asigna identificadores únicos a `0` estos nodos `nodeCount - 1`empezando por , donde `nodeCount` representa el número total de nodos de procesador en el sistema.

El recuento de nodos se puede obtener de la función [GetProcessorNodeCount](concurrency-namespace-functions.md).

## <a name="itopologynodegetnext-method"></a><a name="getnext"></a>Método ITopologyNode::GetNext

Devuelve una interfaz al siguiente nodo de topología en orden de enumeración.

```cpp
virtual ITopologyNode *GetNext() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Una interfaz al siguiente nodo en orden de enumeración. Si no hay más nodos en orden de enumeración de `NULL`la topología del sistema, este método devolverá el valor .

## <a name="itopologynodegetnumanode-method"></a><a name="getnumanode"></a>Método ITopologyNode::GetNumaNode

Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.

```cpp
virtual unsigned long GetNumaNode() const = 0;
```

### <a name="return-value"></a>Valor devuelto

Aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.

### <a name="remarks"></a>Observaciones

Un proxy de subproceso que se ejecuta en una raíz del procesador virtual que pertenece a este nodo tendrá afinidad por lo menos al nivel del nodo NUMA para el nodo NUMA que devuelve este método.

## <a name="see-also"></a>Consulte también

[espacio de nombres de simultaneidad](concurrency-namespace.md)
