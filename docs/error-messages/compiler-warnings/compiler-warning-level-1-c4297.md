---
title: Advertencia del compilador (nivel 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 07dd6c65498ddd0d377ec3e0fbc7b44e52bec96b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540262"
---
# <a name="compiler-warning-level-1-c4297"></a>Advertencia del compilador (nivel 1) C4297

'función': se suponía que la función no iniciaba una excepción, pero lo hace

Una declaración de función contiene un (posiblemente implícito) `noexcept` especificador, vacía `throw` especificador de excepción o un [__declspec (nothrow)](../../cpp/nothrow-cpp.md) atributo y la definición contiene uno o varios [throw ](../../cpp/try-throw-and-catch-statements-cpp.md) instrucciones. Para resolver la advertencia C4297, no intente iniciar excepciones en funciones declaradas `__declspec(nothrow)`, `noexcept(true)` o `throw()`. O bien, quite la especificación `noexcept`, `throw()` o `__declspec(nothrow)`.

De manera predeterminada, el compilador genera especificadores `noexcept(true)` implícitos para destructores definidos por el usuario, funciones de desasignador y funciones miembro especiales generadas por el compilador. Esto cumple la norma ISO C ++ 11. Para evitar la generación de especificadores noexcept implícitos y revertir al compilador que el comportamiento no estándar de Visual Studio 2013, use el **/Zc:implicitNoexcept-** opción del compilador. Para obtener más información, consulte [/Zc: implicitnoexcept (especificadores de excepción implícita)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Para obtener más información sobre las especificaciones de excepciones, vea [especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md). Consulte también [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) para obtener información sobre cómo modificar el comportamiento en tiempo de compilación del control de excepciones.

Esta advertencia también se genera para __declspec ([dllexport](../../cpp/dllexport-dllimport.md)) las funciones marcadas como extern "C", incluso si son las funciones de C++.

El siguiente ejemplo genera la advertencia C4297.

```
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```