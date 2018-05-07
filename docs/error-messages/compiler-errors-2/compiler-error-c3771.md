---
title: Error del compilador C3771 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3771
dev_langs:
- C++
helpviewer_keywords:
- C3771
ms.assetid: 68c23b25-7f21-4eaa-8f7e-38fda1130a69
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8adfdb1562cc9efbe208bd7c887b7c4aa77ddd82
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3771"></a>Error del compilador C3771
"identifier": no se puede encontrar ninguna declaración friend en el ámbito del espacio de nombres más próximo  
  
La declaración de la plantilla de clase de la plantilla especificada *identifier* no se encuentra en el espacio de nombres actual.  
  
### <a name="to-correct-this-error"></a>Para corregir este error  
  
-   Asegúrese de que la declaración de la plantilla de clase del identificador de plantilla está definida en el espacio de nombres actual o que el identificador de plantilla sea un nombre completo.  
  
## <a name="example"></a>Ejemplo  
En el ejemplo de código siguiente se declara una función y plantilla de clase en el espacio de nombres `NA`, pero se intenta declarar una plantilla de función friend en el espacio de nombres `NB`.  
  
```cpp  
// C3771.cpp   
// compile with: /c  
  
namespace NA {  
template<class T> class A {  
    void aFunction(T t) {};  
    };  
}  
// using namespace NA;  
namespace NB {  
    class X {  
        template<class T> friend void A<T>::aFunction(T); // C3771  
// try the following line instead  
//      template<class T> friend void NA::A<T>::aFunction(T);  
// or try "using namespace NA;" instead.  
    };  
}  
```  
  
## <a name="see-also"></a>Vea también  
[Templates](../../cpp/templates-cpp.md) (Plantillas [C++])  