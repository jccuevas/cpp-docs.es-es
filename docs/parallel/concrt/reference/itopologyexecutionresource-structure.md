---
title: ITopologyExecutionResource (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetId
- CONCRTRM/concurrency::ITopologyExecutionResource::ITopologyExecutionResource::GetNext
dev_langs: C++
helpviewer_keywords: ITopologyExecutionResource structure
ms.assetid: e36756f7-4cd9-4fa6-ba60-23fea58ef2bf
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: caf2cc77cd31df611f71d07c5a0a49f600767f81
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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
|[Itopologyexecutionresource:: GetId](#getid)|Devuelve el Administrador de recursos del identificador único para este recurso de ejecución.|  
|[Itopologyexecutionresource:: GetNext](#getnext)|Devuelve una interfaz para el recurso de ejecución siguiente en el orden de enumeración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza normalmente para recorrer la topología del sistema tal y como se observa el Administrador de recursos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getid"></a>Itopologyexecutionresource:: GetId (método)  
 Devuelve el Administrador de recursos del identificador único para este recurso de ejecución.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El Administrador de recursos del identificador único para este recurso de ejecución.  
  
##  <a name="getnext"></a>Itopologyexecutionresource:: GetNext (método)  
 Devuelve una interfaz para el recurso de ejecución siguiente en el orden de enumeración.  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una interfaz para el recurso de ejecución siguiente en el orden de enumeración. Si no hay ningún nodo más en orden de enumeración del nodo al que pertenece este recurso de ejecución, este método devolverá el valor `NULL`.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
