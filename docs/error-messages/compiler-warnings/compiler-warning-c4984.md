---
title: ADVERTENCIA del compilador C4984
ms.date: 08/19/2019
f1_keywords:
- C4984
helpviewer_keywords:
- C4984
ms.openlocfilehash: 91ae30018c7de633d8ba23d538b301ad4bbac984
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/20/2019
ms.locfileid: "69632909"
---
# <a name="compiler-warning-c4984"></a>ADVERTENCIA del compilador C4984

> ' if constexpr ' es una extensión del lenguaje C++ 17

## <a name="remarks"></a>Comentarios

El compilador `if constexpr` encontró una expresión en el código compilado mediante el estándar predeterminado de c++ 14. Esta expresión se especifica empezando en el estándar C++ 17. Si necesita compatibilidad con C++ 11 o C++ 14, esta expresión no es portátil.

C4984 se emite como un error de forma predeterminada, pero se elimina. Para habilitar esta expresión compilando el código como C++ 17, use [/STD: c++ 17 o/STD: C + + latest](../../build/reference/std-specify-language-standard-version.md). Para usar la `if constexpr` expresión en el código compilado para c++ 14 como extensión de Microsoft, puede suprimir, deshabilitar o cambiar el nivel de advertencia del mensaje de error. Puede usar [/wd4984](../../build/reference/compiler-option-warning-level.md) para deshabilitar C4984 o __/w__*N*__4984__ para habilitarlo como una advertencia de nivel *N* en lugar de un error. O bien, use [#pragma ADVERTENCIA (suprimir: 4984)](../../preprocessor/warning.md) antes de la línea que produce la advertencia en el archivo de código fuente.

Esta advertencia está disponible a partir de la versión 15,3 de Visual Studio 2017. Para obtener información sobre cómo deshabilitar las advertencias introducidas en una versión de compilador determinada o posterior, vea [advertencias del compilador por versión del](compiler-warnings-by-compiler-version.md)compilador.

## <a name="example"></a>Ejemplo

Este ejemplo genera C4984 y muestra cómo corregirlo:

```cpp
// C4984.cpp
// compile with: cl /EHsc C4984.cpp
#include <iostream>

int main()
{
    constexpr bool compile_time = true;
    // Uncomment the following line or use /std:c++17 to fix
    // #pragma warning(suppress:4984)
    if constexpr (compile_time)
    {
        std::cout << "compile_time is true";
    }
    else
    {
        std::cout << "compile_time is false";
    }
}
```
