---
title: ITopologyExecutionResource (estructura) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: d9671dbf84a1104bc3b6f3a6f9d383aac167759c
ms.lasthandoff: 03/17/2017

---
# <a name="itopologyexecutionresource-structure"></a>ITopologyExecutionResource (Estructura)
Una interfaz a un recurso de ejecución definido por el Administrador de recursos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct ITopologyExecutionResource;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Itopologyexecutionresource:: GetId](#getid)|Devuelve el Administrador de recursos del identificador único para este recurso de ejecución.|  
|[Itopologyexecutionresource:: GetNext](#getnext)|Devuelve una interfaz para el siguiente recurso de ejecución en el orden de enumeración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza normalmente para recorrer la topología del sistema observados por el Administrador de recursos.  
  
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
 Devuelve una interfaz para el siguiente recurso de ejecución en el orden de enumeración.  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Interfaz para el siguiente recurso de ejecución en el orden de enumeración. Si no hay ningún nodo más en orden de enumeración del nodo al que pertenece este recurso de ejecución, este método devolverá el valor `NULL`.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

