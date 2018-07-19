---
title: ITopologyNode (estructura) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- ITopologyNode
- CONCRTRM/concurrency::ITopologyNode
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetExecutionResourceCount
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetFirstExecutionResource
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetId
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNext
- CONCRTRM/concurrency::ITopologyNode::ITopologyNode::GetNumaNode
dev_langs:
- C++
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4168fbfbd2bf17ad8b8b752d2843c8f57b0f3f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692696"
---
# <a name="itopologynode-structure"></a>ITopologyNode (Estructura)
Una interfaz a un nodo de topología definido por el Administrador de recursos. Un nodo contiene uno o varios recursos de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct ITopologyNode;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[ITopologyNode::GetExecutionResourceCount](#getexecutionresourcecount)|Devuelve el número de recursos de ejecución que se agrupan bajo este nodo.|  
|[ITopologyNode::GetFirstExecutionResource](#getfirstexecutionresource)|Devuelve el primer recurso de ejecución se agrupa bajo este nodo en el orden de enumeración.|  
|[Itopologynode:: GetId](#getid)|Devuelve el Administrador de recursos del identificador único para este nodo.|  
|[Itopologynode:: GetNext](#getnext)|Devuelve una interfaz en el siguiente nodo de topología en orden de enumeración.|  
|[Itopologynode:: Getnumanode](#getnumanode)|Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza normalmente para recorrer la topología del sistema tal y como se observa el Administrador de recursos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ITopologyNode`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getexecutionresourcecount"></a>  Itopologynode:: Getexecutionresourcecount (método)  
 Devuelve el número de recursos de ejecución que se agrupan bajo este nodo.  
  
```
virtual unsigned int GetExecutionResourceCount() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de recursos de ejecución que se agrupan bajo este nodo.  
  
##  <a name="getfirstexecutionresource"></a>  Itopologynode:: Getfirstexecutionresource (método)  
 Devuelve el primer recurso de ejecución se agrupa bajo este nodo en el orden de enumeración.  
  
```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer recurso de ejecución se agrupa bajo este nodo en el orden de enumeración.  
  
##  <a name="getid"></a>  Itopologynode:: GetId (método)  
 Devuelve el Administrador de recursos del identificador único para este nodo.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El Administrador de recursos del identificador único para este nodo.  
  
### <a name="remarks"></a>Comentarios  
 El Runtime de simultaneidad representa subprocesos de hardware en el sistema en grupos de nodos de procesador. Nodos normalmente se derivan de la topología del hardware del sistema. Por ejemplo, todos los procesadores en un socket concreto o un nodo NUMA concreto pueden pertenecer al mismo nodo de procesador. El Administrador de recursos asigna identificadores únicos a estos nodos a partir de `0` hasta e incluyendo `nodeCount - 1`, donde `nodeCount` representa el número total de nodos de procesador en el sistema.  
  
 Se puede obtener el recuento de nodos de la función [GetProcessorNodeCount](concurrency-namespace-functions.md).  
  
##  <a name="getnext"></a>  Itopologynode:: GetNext (método)  
 Devuelve una interfaz en el siguiente nodo de topología en orden de enumeración.  
  
```
virtual ITopologyNode *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una interfaz en el siguiente nodo en orden de enumeración. Si no hay ningún nodo más en orden de enumeración de la topología del sistema, este método devolverá el valor `NULL`.  
  
##  <a name="getnumanode"></a>  Itopologynode:: Getnumanode (método)  
 Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.  
  
```
virtual unsigned long GetNumaNode() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.  
  
### <a name="remarks"></a>Comentarios  
 Un proxy de subproceso que se ejecuta en una raíz del procesador virtual que pertenece a este nodo tendrá afinidad por lo menos al nivel del nodo NUMA para el nodo NUMA que devuelve este método.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
