---
title: Advertencia del compilador (nivel 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 61bc3951a7d57a5a4eefb69b5a0c4399df99160a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548803"
---
# <a name="compiler-warning-level-1-c4383"></a>Advertencia del compilador (nivel 1) C4383

'operador_eliminacióndereferencias_instancias': el significado de desreferenciar un identificador puede cambiar cuando existe un operador definido por el usuario 'operador'; Escriba el operador como función estática para que sea explícito sobre el operando

Al agregar un reemplazo de instancia definido por el usuario del operador de desreferenciación de un tipo administrado, potencialmente invalidar la capacidad de devolver el objeto del identificador de operador de desreferencia del tipo. Considere la posibilidad de operador de desreferenciación de escritura estática, definido por el usuario.

Para obtener más información, consulte [identificador de operador de objeto (^)](../../windows/handle-to-object-operator-hat-cpp-component-extensions.md) y [operador de referencia de seguimiento](../../windows/tracking-reference-operator-cpp-component-extensions.md).

Además, un operador de la instancia no está disponible para otros compiladores de lenguaje a través de metadatos que se hace referencia. Para obtener más información, consulte [operadores definidos por el usuario (C++ / c++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

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