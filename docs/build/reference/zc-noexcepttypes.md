---
title: /Zc:noexceptTypes (Reglas noexcept de C++17)
ms.date: 06/04/2020
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 0f833209938ccc09cbc37235788b6f719d4d12d4
ms.sourcegitcommit: fe146adb3a02872538637196bb3c45aeeeaaf5c2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/08/2020
ms.locfileid: "84506876"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (Reglas noexcept de C++17)

El estándar c++ 17 crea `throw()` un alias para `noexcept` , quita `throw(` *`type-list`* `)` y y `throw(...)` permite incluir determinados tipos `noexcept` . Este cambio puede provocar una serie de problemas de compatibilidad de código fuente en el código que se ajusta a C++ 14 o anterior. La **`/Zc:noexceptTypes`** opción especifica la conformidad con el estándar c++ 17. **`/Zc:noexceptTypes-`** permite el comportamiento de C++ 14 y versiones anteriores cuando el código se compila en modo C++ 17.

## <a name="syntax"></a>Sintaxis

> **`/Zc:noexceptTypes`**\[**`-`**]

## <a name="remarks"></a>Comentarios

Cuando **`/Zc:noexceptTypes`** se especifica la opción, el compilador se ajusta al estándar de c++ 17 y trata [**`throw()`**](../../cpp/exception-specifications-throw-cpp.md) como alias para [**`noexcept`**](../../cpp/noexcept-cpp.md) , quita `throw(` *`type-list`* `)` y y permite la inclusión de `throw(...)` ciertos tipos **`noexcept`** . La **`/Zc:noexceptTypes`** opción solo está disponible cuando [**`/std:c++17`**](std-specify-language-standard-version.md) o [**`/std:c++latest`**](std-specify-language-standard-version.md) está habilitado. **`/Zc:noexceptTypes`** está habilitado de forma predeterminada para ajustarse al estándar ISO C++ 17. La [**`/permissive-`**](permissive-standards-conformance.md) opción no afecta a **`/Zc:noexceptTypes`** . Desactive esta opción especificando **`/Zc:noexceptTypes-`** para revertir al comportamiento de c++ 14 de **`noexcept`** cuando **`/std:c++17`** **`/std:c++latest`** se especifica o.

A partir de la versión 15,5 de Visual Studio 2017, el compilador de C++ diagnostica más especificaciones de excepción no coincidentes en las declaraciones en modo C++ 17 o cuando se especifica la [**`/permissive-`**](permissive-standards-conformance.md) opción.

Este ejemplo muestra cómo se comportan las declaraciones con un especificador de excepción cuando la **`/Zc:noexceptTypes`** opción está establecida o deshabilitada. Para mostrar el comportamiento cuando se establece, compile con `cl /EHsc /W4 noexceptTypes.cpp` . Para mostrar el comportamiento cuando está deshabilitado, compile con `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp` .

```cpp
// noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 noexceptTypes.cpp
// Compile by using: cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp

void f() throw();    // equivalent to void f() noexcept;
void f() { }         // warning C5043
void g() throw(...); // warning C5040

struct A
{
    virtual void f() throw();
};

struct B : A
{
    virtual void f() { } // error C2694
};
```

Cuando se compila con la configuración predeterminada **`/Zc:noexceptTypes`** , el ejemplo genera las advertencias enumeradas. Para actualizar el código, use lo siguiente en su lugar:

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A
{
    virtual void f() noexcept;
};

struct B : A
{
    virtual void f() noexcept { }
};
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la **Configuration Properties**página de propiedades línea de comandos de  >  **C/C++** de propiedades de configuración  >  **Command Line** .

1. Modifique la propiedad **opciones adicionales** para incluir *`/Zc:noexceptTypes`* o *`/Zc:noexceptTypes-`* y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Consulte también:

[**`/Zc`** Conformidad](zc-conformance.md)\
[noexcept](../../cpp/noexcept-cpp.md)\
[Especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md)
