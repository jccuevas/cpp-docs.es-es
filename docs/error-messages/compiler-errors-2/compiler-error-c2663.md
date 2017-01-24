---
title: "Error del compilador C2663 | Microsoft Docs"
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
  - "C2663"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2663"
ms.assetid: 1e93e368-fd52-42bf-9908-9b6df467c8c9
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2663
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : número sobrecargas no tienen ninguna conversión válida para el puntero 'this'  
  
 El compilador no pudo convertir `this` a ninguna de las versiones sobrecargadas de la función miembro.  
  
 Este error puede producirse invocando una función miembro no\-`const` en un objeto `const`.  Posible solución:  
  
1.  Quite `const` de la declaración del objeto.  
  
2.  Agregue `const` a una de las sobrecargas de función miembro.  
  
 El código siguiente genera el error C2663:  
  
```  
// C2663.cpp  
struct C {  
   void f() volatile {}  
   void f() {}  
};  
  
struct D {  
   void f() volatile;  
   void f() const {}  
};  
  
const C *pcc;  
const D *pcd;  
  
int main() {  
   pcc->f();    // C2663  
   pcd->f();    // OK  
}  
```