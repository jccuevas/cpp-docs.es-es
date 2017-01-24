---
title: "Advertencia del compilador (nivel 4) C4289 | Microsoft Docs"
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
  - "C4289"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4289"
ms.assetid: 0dbd2863-4cde-4e16-894b-104a2d5fa724
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4289
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar : 'var' : la variable de control de bucles declarada en el bucle For se utiliza fuera del ámbito del bucle For  
  
 Al compilar con [\/Ze](../../build/reference/za-ze-disable-language-extensions.md) y **\/Zc:forScope\-**, se ha utilizado una variable declarada en un bucle [for](../../cpp/for-statement-cpp.md) después del ámbito del bucle **for**.  
  
 Vea [\/Zc:forScope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) para obtener información sobre la forma de especificar el comportamiento estándar en los bucles **for** mediante **\/Ze**.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
 El código siguiente genera el error C4289:  
  
```  
// C4289.cpp  
// compile with: /W4 /Zc:forScope-  
#pragma warning(default:4289)  
int main() {  
   for (int i = 0 ; ; )   // C4289  
      break;  
   i++;  
}  
```