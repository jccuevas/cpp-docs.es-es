---
title: simple_partitioner (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- simple_partitioner
- PPL/concurrency::simple_partitioner
- PPL/concurrency::simple_partitioner::simple_partitioner
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 5faef5bd1be6cc02d6614a6f6193c74167a8ff23
ms.openlocfilehash: 08d378c841fd9181fe9a2cf918bde9fe3ebbdc32
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

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
|[simple_partitioner](#ctor)|Construye un objeto `simple_partitioner`.|  
|[~ simple_partitioner (destructor)](#dtor)|Destruye un objeto `simple_partitioner`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `simple_partitioner`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** ppl.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="dtor"></a>~ simple_partitioner 

 Destruye un objeto `simple_partitioner`.  
  
```
~simple_partitioner();
```  
  
##  <a name="ctor"></a>simple_partitioner 

 Construye un objeto `simple_partitioner`.  
  
```
explicit simple_partitioner(_Size_type _Chunk_size);
```  
  
### <a name="parameters"></a>Parámetros  
 `_Chunk_size`  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

