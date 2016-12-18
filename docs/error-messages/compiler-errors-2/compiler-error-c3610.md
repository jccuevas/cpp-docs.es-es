---
title: "Error del compilador C3610 | Microsoft Docs"
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
  - "C3610"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3610"
ms.assetid: 9349a348-9d37-4a00-9eab-481039268d31
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3610
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipodevalor' : se debe aplicar la conversión 'boxing' al tipo de valor antes de poder llamar al método 'método'  
  
 De forma predeterminada, un tipo de valor no se encuentra en el montón administrado.  Para poder llamar a los métodos de las clases del motor en tiempo de ejecución de .NET, como `Object`, es necesario mover el tipo de valor al montón administrado.  
  
 Sólo se puede reproducir el error C3610 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3610:  
  
```  
// C3610.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
  
__value class A {};  
  
int main() {  
   A a;  
   a.GetType(); // C3610  
  
   // OK  
   __box A* ovar = __box(a);  
   ovar->GetType();  
}  
```