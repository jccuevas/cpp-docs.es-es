---
title: "Error del compilador C2084 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2084"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2084"
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C2084
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la función 'función' ya tiene un cuerpo  
  
 La función en cuestión ya se encuentra definida.  
  
 En versiones anteriores de Visual C\+\+:  
  
-   El compilador aceptaba varias especializaciones de plantilla que se resolvían con el mismo tipo real, aunque las definiciones adicionales nunca estuvieran disponibles.  Ahora, el compilador detecta estas definiciones múltiples.  
  
-   \_\_int32 e int se trataban como tipos separados.  Ahora, el compilador trata \_\_int32 como sinónimo de int.  Esto significa que el compilador detectará varias definiciones si se sobrecarga una función en \_\_int32 e int y generará un error.  
  
 El código siguiente genera el error C2084:  
  
```  
// C2084.cpp  
void Func(int);  
void Func(int) {}   // define function  
void Func(int) {}   // C2084 second definition  
```  
  
 Posible solución:  
  
```  
// C2084b.cpp  
// compile with: /c  
void Func(int);  
void Func(int) {}  
```