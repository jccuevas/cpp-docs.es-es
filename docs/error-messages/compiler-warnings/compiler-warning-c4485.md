---
title: "Advertencia del compilador C4485 | Microsoft Docs"
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
  - "C4485"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4485"
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4485
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función\_de\_reemplazo' : coincide con el método de clase de referencia base 'función\_de\_clase\_base', pero no está marcado como 'new' ni 'override'; se da por supuesto que es 'new' \(y 'virtual'\)  
  
 Un descriptor de acceso reemplaza, con o sin la palabra clave `virtual`, una función de descriptor de acceso a clase base, pero el especificador `override` o `new` no formaba parte de la firma de función de reemplazo.  Agregue el especificador `new` y `override` para resolver esta advertencia.  
  
 Para obtener más información, vea [override](../../windows/override-cpp-component-extensions.md) y [new \(nueva ranura en vtable\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md).  
  
 La advertencia C4485 siempre se emite como error.  Utilice la pragma [warning](../../preprocessor/warning.md) para suprimir C4485.  
  
## Ejemplo  
 El ejemplo siguiente genera C4485:  
  
```  
// C4485.cpp  
// compile with: /clr  
delegate void Del();  
  
ref struct A {  
   virtual event Del ^E;  
};  
  
ref struct B : A {  
   virtual event Del ^E;   // C4485  
};  
  
ref struct C : B {  
   virtual event Del ^E {  
      void raise() override {}  
      void add(Del ^) override {}  
      void remove(Del^) override {}  
   }  
};  
```