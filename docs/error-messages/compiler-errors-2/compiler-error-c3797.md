---
title: "Error del compilador C3797 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3797"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3797"
ms.assetid: ab27ff34-8c1d-4297-b004-9e39bd3a4f25
caps.latest.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 4
---
# Error del compilador C3797
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'reemplazo': la declaración de evento no puede tener un especificador de reemplazo \(en su lugar se debe colocar en métodos add, remove o raise\)  
  
 No puede reemplazar un evento trivial \(un evento sin métodos de descriptor de acceso definidos explícitamente\) con otro evento trivial.  El evento que reemplaza debe definir su comportamiento con funciones de descriptor de acceso.  
  
 Para obtener más información, vea [event](../../windows/event-cpp-component-extensions.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C3797.  
  
```  
// C3797.cpp  
// compile with: /clr /c  
delegate void MyDel();  
  
ref class Class1 {  
public:  
   virtual event MyDel ^ E;  
};  
  
ref class Class2 : public Class1 {  
public:  
   virtual event MyDel ^ E override;   // C3797  
};  
  
// OK  
ref class Class3 : public Class1 {  
public:  
   virtual event MyDel ^ E {  
      void add(MyDel ^ d) override {}  
      void remove(MyDel ^ d) override {}  
   }  
};  
```