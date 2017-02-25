---
title: "Advertencia del compilador (nivel 2) C4056 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4056"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4056"
ms.assetid: a3c3a9b8-ec30-452d-96cb-3694adcce789
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia del compilador (nivel 2) C4056
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

desbordamiento en la aritmética de constante de punto flotante  
  
 La aritmética de una constante de punto flotante genera un resultado que supera el valor máximo permitido.  
  
 Las optimizaciones del compilador durante la aritmética constante pueden ocasionar esta advertencia.  Se puede omitir con seguridad esta advertencia si desaparece al desactivar la optimización \([\/Od](../../build/reference/od-disable-debug.md)\).  
  
 El código siguiente genera el error C4056:  
  
```  
// C4056.cpp  
// compile with: /W2 /LD  
#pragma warning (default : 4056)  
float fp_val = 1.0e300 * 1.0e300;   // C4056  
```