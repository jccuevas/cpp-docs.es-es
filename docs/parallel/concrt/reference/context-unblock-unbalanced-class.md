---
title: "context_unblock_unbalanced (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::context_unblock_unbalanced"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "context_unblock_unbalanced (clase)"
ms.assetid: a76066c8-19dd-44fa-959a-6941ec1b0d2d
caps.latest.revision: 20
caps.handback.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# context_unblock_unbalanced (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se llama a los métodos `Block` y `Unblock` de un objeto `Context` que no están emparejados correctamente.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
class context_unblock_unbalanced : public std::exception;  
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[Constructor context_unblock_unbalanced:: context_unblock_unbalanced](#context_unblock_unbalanced__context_unblock_unbalanced_constructor)|Sobrecargado. Construye un objeto `context_unblock_unbalanced`.|  
  
## <a name="remarks"></a>Comentarios  
 Las llamadas a la `Block` y `Unblock` métodos de un `Context` objeto siempre se debe emparejar correctamente. El Runtime de simultaneidad permite las operaciones que se realicen en cualquier orden. Por ejemplo, una llamada a `Block` puede ir seguida de una llamada a `Unblock`, o viceversa. Esta excepción se produce si, por ejemplo, dos llamadas a la `Unblock` método realizados en una fila en un `Context` objeto que no estaba bloqueado.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 `exception`  
  
 `context_unblock_unbalanced`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
##  <a name="a-namecontextunblockunbalancedcontextunblockunbalancedconstructora-contextunblockunbalancedcontextunblockunbalanced-constructor"></a><a name="context_unblock_unbalanced__context_unblock_unbalanced_constructor"></a>  Constructor context_unblock_unbalanced:: context_unblock_unbalanced  
 Construye un objeto `context_unblock_unbalanced`.  
  
```  
explicit _CRTIMP context_unblock_unbalanced(_In_z_ const char* _Message) throw();

 
context_unblock_unbalanced() throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `_Message`  
 Mensaje descriptivo del error.  
  
## <a name="see-also"></a>Vea también  
 [espacio de nombres de simultaneidad](../../../parallel/concrt/reference/concurrency-namespace.md)
