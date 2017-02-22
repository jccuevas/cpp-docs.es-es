---
title: "Error del compilador C2743 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2743"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2743"
ms.assetid: 644cd444-21d2-471d-a176-f5f52c5a0b73
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C2743
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'tipo': no se puede aplicar catch a un tipo nativo con el destructor \_\_clrcall o copiar el constructor  
  
 Un módulo compilado con **\/clr** \(no **\/clr:pure**\) intentó aplicar catch a una excepción de tipo nativo donde el destructor del tipo o el constructor de la copia utilizan la convención de llamada \_`_clrcall`.  
  
 Cuando se compila con **\/clr** \(no **\/clr:pure**\), el control de excepciones espera que las funciones miembro de un tipo nativo sean [\_\_cdecl](../../cpp/cdecl.md) y no [\_\_clrcall](../../cpp/clrcall.md).  No se puede aplicar catch a los tipos nativos con funciones miembro que utilicen la convención de llamada `__clrcall` en un módulo compilado con **\/clr**.  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C2743.  
  
```  
// C2743.cpp  
// compile with: /clr  
public struct S {  
   __clrcall ~S() {}  
};  
  
public struct T {  
   ~T() {}  
};  
  
int main() {  
   try {}  
   catch(S) {}   // C2743  
   // try the following line instead  
   // catch(T) {}  
  
   try {}  
   catch(S*) {}   // OK  
}  
```