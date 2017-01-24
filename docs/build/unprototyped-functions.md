---
title: "Funciones sin prototipo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 34200b8c-5b52-4f0d-aff8-9f70d82868ed
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Funciones sin prototipo
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En el caso de las funciones sin prototipos bien definidos, el llamador pasará los valores de tipo entero como enteros y los valores de punto flotante como valores de doble precisión.  Sólo en el caso de los valores de punto flotante, tanto el registro entero como el registro de punto flotante incluirán el valor de tipo float si el destinatario espera el valor de los registros enteros.  
  
```  
func1();  
func2() {   // RCX = 2, RDX = XMM1 = 1.0, and R8 = 7  
   func1(2, 1.0, 7);  
}  
```  
  
## Vea también  
 [Convención de llamada](../build/calling-convention.md)