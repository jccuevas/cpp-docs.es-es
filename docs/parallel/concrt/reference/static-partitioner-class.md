---
title: static_partitioner (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a15310be9a879a2dbcb117a987e56571e953f825
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
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
|[~ static_partitioner (destructor)](#dtor)|Destruye un objeto `static_partitioner`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `static_partitioner`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a> ~ static_partitioner) 

 Destruye un objeto `static_partitioner`.  
  
```
~static_partitioner();
```  
  
##  <a name="ctor"></a> static_partitioner) 

 Construye un objeto `static_partitioner`.  
  
```
static_partitioner();
```  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
