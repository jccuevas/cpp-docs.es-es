---
title: "Compiler Error C2394 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2394"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2394"
ms.assetid: 653fa9a0-29b3-48aa-bc01-82f98f717a2b
caps.latest.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 12
---
# Compiler Error C2394
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'su\_tipo::operator'op'" : el operador CLR o WinRT no es válido.Al menos un parámetro debe ser de los tipos siguientes: 'T^', 'T^%', 'T^&', donde T \= 'su\_tipo'  
  
 Un operador en un tipo administrado o de Windows en tiempo de ejecución no tenía al menos un parámetro con un tipo igual al del valor devuelto del operador.  
  
 El código siguiente genera el error C2394:  
  
```  
// C2394.cpp  
// compile with: /clr /c  
ref struct Y {  
   static Y^ operator -(int i, char c);   // C2394  
  
   // OK  
   static Y^ operator -(Y^ hY, char c);  
   // or  
   static Y^ operator -(int i, Y^& rhY);  
};  
```