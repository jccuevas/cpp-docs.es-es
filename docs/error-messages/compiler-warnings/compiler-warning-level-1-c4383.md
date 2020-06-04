---
title: Advertencia del compilador (nivel 1) C4383
ms.date: 11/04/2016
f1_keywords:
- C4383
helpviewer_keywords:
- C4383
ms.assetid: 96c0e52d-874e-4b57-a154-0e49b6a00fae
ms.openlocfilehash: 1c4a7ca806430c73c8e8396e596782253cc06f09
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162743"
---
# <a name="compiler-warning-level-1-c4383"></a>Advertencia del compilador (nivel 1) C4383

' instance_dereference_operator ': el significado de desreferenciar un identificador puede cambiar cuando existe un operador ' Operator ' definido por el usuario; escribir el operador como una función estática para que sea explícito sobre el operando

Cuando se agrega una invalidación de instancia definida por el usuario del operador de desreferencia en un tipo administrado, se puede reemplazar la capacidad del operador de desreferenciación del tipo para devolver el objeto del identificador. Considere la posibilidad de escribir un operador de desreferencia estático definido por el usuario.

Para obtener más información, consulte [identificador del operador de objeto (^)](../../extensions/handle-to-object-operator-hat-cpp-component-extensions.md) y [operador de referencia de seguimiento](../../extensions/tracking-reference-operator-cpp-component-extensions.md).

Además, un operador de instancia no está disponible para otros compiladores de lenguaje a través de metadatos a los que se hace referencia. Para obtener más información, consulte [operadores definidos por elC++usuario (/CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4383.

```cpp
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
