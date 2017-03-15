---
title: "lock (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "msclr::lock"
  - "msclr.lock"
  - "lock"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "lock (clase)"
ms.assetid: 5123edd9-6aed-497d-9a0b-f4b6d6c0d666
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# lock (Clase)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Esta clase automatiza tomar un bloqueo para sincronizar el acceso a un objeto de varios subprocesos.  Cuando le construido adquiere el bloqueo y cuando lo que se libera el bloqueo.  
  
## Sintaxis  
  
```  
ref class lock;  
```  
  
## Comentarios  
 `lock` sólo está disponible para los objetos de CLR y sólo se puede utilizar en el código de CLR.  
  
 Internamente, la clase lock usa <xref:System.Threading.Monitor> para sincronizar el acceso.  Consulte este tema para obtener información más detallada sobre la sincronización.  
  
## Requisitos  
 **Archivo de encabezado** \<msclr\\lock.h\>  
  
 msclr de**Namespace**  
  
## Vea también  
 [bloquear](../dotnet/lock.md)   
 [lock \(Miembros\)](../dotnet/lock-members.md)