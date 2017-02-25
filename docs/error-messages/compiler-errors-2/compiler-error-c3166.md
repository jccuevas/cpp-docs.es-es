---
title: "Error del compilador C3166 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3166"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3166"
ms.assetid: ec3e330d-c15d-4158-8268-09101486c566
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error del compilador C3166
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'puntero' : no se puede declarar un puntero a un puntero \_\_gc interior como miembro de 'tipo'  
  
 El compilador ha encontrado una declaración de puntero no válida \(un puntero [\_\_nogc](../../misc/nogc.md) a un puntero [\_\_gc](../../misc/gc.md)\).  Puede que dicha sintaxis se admita en futuras versiones.  
  
 Sólo se puede reproducir el error C3166 utilizando **\/clr:oldSyntax**.  
  
 El código siguiente genera el error C3166:  
  
```  
// C3166.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__gc struct G {  
   int __gc* __nogc* p;   // C3166  
};  
  
public __gc class H {  
public:  
   Int32 __gc* __nogc* p;   // C3166  
};  
  
public __value struct I {  
   int __gc* __nogc* p;   // C3166  
};  
  
public __value class J {  
public:  
   int __gc* __nogc* p;   // C3166  
};  
  
int main() {  
   G* pG = new G;  
   H* pH = new H;  
}  
```