---
title: simple_partitioner (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ppl/concurrency::simple_partitioner
dev_langs:
- C++
helpviewer_keywords:
- simple_partitioner class
ms.assetid: d7e997af-54d1-43f5-abe0-def72df6edb3
caps.latest.revision: 8
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
ms.sourcegitcommit: fc190feb08d9b221cd1cc21a9c91ad567c86c848
ms.openlocfilehash: dc90df5ba9fbbf5566a26a014a6a2db2ae4a0459
ms.lasthandoff: 02/24/2017

---
# <a name="simplepartitioner-class"></a>simple_partitioner (Clase)
La clase `simple_partitioner` representa una partición estática del intervalo sobre el que se itera mediante `parallel_for`. La clase Partitioner divide el intervalo en fragmentos de forma que cada fragmento tiene al menos el número de iteraciones especificadas por el tamaño del fragmento.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class simple_partitioner;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[simple_partitioner (Constructor)](#ctor)|Construye un objeto `simple_partitioner`.|  
|[~ simple_partitioner (destructor)](#dtor)|Destruye un objeto `simple_partitioner`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `simple_partitioner`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namedtora-simplepartitioner"></a><a name="dtor"></a>~ simple_partitioner 

 Destruye un objeto `simple_partitioner`.  
  
```
~simple_partitioner();
```  
  
##  <a name="a-namectora-simplepartitioner"></a><a name="ctor"></a>simple_partitioner 

 Construye un objeto `simple_partitioner`.  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Chunk_size`  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

