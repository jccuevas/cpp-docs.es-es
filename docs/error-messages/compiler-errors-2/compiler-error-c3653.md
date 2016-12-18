---
title: "Error del compilador C3653 | Microsoft Docs"
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
  - "C3653"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3653"
ms.assetid: 316549d7-f7ef-4578-a2ba-57adc8aac527
caps.latest.revision: 12
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3653
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : no se puede utilizar como reemplazo con nombre: no se encontró una función que se va a reemplazar; compruebe si ha asignado nombre a la función explícitamente mediante un operador ::  
  
 Un reemplazo explícito especificaba una función que no se ha encontrado en ninguna interfaz.  Para obtener más información, vea [Reemplazos explícitos](../../windows/explicit-overrides-cpp-component-extensions.md).  
  
 El código siguiente genera el error C3653:  
  
```  
// C3653.cpp  
// compile with: /clr  
public interface struct I {  
   void h();  
};  
  
public ref struct X : public I {  
   virtual void f() new sealed = J {};   // C3653 no J in scope  
   virtual void g() {}   // OK  
   virtual void h() new sealed = I::h {};   // OK  
};  
```