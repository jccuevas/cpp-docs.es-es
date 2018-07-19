---
title: ITopologyExecutionResource (estructura) | Documentos de Microsoft
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
ms.openlocfilehash: adb456315b2c6d15b7a3696df9a6845a2bd2b899
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33686482"
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
|[ITopologyExecutionResource::GetNext](#getnext)|Devuelve una interfaz para el recurso de ejecución siguiente en el orden de enumeración.|  
  
## <a name="remarks"></a>Comentarios  
 Esta interfaz se utiliza normalmente para recorrer la topología del sistema tal y como se observa el Administrador de recursos.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `ITopologyExecutionResource`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrtrm.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="getid"></a>  Itopologyexecutionresource:: GetId (método)  
 Devuelve el Administrador de recursos del identificador único para este recurso de ejecución.  
  
```
virtual unsigned int GetId() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 El Administrador de recursos del identificador único para este recurso de ejecución.  
  
##  <a name="getnext"></a>  Itopologyexecutionresource:: GetNext (método)  
 Devuelve una interfaz para el recurso de ejecución siguiente en el orden de enumeración.  
  
```
virtual ITopologyExecutionResource *GetNext() const = 0;
```  
  
### <a name="return-value"></a>Valor devuelto  
 Una interfaz para el recurso de ejecución siguiente en el orden de enumeración. Si no hay ningún nodo más en orden de enumeración del nodo al que pertenece este recurso de ejecución, este método devolverá el valor `NULL`.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
