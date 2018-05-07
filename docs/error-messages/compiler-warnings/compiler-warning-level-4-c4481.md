---
title: Compilador advertencia (nivel 4) C4481 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4481
dev_langs:
- C++
helpviewer_keywords:
- C4481
ms.assetid: 7bfd4e0c-b452-4e6c-b7c4-ac5cc93fe4ea
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: aeef5f2121808c5444af942fac0e3b72919f2354
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4481"></a>Advertencia del compilador (nivel 4) C4481
ha utilizado una extensión no estándar: 'palabra clave' especificador de reemplazo  
  
 Se utiliza una palabra clave que no está en el estándar de C++, por ejemplo, uno de los especificadores de invalidación que también funciona bajo/CLR.  Para obtener más información, vea  
  
-   [/clr (Compilación de Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Especificadores de invalidación](../../windows/override-specifiers-cpp-component-extensions.md)  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4481.  
  
```  
// C4481.cpp  
// compile with: /W4 /c  
class B {  
   virtual void f(unsigned);  
};  
  
class C : B {  
   void f(unsigned) override;   // C4481  
   void f2(unsigned);  
};  
```