---
title: "invalid_link_target (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::invalid_link_target"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_link_target (clase)"
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
caps.latest.revision: 19
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# invalid_link_target (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se llama al método `link_target` de un bloque de mensajería y el bloque de mensajería no se puede vincular al destino.  Este puede ser el resultado de superar el número de vínculos que se permiten en el bloque de mensajería o de intentar vincular un destino específico al mismo origen dos veces.  
  
## Sintaxis  
  
```  
class invalid_link_target : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_link\_target::invalid\_link\_target \(Constructor\)](../Topic/invalid_link_target::invalid_link_target%20Constructor.md)|Sobrecargado.  Construye un objeto `invalid_link_target`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `invalid_link_target`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [Bloques de mensajes asincrónicos](../../../parallel/concrt/asynchronous-message-blocks.md)