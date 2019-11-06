---
title: ADVERTENCIA del compilador (nivel 1) C4297
ms.date: 11/04/2016
f1_keywords:
- C4297
helpviewer_keywords:
- C4297
ms.assetid: ba92fcdc-9f70-4f60-abe6-281f9582ca59
ms.openlocfilehash: 48ae909b9484fd0581f4691059272c5a488ea5fe
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626618"
---
# <a name="compiler-warning-level-1-c4297"></a>ADVERTENCIA del compilador (nivel 1) C4297

'función': se suponía que la función no iniciaba una excepción, pero lo hace

Una declaración de función contiene un especificador `noexcept` (posiblemente implícito), un especificador de excepción `throw` vacío o un atributo [_ _ declspec (nothrow)](../../cpp/nothrow-cpp.md) , y la definición contiene una o más instrucciones [Throw](../../cpp/try-throw-and-catch-statements-cpp.md) . Para resolver la advertencia C4297, no intente iniciar excepciones en funciones declaradas `__declspec(nothrow)`, `noexcept(true)` o `throw()`. O bien, quite la especificación `noexcept`, `throw()` o `__declspec(nothrow)`.

De manera predeterminada, el compilador genera especificadores `noexcept(true)` implícitos para destructores definidos por el usuario, funciones de desasignador y funciones miembro especiales generadas por el compilador. Esto cumple la norma ISO C ++ 11. Para evitar la generación de especificadores noexception implícitos y revertir el compilador al comportamiento no estándar de Visual Studio 2013, use la opción **/Zc: implicitNoexcept-** Compiler. Para obtener más información, vea [/Zc: implicitNoexcept (especificadores de excepción implícitos)](../../build/reference/zc-implicitnoexcept-implicit-exception-specifiers.md).

Para obtener más información sobre las especificaciones de excepción, vea [Especificaciones de excepciones (Throw)](../../cpp/exception-specifications-throw-cpp.md). Además, consulte [/EH (modelo de control de excepciones)](../../build/reference/eh-exception-handling-model.md) para obtener información sobre cómo modificar el comportamiento del control de excepciones en tiempo de compilación.

Esta advertencia también se genera para las funciones _ _ declspec ([dllexport](../../cpp/dllexport-dllimport.md)) marcadas como extern "C" C++ , incluso si son funciones.

El siguiente ejemplo genera la advertencia C4297.

```cpp
// C4297.cpp
// compile with: /W1 /LD
void __declspec(nothrow) f1()   // declared nothrow
// try the following line instead
// void f1()
{
   throw 1;   // C4297
}
```