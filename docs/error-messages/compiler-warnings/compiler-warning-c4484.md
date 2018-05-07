---
title: Advertencia del compilador C4484 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4484
dev_langs:
- C++
helpviewer_keywords:
- C4484
ms.assetid: 3d30e5b3-2297-45b7-a37a-1360056fdd0e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 75531c207f0136f16109b4d69d689b883998aae2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-c4484"></a>Advertencia del compilador C4484
'función_de_reemplazo': coincide con el método de clase ref base 'función_de_clase_base', pero no está marcado como 'virtual', 'new' o 'override'; se supone 'new' (y no 'virtual')  
  
 Cuando se compila con **/CLR**, el compilador no invalidará implícitamente una función de clase base, lo que significa que la función obtendrá una nueva ranura en vtable. Para resolver, especifique explícitamente si una función es un reemplazo.  
  
 Para obtener más información, consulte:  
  
-   [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [override](../../windows/override-cpp-component-extensions.md)  
  
-   [New (nueva ranura en vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md)  
  
 Advertencia C4484 siempre se emite como un error. Use la [advertencia](../../preprocessor/warning.md) pragma para suprimir la advertencia C4484.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera la advertencia C4484.  
  
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