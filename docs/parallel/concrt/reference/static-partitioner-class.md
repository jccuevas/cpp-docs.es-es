---
title: static_partitioner (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- static_partitioner
- PPL/concurrency::static_partitioner
- PPL/concurrency::static_partitioner::static_partitioner
dev_langs:
- C++
helpviewer_keywords:
- static_partitioner class
ms.assetid: 2b3dbdf0-6eb9-49f6-8639-03df1d974143
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 20dad961b694042c721f388c9a40e0bf99b9b77d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="staticpartitioner-class"></a>static_partitioner (Clase)
La clase `static_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`. La clase Partitioner divide el intervalo en tantos fragmentos como trabajadores hay disponibles para el programador subyacente.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class static_partitioner;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[static_partitioner](#ctor)|Construye un objeto `static_partitioner`.|  
|[~static_partitioner Destructor](#dtor)|Destruye un objeto `static_partitioner`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `static_partitioner`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a> ~static_partitioner 

 Destruye un objeto `static_partitioner`.  
  
```
~static_partitioner();
```  
  
##  <a name="ctor"></a> static_partitioner 

 Construye un objeto `static_partitioner`.  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
