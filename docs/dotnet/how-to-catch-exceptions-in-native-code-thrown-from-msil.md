---
title: 'Cómo: Detectar excepciones en código nativo iniciadas desde MSIL'
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 23adb573a62e93933c487f611c05aed4c08494ef
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545088"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Cómo: Detectar excepciones en código nativo iniciadas desde MSIL

En código nativo, puede detectar excepciones nativas C++ desde MSIL.  Puede detectar excepciones CLR con `__try` y `__except`.

Para obtener más información, vea [control de excepciones estructurado (C++C/)](../cpp/structured-exception-handling-c-cpp.md) y [procedimientos recomendados modernos C++ para excepciones y control de errores](../cpp/errors-and-exception-handling-modern-cpp.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se define un módulo con dos funciones, una que produce una excepción nativa y otra que produce una excepción de MSIL.

```cpp
// catch_MSIL_in_native.cpp
// compile with: /clr /c
void Test() {
   throw ("error");
}

void Test2() {
   throw (gcnew System::Exception("error2"));
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se define un módulo que detecta una excepción nativa y de MSIL.

```cpp
// catch_MSIL_in_native_2.cpp
// compile with: /clr catch_MSIL_in_native.obj
#include <iostream>
using namespace std;
void Test();
void Test2();

void Func() {
   // catch any exception from MSIL
   // should not catch Visual C++ exceptions like this
   // runtime may not destroy the object thrown
   __try {
      Test2();
   }
   __except(1) {
      cout << "caught an exception" << endl;
   }

}

int main() {
   // catch native C++ exception from MSIL
   try {
      Test();
   }
   catch(char * S) {
      cout << S << endl;
   }
   Func();
}
```

```Output
error
caught an exception
```

## <a name="see-also"></a>Consulte también

[Control de excepciones](../extensions/exception-handling-cpp-component-extensions.md)
