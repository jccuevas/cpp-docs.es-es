---
title: Advertencia del compilador C4485 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4485
dev_langs: C++
helpviewer_keywords: C4485
ms.assetid: a6f2b437-ca93-4dcd-b9cb-df415e10df86
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 435e49a857e3c448ac7e5f7ef00bb9032320aa25
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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