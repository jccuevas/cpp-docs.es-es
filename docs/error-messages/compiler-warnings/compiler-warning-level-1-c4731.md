---
title: "Advertencia del compilador (nivel 1) C4731 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4731"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4731"
ms.assetid: 5658c24c-3e6f-4505-835b-1fb92d47cab0
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4731
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'puntero': registro de puntero de marco 'registro' modificado por código de ensamblado en línea  
  
 Se modificó un registro de puntero de marco.  Se debe guardar y restaurar el registro en el bloque de ensamblado en línea o variable de marco \(local o de parámetro, según el registro modificado\), o de lo contrario el código podría no funcionar correctamente.  
  
 El código siguiente genera el error C4731:  
  
```  
// C4731.cpp  
// compile with: /W1 /LD  
// processor: x86  
// C4731 expected  
void bad(int p) {  
   __asm  
   {  
      mov ebp, 1  
   }  
  
   if (p == 1)  
   {  
      // ...  
   }  
}  
```  
  
 EBP es el puntero de marco \(no se permite FPO\) y se está modificando.  Cuando se hace más tarde referencia a `p`, dicha referencia es relativa a `EBP`.  Pero `EBP` ha quedado sobrescrito por el código, por lo que el programa no funcionará correctamente e incluso podría no funcionar en absoluto.