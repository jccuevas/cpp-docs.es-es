---
title: "context_self_unblock (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::context_self_unblock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "context_self_unblock (clase)"
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
caps.latest.revision: 21
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# context_self_unblock (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se llama al método `Unblock` de un objeto `Context` desde el mismo contexto. Esto indicaría que un contexto especificado ha intentado desbloquearse a sí mismo.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class context_self_unblock : public std::exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor de context_self_unblock::context_self_unblock](#context_self_unblock__context_self_unblock_constructor)|Sobrecargado. Construye un objeto `context_self_unblock`.|  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `context_self_unblock`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namecontextselfunblockcontextselfunblockconstructora-contextselfunblockcontextselfunblock-constructor"></a><a name="context_self_unblock__context_self_unblock_constructor"></a>  Constructor de context_self_unblock::context_self_unblock  
 Construye un objeto `context_self_unblock`.  
  
```  
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

 
context_self_unblock() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [espacio de nombres de simultaneidad](../../../parallel/concrt/reference/concurrency-namespace.md)
