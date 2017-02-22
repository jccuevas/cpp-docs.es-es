---
title: "/TLS | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/TLS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/TLS (opción de dumpbin)"
  - "-TLS (opción de dumpbin)"
ms.assetid: 2b3f48f9-cac4-4351-b15c-2833b43bc709
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# /TLS
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Muestra la estructura IMAGE\_TLS\_DIRECTORY de un ejecutable.  
  
## Comentarios  
 La opción \/TLS muestra los campos de la estructura TLS, así como las direcciones de las funciones de devolución de llamada de TLS.  
  
 Si un programa no utiliza almacenamiento local de subprocesos, su imagen no contendrá ninguna estructura TLS.  Para obtener más información, vea [subproceso](../../cpp/thread.md).  
  
 IMAGE\_TLS\_DIRECTORY se define en winnt.h.  
  
## Vea también  
 [Opciones de DUMPBIN](../../build/reference/dumpbin-options.md)