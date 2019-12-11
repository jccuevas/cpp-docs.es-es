---
title: Advertencia del compilador (nivel 4) C4702
ms.date: 11/04/2016
f1_keywords:
- C4702
helpviewer_keywords:
- C4702
ms.assetid: d8198c1e-8762-42a6-9e6b-cb568b7a1686
ms.openlocfilehash: 5e46bfef925f999ed7f04b5bbe7c88800209ed14
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990651"
---
# <a name="compiler-warning-level-4-c4702"></a>Advertencia del compilador (nivel 4) C4702

código inaccesible

Esta advertencia es el resultado del trabajo de conformidad del compilador realizado para Visual Studio .NET 2003: código inaccesible. Cuando el compilador (back-end) detecta código inaccesible, genera C4702, una advertencia de nivel 4.

Para el código que es válido en las versiones de Visual Studio .NET 2003 y Visual Studio .NET de C++visual, quite el código inaccesible o asegúrese de que todo el flujo de ejecución pueda acceder a todo el código fuente.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4702.

```cpp
// C4702.cpp
// compile with: /W4
#include <stdio.h>

int main() {
   return 1;
   printf_s("I won't print.\n");   // C4702 unreachable
}
```

## <a name="example"></a>Ejemplo

Al compilar con las funciones **/GX**, **/EHC**, **/EHsc**o **/EHac** y usar funciones extern de c, el código puede volverse inaccesible porque las funciones extern de c no se inician, por lo que el bloque catch no es accesible.  Si cree que esta advertencia no es válida porque una función puede iniciar, compile con **/EHA** o **/EHS**, dependiendo de la excepción que se produzca.

Para obtener más información, consulte [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) .

En el ejemplo siguiente se genera C4702.

```cpp
// C4702b.cpp
// compile with: /W4 /EHsc
#include <iostream>

using namespace std;
extern "C" __declspec(dllexport) void Function2(){}

int main() {
   try {
      Function2();
   }
   catch (...) {
      cout << "Exp: Function2!" << endl;   // C4702
   }
}
```
