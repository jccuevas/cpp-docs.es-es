---
title: "Error del compilador C2959 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2959"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2959"
ms.assetid: d66bb2a8-70c3-4209-a358-b0c47f111a50
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error del compilador C2959
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

una clase genérica o función no puede ser miembro de una plantilla  
  
 Para obtener más información, vea [Windows en tiempo de ejecución y plantillas administradas](../../windows/windows-runtime-and-managed-templates-cpp-component-extensions.md) y [Genéricos](../../windows/generics-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2959.  
  
```  
// C2959.cpp  
// compile with: /clr /c  
template <class T> ref struct S {  
   generic <class U> ref struct GR1;   // C2959  
};  
```