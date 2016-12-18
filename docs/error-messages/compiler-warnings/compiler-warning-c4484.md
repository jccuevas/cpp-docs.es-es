---
title: "Advertencia del compilador C4484 | Microsoft Docs"
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
  - "C4484"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4484"
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador C4484
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'override\_función' : coincide con el método de clase ref base 'función\_clase\_base', pero no está marcado como 'virtual', 'new' u 'override'; se da por supuesto que es 'new' \(y no 'virtual'\)  
  
 Al compilar con **\/clr**, el compilador no reemplazará de forma implícita una función de clase base, lo que significa que la función obtendrá una nueva ranura en la tabla vtable.  Para resolverlo, especifique explícitamente si una función es un reemplazo.  
  
 Para obtener más información, vea:  
  
-   [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [new \(nueva ranura en vtable\)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 La advertencia C4484 siempre se emite como error.  Utilice la directiva pragma [warning](../../preprocessor/warning.md) para suprimir la advertencia C4484.  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4484.  
  
```  
// C4484.cpp  
// compile with: /clr  
ref struct A {  
   virtual void Test() {}  
};  
  
ref struct B : A {  
   void Test() {}   // C4484  
};  
  
// OK  
ref struct C {  
   virtual void Test() {}  
   virtual void Test2() {}  
};  
  
ref struct D : C {  
   virtual void Test() new {}  
   virtual void Test2() override {}  
};  
```