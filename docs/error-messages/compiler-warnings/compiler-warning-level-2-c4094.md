---
title: "Advertencia del compilador (nivel 2) C4094 | Microsoft Docs"
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
  - "C4094"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4094"
ms.assetid: e68929fb-3a1c-4be7-920b-d5f79f534f99
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 2) C4094
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'símbolo \(token\)' sin etiqueta no ha declarado ningún símbolo  
  
 El compilador detectó una declaración vacía que utilizaba una estructura, unión o clase sin etiquetas.  Se omite la declaración.  
  
## Ejemplo  
  
```  
// C4094.cpp  
// compile with: /W2  
struct  
{  
};   // C4094  
  
int main()  
{  
}  
```  
  
 Estas definiciones generan un error en condiciones de compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).