---
title: "Error del compilador C3633 | Microsoft Docs"
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
  - "C3633"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3633"
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3633
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede definir 'miembro' como un miembro de 'tipo' administrado  
  
 Los miembros de datos de clase de referencia de CLR no pueden ser de un tipo de C\+\+ que no sea POD.  Puede crear instancias sólo de un tipo nativo POD en un tipo CLR.  Por ejemplo, un tipo POD no puede contener un constructor de copias ni un operador de asignación.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3633.  
  
```  
// C3633.cpp  
// compile with: /clr /c  
#pragma warning( disable : 4368 )  
  
class A1 {  
public:  
   A1() { II = 0; }  
   int II;  
};  
  
ref class B {  
public:  
   A1 a1;   // C3633  
   A1 * a2;   // OK  
   B() : a2( new A1 ) {}  
    ~B() { delete a2; }  
};  
```  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3633.  
  
```  
// C3633_b.cpp  
// compile with: /clr:oldSyntax /c  
class A1 {  
public:  
   A1() { II = 0; }  
   int II;  
};  
  
__gc class B {  
public:  
   A1 a1;   // C3633  
   A1 * a2;   // OK  
   B() : a2( new A1 ) {}  
    ~B() { delete a2; }  
};  
```