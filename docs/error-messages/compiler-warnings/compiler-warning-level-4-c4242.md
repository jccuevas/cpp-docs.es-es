---
title: "Advertencia del compilador (nivel 4) C4242 | Microsoft Docs"
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
  - "C4242"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4242"
ms.assetid: 8df742e1-fbf1-42f3-8e93-c0e1c222dc7e
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4242
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : conversión de 'tipo1' a 'tipo2', posible pérdida de datos  
  
 Los tipos son diferentes.  La conversión puede provocar la pérdida de datos.  El compilador realiza la conversión de tipos.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 Para obtener información adicional sobre C4242, vea [Errores comunes del compilador](http://msdn.microsoft.com/library/windows/desktop/aa384160).  
  
 El código siguiente genera el error C4242:  
  
```  
// C4242.cpp  
// compile with: /W4  
#pragma warning(4:4242)  
int func() {  
   return 0;  
}  
  
int main() {  
   char a;  
   a = func();   // C4242, return type and variable type do not match  
}  
```