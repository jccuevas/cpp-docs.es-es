---
title: Advertencia del compilador C4485 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4485
dev_langs:
- C++
helpviewer_keywords:
- C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b84d2976e31d5cc3a9b6547d0c4b02a61327ce0
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33270443"
---
# <a name="compiler-warning-c4485"></a>Advertencia del compilador C4485
'función_de_reemplazo': coincide con el método de clase ref base 'función_de_clase_base', pero no está marcada 'new' u 'override'; se supone 'new' (y 'virtual')  
  
 Reemplaza un descriptor de acceso, con o sin el `virtual` (palabra clave), una función de descriptor de acceso de la clase base, pero la `override` o `new` especificador no formaba parte de la firma de la función de reemplazo. Agregar el `new` o `override` especificador para resolver esta advertencia.  
  
 Vea [invalidar](../../windows/override-cpp-component-extensions.md) y [new (nueva ranura en vtable)](../../windows/new-new-slot-in-vtable-cpp-component-extensions.md) para obtener más información.  
  
 C4485 siempre se emite como un error. Use la [advertencia](../../preprocessor/warning.md) pragma para suprimir C4485.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4485  
  
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