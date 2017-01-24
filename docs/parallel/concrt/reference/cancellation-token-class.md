---
title: "cancellation_token (Clase) | Microsoft Docs"
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
  - "pplcancellation_token/concurrency::cancellation_token"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token (clase)"
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
caps.latest.revision: 10
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cancellation_token (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `cancellation_token` representa la capacidad para determinar si se ha solicitado la cancelación de alguna operación.  Se puede asociar un determinado símbolo con un objeto `task_group`, `structured_task_group` o `task` para proporcionar una cancelación implícita.  Este token también puede sondearse para la cancelación o puede hacer que se registre una devolución únicamente si se cancela el objeto `cancellation_token_source` asociado.  
  
## Sintaxis  
  
```  
class cancellation_token;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token::cancellation\_token \(Constructor\)](../Topic/cancellation_token::cancellation_token%20Constructor.md)||  
|[cancellation\_token::~cancellation\_token \(Destructor\)](../Topic/cancellation_token::~cancellation_token%20Destructor.md)||  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token::deregister\_callback \(Método\)](../Topic/cancellation_token::deregister_callback%20Method.md)|Quita una devolución de llamada registrada anteriormente mediante el método `register` basándose en el objeto `cancellation_token_registration` devuelto en el momento del registro.|  
|[cancellation\_token::is\_cancelable \(Método\)](../Topic/cancellation_token::is_cancelable%20Method.md)|Devuelve una indicación de si este token se puede cancelar o no.|  
|[cancellation\_token::is\_canceled \(Método\)](../Topic/cancellation_token::is_canceled%20Method.md)|Devuelve `true` si el token se ha cancelado.|  
|[cancellation\_token::none \(Método\)](../Topic/cancellation_token::none%20Method.md)|Devuelve un token de cancelación que nunca puede estar sujeto a la cancelación.|  
|[cancellation\_token::register\_callback \(Método\)](../Topic/cancellation_token::register_callback%20Method.md)|Registra una función de devolución de llamada con el token.  La devolución de llamada se realizará únicamente si se cancela el token.  Observe que si el token ya se canceló en el punto en el que se llama a este método, la devolución de llamada se realizará inmediatamente y de forma sincrónica.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token::operator\!\= \(Operador\)](../Topic/cancellation_token::operator!=%20Operator.md)||  
|[cancellation\_token::operator\= \(Operador\)](../Topic/cancellation_token::operator=%20Operator.md)||  
|[cancellation\_token::operator\=\= \(Operador\)](../Topic/cancellation_token::operator==%20Operator.md)||  
  
## Jerarquía de herencia  
 `cancellation_token`  
  
## Requisitos  
 **Encabezado:** pplcancellation\_token.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)