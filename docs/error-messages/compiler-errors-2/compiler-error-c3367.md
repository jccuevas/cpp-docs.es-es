---
title: Error del compilador C3367
ms.date: 11/04/2016
f1_keywords:
- C3367
helpviewer_keywords:
- C3367
ms.assetid: e675d42b-f5b0-4d43-aab1-1f5024233102
ms.openlocfilehash: f53312fa9225270ef79d50d2ad351adce790d6fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456295"
---
# <a name="compiler-error-c3367"></a>Error del compilador C3367

'función_miembro_estática': no se puede usar la función estática para crear un delegado sin enlazar.

Cuando se llama a un delegado sin enlazar, debe pasar una instancia de un objeto. Puesto que se llama a una función miembro estática a través del nombre de clase, solo puede crear una instancia de un delegado sin enlazar con una función miembro de instancia.

Para obtener más información sobre los delegados sin enlazar, vea [Cómo: definir y usar delegados (C++ / c++ / CLI)](../../dotnet/how-to-define-and-use-delegates-cpp-cli.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C3367.

```cpp
// C3367.cpp
// compile with: /clr
ref struct R {
   void b() {}
   static void f() {}
};

delegate void Del(R^);

int main() {
   Del ^ a = gcnew Del(&R::b);   // OK
   Del ^ b = gcnew Del(&R::f);   // C3367
}
```