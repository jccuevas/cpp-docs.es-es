---
title: "invalid_operation (Clase) | Microsoft Docs"
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
  - "concrt/concurrency::invalid_operation"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "invalid_operation (clase)"
ms.assetid: 26ba07dc-fcdf-44cb-b748-a31d35205b52
caps.latest.revision: 19
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# invalid_operation (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se realiza una operación no válida que no está descrita con más precisión por otro tipo de excepción producido por el runtime de simultaneidad.  
  
## Sintaxis  
  
```  
class invalid_operation : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[invalid\_operation::invalid\_operation \(Constructor\)](../Topic/invalid_operation::invalid_operation%20Constructor.md)|Sobrecargado.  Construye un objeto `invalid_operation`.|  
  
## Comentarios  
 Los diversos métodos que producen esta excepción normalmente indicarán bajo qué circunstancias la producen.  
  
## Jerarquía de herencia  
 `exception`  
  
 `invalid_operation`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)