---
title: context_self_unblock (clase) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
dev_langs:
- C++
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
caps.latest.revision: 21
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
ms.openlocfilehash: a5fa917c2873cf23bdb3b527f1d3e86055b6f8eb
ms.contentlocale: es-es
ms.lasthandoff: 03/17/2017

---
# <a name="contextselfunblock-class"></a>context_self_unblock (Clase)
Esta clase describe una excepción que se produce cuando se llama al método `Unblock` de un objeto `Context` desde el mismo contexto. Esto indicaría que un contexto especificado ha intentado desbloquearse a sí mismo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class context_self_unblock : public std::exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[context_self_unblock](#ctor)|Sobrecargado. Construye un objeto `context_self_unblock`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `context_self_unblock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="ctor"></a>context_self_unblock 

 Construye un objeto `context_self_unblock`.  
  
```  
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

 
context_self_unblock() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [concurrency (espacio de nombres)](concurrency-namespace.md)

