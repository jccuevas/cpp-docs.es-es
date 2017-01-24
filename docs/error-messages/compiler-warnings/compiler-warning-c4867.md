---
title: "Advertencia del compilador C4867 | Microsoft Docs"
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
  - "C4867"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4867"
ms.assetid: 8a257d70-c3a7-462d-b285-e57c952a8bf7
caps.latest.revision: 16
caps.handback.revision: 16
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4867
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función' : falta la lista de argumentos de la llamada a la función, utilice 'llamada' para crear un puntero al miembro  
  
 Un puntero a la función miembro se inicializó incorrectamente.  
  
 Esta advertencia también se puede generar como resultado del trabajo de conformidad de compilador realizado para Visual C\+\+ 2005: la conformidad puntero\-a\-miembro mejorada.  El código que compiló antes de Visual C\+\+ 2005 ahora generará C4867.  
  
 Esta advertencia siempre se emite como error.  Utilice el pragma [warning](../../preprocessor/warning.md) para deshabilitar esta advertencia.  Para obtener más información sobre C4867 y MFC\/ATL, vea [\_ATL\_ENABLE\_PTM\_WARNING](../Topic/_ATL_ENABLE_PTM_WARNING.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4867.  
  
```  
// C4867.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b = {f};   // C4867  
      B b2 = {&A::f};   // OK  
   }  
};  
```