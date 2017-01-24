---
title: "Error del compilador C3195 | Microsoft Docs"
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
  - "C3195"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3195"
ms.assetid: 97e4f681-812b-49e8-ba57-24b7817e3cd8
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3195
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'operador' : está reservado y no se puede utilizar como miembro de una clase ref o de un tipo de valor.Los operadores CLR o WinRT se deben definir mediante la palabra clave 'operator'  
  
 El compilador detectó una definición de operador con la sintaxis de Extensiones administradas para C\+\+.  
  
 Use la nueva sintaxis de C\+\+ o la opción del compilador **\/clr:oldSyntax** para habilitar la sintaxis de Extensiones administradas para C\+\+.  
  
 El ejemplo siguiente genera el error C3195 y muestra cómo corregirlo:  
  
```  
// C3195.cpp  
// compile with: /clr /LD  
#using <mscorlib.dll>  
value struct V {  
   static V op_Addition(V v, int i);   // C3195  
   static V operator +(V v, char c);   // OK for new C++ syntax   
};  
```