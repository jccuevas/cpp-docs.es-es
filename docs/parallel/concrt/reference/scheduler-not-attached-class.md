---
title: scheduler_not_attached (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::scheduler_not_attached
dev_langs:
- C++
helpviewer_keywords:
- scheduler_not_attached class
ms.assetid: 26001970-b400-463b-be3d-8623359c399a
caps.latest.revision: 19
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
ms.openlocfilehash: 4ee1cbe219b7a1fc5a646afd5e975e84be949f65
ms.lasthandoff: 02/24/2017

---
# <a name="schedulernotattached-class"></a>scheduler_not_attached (Clase)
Esta clase describe una excepción que se produce cuando se realiza una operación que requiere que un programador se adjunte al contexto actual y no hay ninguno.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class scheduler_not_attached : public std::exception;
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[scheduler_not_attached (Constructor)](#ctor)|Sobrecargado. Construye un objeto `scheduler_not_attached`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `scheduler_not_attached`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namectora-schedulernotattached"></a><a name="ctor"></a>scheduler_not_attached) 

 Construye un objeto `scheduler_not_attached`.  
  
```
explicit _CRTIMP scheduler_not_attached(_In_z_ const char* _Message) throw();

scheduler_not_attached() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)   
 [Scheduler (clase)](scheduler-class.md)

