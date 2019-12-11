---
title: Advertencia del compilador (nivel 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 3a8f2093e90f8a681d171e19e2b8a066546f8684
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990662"
---
# <a name="compiler-warning-level-4-c4571"></a>Advertencia del compilador (nivel 4) C4571

Información: la semántica de catch (...) cambió desde Visual C++ 7,1; ya no se detectan excepciones estructuradas (SEH)

C4571 se genera para cada bloque catch (...) al compilar con **/EHS**.

Al compilar con **/EHS**, un bloque catch (...) no detectará una excepción estructurada (división por cero, puntero nulo, por ejemplo); un bloque catch (...) solo detectará C++ excepciones generadas explícitamente.  Para más información, consulte [Control de excepciones](../../cpp/exception-handling-in-visual-cpp.md).

De forma predeterminada, esta advertencia está desactivada.  Active esta advertencia para asegurarse de que, al compilar con **/EHS** , los bloques catch (...) no pretenden detectar excepciones estructuradas.  Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.

Puede resolver C4571 de una de las siguientes maneras:

- Compile con **/EHA** si aún desea que los bloques catch (...) detecten las excepciones estructuradas.

- No habilite C4571 si no desea que los bloques catch (...) detecten excepciones estructuradas, pero aún desea usar bloques catch (...).  Todavía puede detectar excepciones estructuradas mediante las palabras clave de control de excepciones estructurado ( **__try**, **__except**y **__finally**).  Pero recuerde que, cuando se produce una excepción, no se llamará a C++ los destructores de/EHS compilados cuando se produzca una excepción de SEH.

- Reemplace el bloque catch (...) por bloques catch para C++ excepciones específicas y, opcionalmente, agregue control de excepciones estructurado C++ alrededor del control de excepciones ( **__try**, **__except**y **__finally**).  Vea [control de excepciones estructurado (CC++/)](../../cpp/structured-exception-handling-c-cpp.md) para obtener más información.

Consulte [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) para obtener más información.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4571.

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
