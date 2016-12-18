---
title: "Advertencia del compilador (nivel 1) C4382 | Microsoft Docs"
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
  - "C4382"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4382"
ms.assetid: 34be9ad3-bae6-411a-8f80-0c8fd0d2c092
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4382
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

produciendo 'tipo' : un tipo con el destructor \_\_clrcall o el constructor de copia solamente se puede detectar en el módulo \/clr:pure  
  
 Cuando se compila con **\/clr** \(no **\/clr:pure**\), el control de excepciones espera que las funciones miembro de un tipo nativo sean [\_\_cdecl](../../cpp/cdecl.md) y no [\_\_clrcall](../../cpp/clrcall.md).  No se puede aplicar catch a los tipos nativos con funciones miembro que utilicen la convención de llamada `__clrcall` en un módulo compilado con **\/clr**.  
  
 Si la excepción se detectara en un módulo compilado con **\/clr:pure**, podría omitir esta advertencia.  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4382.  
  
```  
// C4382.cpp  
// compile with: /clr /W1 /c  
struct S {  
   __clrcall ~S() {}  
};  
  
struct T {  
   ~T() {}  
};  
  
int main() {  
   S s;  
   throw s;   // C4382  
  
   S * ps = &s;  
   throw ps;   // OK  
  
   T t;  
   throw t;   // OK  
}  
```