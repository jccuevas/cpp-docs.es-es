---
title: "STACKSIZE | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "STACKSIZE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "STACKSIZE (instrucción de archivo .def)"
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# STACKSIZE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Establece el tamaño de la pila en bytes.  
  
```  
STACKSIZE reserve[,commit]  
```  
  
## Comentarios  
 Un modo equivalente de especificar el tamaño de la pila es con la opción [Asignaciones de la pila](../../build/reference/stack-stack-allocations.md) \(\/STACK\).  Vea la documentación de esa opción para obtener más información sobre los argumentos *reserve* y `commit`.  
  
 Esta opción no tiene efecto sobre las DLL.  
  
## Vea también  
 [Reglas para instrucciones de definición de módulos](../../build/reference/rules-for-module-definition-statements.md)