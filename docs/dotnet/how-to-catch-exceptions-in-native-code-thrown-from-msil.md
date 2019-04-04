---
title: Filtrar Detectar excepciones en código nativo iniciada desde MSIL
ms.date: 11/04/2016
helpviewer_keywords:
- exceptions, catching
- catching exceptions, thrown from MSIL
- MSIL, catching exceptions in native code
ms.assetid: c15afd2b-8505-43bf-8a4a-f1d41532a124
ms.openlocfilehash: 95ce7a2afabc34ea78376b12da61f419dab4af34
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776562"
---
# <a name="how-to-catch-exceptions-in-native-code-thrown-from-msil"></a>Filtrar Detectar excepciones en código nativo iniciada desde MSIL

En código nativo, puede detectar las excepciones de C++ nativa de MSIL.  Se pueden detectar las excepciones de CLR con `__try` y `__except`.

Para obtener más información, consulte [control de excepciones estructurado (C/C ++)](../cpp/structured-exception-handling-c-cpp.md) y [control de excepciones de C++](../cpp/cpp-exception-handling.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente define un módulo con dos funciones, uno que produce una excepción nativa y otro que produce una excepción de MSIL.

```
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

El ejemplo siguiente define un módulo que se detecta un nativo y las excepciones de MSIL.

```
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

## <a name="see-also"></a>Vea también

[Control de excepciones](../extensions/exception-handling-cpp-component-extensions.md)
