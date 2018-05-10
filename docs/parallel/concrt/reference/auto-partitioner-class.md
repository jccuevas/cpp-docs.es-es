---
title: auto_partitioner (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: reference
f1_keywords:
- auto_partitioner
- PPL/concurrency::auto_partitioner
- PPL/concurrency::auto_partitioner::auto_partitioner
dev_langs:
- C++
helpviewer_keywords:
- auto_partitioner class
ms.assetid: 7cc08e5d-20b4-47a4-b4b5-c214a78f5a9e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 05232aa954a9ded7d2ab3a26ae4e1524610c3d04
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
---
# <a name="autopartitioner-class"></a>auto_partitioner (Clase)
La clase `auto_partitioner` representa a los métodos predeterminados `parallel_for`, `parallel_for_each` y usa `parallel_transform` para dividir el intervalo sobre el que iteran. Este método de particiones emplea la apropiación del intervalo para el equilibrio de carga, así como la cancelación por iterar.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class auto_partitioner;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[auto_partitioner](#ctor)|Construye un objeto `auto_partitioner`.|  
|[~ auto_partitioner (destructor)](#dtor)|Destruye un objeto `auto_partitioner`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `auto_partitioner`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a> ~ auto_partitioner) 

 Destruye un objeto `auto_partitioner`.  
  
```
~auto_partitioner();
```  
  
##  <a name="ctor"></a> auto_partitioner) 

 Construye un objeto `auto_partitioner`.  
  
```
auto_partitioner();
```  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
