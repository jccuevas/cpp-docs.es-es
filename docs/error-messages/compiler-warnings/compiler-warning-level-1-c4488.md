---
title: "Advertencia del compilador (nivel 1) C4488 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4488"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4488"
ms.assetid: 55625e46-ddb5-4c7c-99c7-cd4aa9f879bd
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Advertencia del compilador (nivel 1) C4488
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : requiere que la palabra clave 'palabra clave' implemente el método de interfaz 'método\_de\_interfaz'  
  
 Una clase debe implementar todos los miembros de la interfaz de la que se herede directamente.  Un miembro implementado debe tener accesibilidad pública y debe marcarse como virtual.  
  
## Ejemplo  
 Puede producirse la advertencia C4488 si un miembro implementado no es público.  El ejemplo siguiente genera el error C4488.  
  
```  
// C4488.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
// implemented member not public  
ref class B : MyI { virtual void f1() {} };  // C4488  
  
// OK  
ref class C : MyI {  
public:  
   virtual void f1() {}  
};  
```  
  
## Ejemplo  
 Puede producirse la advertencia C4488 si un miembro implementado no está marcado como virtual.  El ejemplo siguiente genera el error C4488.  
  
```  
// C4488_b.cpp  
// compile with: /clr /c /W1 /WX  
interface struct MyI {  
   void f1();  
};  
  
ref struct B : MyI { void f1() {} };   // C4488  
ref struct C : MyI { virtual void f1() {} };   // OK  
```