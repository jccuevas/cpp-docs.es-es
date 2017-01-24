---
title: "cancellation_token_registration (Clase) | Microsoft Docs"
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
  - "pplcancellation_token/concurrency::cancellation_token_registration"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "cancellation_token_registration (clase)"
ms.assetid: 823d63f4-7233-4d65-8976-6152ccf12d0e
caps.latest.revision: 9
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# cancellation_token_registration (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

La clase `cancellation_token_registration` representa una notificación de devolución de llamada de un objeto `cancellation_token`.  Cuando el método `register` de un objeto `cancellation_token` se usa para recibir una notificación de cuándo se produce la cancelación, se devuelve un objeto `cancellation_token_registration` como identificador a la devolución de la llamada de modo que el llamador puede solicitar que ya no se realice una devolución de llamada específica a través del uso del método `deregister`.  
  
## Sintaxis  
  
```  
class cancellation_token_registration;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token\_registration::cancellation\_token\_registration \(Constructor\)](../Topic/cancellation_token_registration::cancellation_token_registration%20Constructor.md)||  
|[cancellation\_token\_registration::~cancellation\_token\_registration \(Destructor\)](../Topic/cancellation_token_registration::~cancellation_token_registration%20Destructor.md)||  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[cancellation\_token\_registration::operator\!\= \(Operador\)](../Topic/cancellation_token_registration::operator!=%20Operator.md)||  
|[cancellation\_token\_registration::operator\= \(Operador\)](../Topic/cancellation_token_registration::operator=%20Operator.md)||  
|[cancellation\_token\_registration::operator\=\= \(Operador\)](../Topic/cancellation_token_registration::operator==%20Operator.md)||  
  
## Jerarquía de herencia  
 `cancellation_token_registration`  
  
## Requisitos  
 **Encabezado:** pplcancellation\_token.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)