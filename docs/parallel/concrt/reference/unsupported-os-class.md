---
title: "unsupported_os (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "concrt/concurrency::unsupported_os"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "unsupported_os (clase)"
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
caps.latest.revision: 20
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 20
---
# unsupported_os (Clase)
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

Esta clase describe una excepción que se produce cuando se usa un sistema operativo no compatible.  
  
## Sintaxis  
  
```  
class unsupported_os : public std::exception;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[unsupported\_os::unsupported\_os \(Constructor\)](../Topic/unsupported_os::unsupported_os%20Constructor.md)|Sobrecargado.  Construye un objeto `unsupported_os`.|  
  
## Jerarquía de herencia  
 `exception`  
  
 `unsupported_os`  
  
## Requisitos  
 **Encabezado:** concrt.h  
  
 **Espacio de nombres:** simultaneidad  
  
## Vea también  
 [concurrency \(Espacio de nombres\)](../../../parallel/concrt/reference/concurrency-namespace.md)