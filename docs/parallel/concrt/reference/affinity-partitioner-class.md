---
title: affinity_partitioner (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- affinity_partitioner
- PPL/concurrency::affinity_partitioner
- PPL/concurrency::affinity_partitioner::affinity_partitioner
dev_langs:
- C++
helpviewer_keywords:
- affinity_partitioner class
ms.assetid: 31bf7bb1-bd01-491c-9760-d9d60edfccad
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8ecc7e20947eee2491bf806f225178724b268ace
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="affinitypartitioner-class"></a>affinity_partitioner (Clase)
La clase `affinity_partitioner` es similar a la clase `static_partitioner`, pero mejora la afinidad de caché eligiendo la asignación de subintervalos para subprocesos de trabajo. Esta clase puede mejorar considerablemente el rendimiento cuando un bucle se vuelve a ejecutar sobre el mismo conjunto de datos, y los datos se ajustan al caché. Observe que el mismo objeto `affinity_partitioner` debe utilizarse con iteraciones posteriores de un bucle paralelo que se ejecuta sobre un conjunto de datos determinado, para beneficiarse de la situación de los datos.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class affinity_partitioner;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[affinity_partitioner](#ctor)|Construye un objeto `affinity_partitioner`.|  
|[~affinity_partitioner Destructor](#dtor)|Destruye un `affinity_partitioner` objeto.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `affinity_partitioner`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a> ~affinity_partitioner 

 Destruye un `affinity_partitioner` objeto.  
  
```
~affinity_partitioner();
```  
  
##  <a name="ctor"></a> affinity_partitioner) 

 Construye un objeto `affinity_partitioner`.  
  
```
affinity_partitioner();
```  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)
