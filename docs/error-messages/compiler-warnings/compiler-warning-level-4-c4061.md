---
title: "Advertencia del compilador (nivel 4) C4061 | Microsoft Docs"
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
  - "C4061"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4061"
ms.assetid: a99cf88e-7941-4519-8b1b-f6889d914b2f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4061
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el enumerador 'identificador' en la instrucción switch de la enumeración 'enumeración' no está controlada de forma explícita por una etiqueta de caso  
  
 La enumeración no tiene un controlador asociado en una instrucción `switch`.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El código siguiente genera el error C4061:  
  
```  
// C4061.cpp  
// compile with: /W4  
#pragma warning(default : 4061)  
  
enum E { a, b, c };  
void func ( E e )  
{  
   switch(e)  
   {  
      case a:  
      case b:  
      default:  
         break;  
   }   // C4061 c' not handled  
}  
  
int main()  
{  
}  
```