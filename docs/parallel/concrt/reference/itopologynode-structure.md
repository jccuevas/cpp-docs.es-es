---
title: ITopologyNode (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrtrm/concurrency::ITopologyNode
dev_langs:
- C++
helpviewer_keywords:
- ITopologyNode structure
ms.assetid: 92e7e032-04f6-4c7c-be36-8f9a35fc4734
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: fa774c7f025b581d65c28d65d83e22ff2d798230
ms.openlocfilehash: 8274da148f9f74cad73d63363bbbaff307943539
ms.lasthandoff: 02/24/2017

---
# <a name="itopologynode-structure"></a>ITopologyNode (Estructura)
Una interfaz a un nodo de topología definido por el Administrador de recursos. Un nodo contiene uno o varios recursos de ejecución.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct ITopologyNode;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Itopologynode:: Getexecutionresourcecount (método)](#getexecutionresourcecount)|Devuelve el número de recursos de ejecución que se agrupan bajo este nodo.|  
|[Itopologynode:: Getfirstexecutionresource (método)](#getfirstexecutionresource)|Devuelve el primer recurso de ejecución se agrupa bajo este nodo en el orden de enumeración.|  
|[Itopologynode:: GetId (método)](#getid)|Devuelve el Administrador de recursos del identificador único para este nodo.|  
|[Itopologynode:: GetNext (método)](#getnext)|Devuelve una interfaz hasta el siguiente nodo de topología en el orden de enumeración.|  
|[Itopologynode:: Getnumanode (método)](#getnumanode)|Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza normalmente para recorrer la topología del sistema observados por el Administrador de recursos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ITopologyNode`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namegetexecutionresourcecounta--itopologynodegetexecutionresourcecount-method"></a><a name="getexecutionresourcecount"></a>Itopologynode:: Getexecutionresourcecount (método)  
 Devuelve el número de recursos de ejecución que se agrupan bajo este nodo.  
  
```
virtual unsigned int GetExecutionResourceCount() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El número de recursos de ejecución se agrupan bajo este nodo.  
  
##  <a name="a-namegetfirstexecutionresourcea--itopologynodegetfirstexecutionresource-method"></a><a name="getfirstexecutionresource"></a>Itopologynode:: Getfirstexecutionresource (método)  
 Devuelve el primer recurso de ejecución se agrupa bajo este nodo en el orden de enumeración.  
  
```
virtual ITopologyExecutionResource *GetFirstExecutionResource() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El primer recurso de ejecución se agrupa bajo este nodo en el orden de enumeración.  
  
##  <a name="a-namegetida--itopologynodegetid-method"></a><a name="getid"></a>Itopologynode:: GetId (método)  
 Devuelve el Administrador de recursos del identificador único para este nodo.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El Administrador de recursos del identificador único para este nodo.  
  
### <a name="remarks"></a>Comentarios  
 El Runtime de simultaneidad representa subprocesos de hardware en el sistema en grupos de nodos de procesador. Nodos normalmente se derivan de la topología de hardware del sistema. Por ejemplo, todos los procesadores en un socket concreto o un nodo NUMA concreto pueden pertenecer al mismo nodo de procesador. El Administrador de recursos asigna identificadores únicos a estos nodos a partir de `0` hasta e incluyendo `nodeCount - 1`, donde `nodeCount` representa el número total de nodos de procesador en el sistema.  
  
 Se puede obtener el recuento de nodos de la función [GetProcessorNodeCount](concurrency-namespace-functions.md).  
  
##  <a name="a-namegetnexta--itopologynodegetnext-method"></a><a name="getnext"></a>Itopologynode:: GetNext (método)  
 Devuelve una interfaz hasta el siguiente nodo de topología en el orden de enumeración.  
  
```
virtual ITopologyNode *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una interfaz en el siguiente nodo en orden de enumeración. Si no hay ningún nodo más en orden de enumeración de la topología del sistema, este método devolverá el valor `NULL`.  
  
##  <a name="a-namegetnumanodea--itopologynodegetnumanode-method"></a><a name="getnumanode"></a>Itopologynode:: Getnumanode (método)  
 Devuelve la aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.  
  
```
virtual unsigned long GetNumaNode() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Aplicación Windows asignada al número de nodo NUMA al que pertenece este nodo de Administrador de recursos.  
  
### <a name="remarks"></a>Comentarios  
 Un proxy de subproceso que se ejecuta en una raíz del procesador virtual que pertenece a este nodo tendrá afinidad por lo menos al nivel del nodo NUMA para el nodo NUMA que devuelve este método.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

