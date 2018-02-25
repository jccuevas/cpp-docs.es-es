---
title: auto_partitioner (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 6e1cdb2cf5dcb149879be44c59714c5af6008c4b
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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
|[~auto_partitioner Destructor](#dtor)|Destruye un objeto `auto_partitioner`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `auto_partitioner`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a> ~auto_partitioner 

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
