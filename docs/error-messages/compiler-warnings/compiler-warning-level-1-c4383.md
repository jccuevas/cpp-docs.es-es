---
title: Compilador advertencia (nivel 1) C4383 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4383
dev_langs:
- C++
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b78209cf4e3e320cca8b161a4e6c99eaca6d771c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4383"></a>Advertencia del compilador (nivel 1) C4383
'operador_eliminacióndereferencias_instancias': el significado de desreferenciar un identificador puede cambiar cuando existe un operador definido por el usuario 'operador'; escribir el operador como una función estática para indicar explícitamente el operando  
  
 Cuando se agrega un reemplazo de instancias definido por el usuario del operador de desreferenciación en un tipo administrado, podría invalidar la capacidad de operador de desreferenciación del tipo para devolver el objeto del identificador. Considere la posibilidad de escribir un estático definido por el usuario operador de desreferenciación.  
  
 Para obtener más información, consulte [identificador a un operador de objeto (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md) y [operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).  
  
 Además, un operador de la instancia no está disponible para otros compiladores de lenguaje a través de los metadatos que se hace referencia. Para obtener más información, consulte [operadores definidos por el usuario (C++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C4383.  
  
```  
// C4383.cpp  
// compile with: /clr /W1  
  
ref struct S {  
   int operator*() { return 0; }   // C4383  
};  
  
ref struct T {  
   static int operator*(T%) { return 0; }  
};   
  
int main() {  
   S s;  
   S^ pS = %s;  
  
   T t;  
   T^ pT = %t;  
   T% rT = *pT;  
}  
```