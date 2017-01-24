---
title: "Error del compilador C3656 | Microsoft Docs"
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
  - "C3656"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3656"
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3656
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'reemplazo' : no se puede repetir el especificador de reemplazo  
  
 Una palabra clave de reemplazo explícito solo se puede especificar una vez.  Para obtener más información, vea [Reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3656:  
  
```  
// C3656.cpp  
// compile with: /clr /c  
public interface struct O {  
   int f();  
};  
  
public ref struct V : O {  
   int f() override override { return 0; }   // C3656  
   // try the following line instead  
   // int f() override { return 0; }  
};  
```