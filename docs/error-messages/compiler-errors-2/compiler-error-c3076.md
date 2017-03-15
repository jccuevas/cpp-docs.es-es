---
title: "Error del compilador C3076 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3076"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3076"
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Error del compilador C3076
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'instancias' : no puede incrustar una instancia de un tipo de referencia, 'tipo', en un tipo nativo  
  
 Un tipo nativo no puede contener una instancia de un tipo CLR.  
  
 Para obtener más información, vea [Semántica de pila de C\+\+ para los tipos de referencia](../../dotnet/cpp-stack-semantics-for-reference-types.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3076.  
  
```  
// C3076.cpp  
// compile with: /clr /c  
ref struct U {};  
  
struct V {  
   U y;   // C3076  
};  
  
ref struct W {  
   U y;   // OK  
};  
```