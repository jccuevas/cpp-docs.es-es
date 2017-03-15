---
title: Clase invalid_oversubscribe_operation | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- concrt/concurrency::invalid_oversubscribe_operation
dev_langs:
- C++
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
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
ms.openlocfilehash: becb02cfd6a052a019ee73e182804c63a286403e
ms.lasthandoff: 02/24/2017

---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation (Clase)
Esta clase describe una excepción cuando se llama al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `false` sin realizar antes una llamada al método `Context::Oversubscribe` con el parámetro `_BeginOversubscription` establecido en `true`.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class invalid_oversubscribe_operation : public std::exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[invalid_oversubscribe_operation (Constructor)](#ctor)|Sobrecargado. Construye un objeto `invalid_oversubscribe_operation`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `invalid_oversubscribe_operation`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namectora-invalidoversubscribeoperation"></a><a name="ctor"></a>invalid_oversubscribe_operation 

 Construye un objeto `invalid_oversubscribe_operation`.  
  
```  
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

 
invalid_oversubscribe_operation() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [simultaneidad Namespace](concurrency-namespace.md)

