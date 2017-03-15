---
title: "Error del compilador C2021 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2021"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2021"
ms.assetid: 064f32e2-3794-48d5-9767-991003dcb36a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2021
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se esperaba un valor de exponente, no 'carácter'  
  
 El carácter utilizado como exponente de una constante de punto flotante no es un número válido.  Asegúrese de utilizar un exponente válido.  
  
## Ejemplo  
 El código siguiente genera el error C2021:  
  
```  
// C2021.cpp  
float test1=1.175494351E;   // C2021  
```  
  
## Ejemplo  
 Posible solución:  
  
```  
// C2021b.cpp  
// compile with: /c  
float test2=1.175494351E8;  
```