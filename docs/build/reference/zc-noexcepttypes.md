---
title: /Zc:noexceptTypes (Reglas noexcept de C++17)
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: 35bea7c2c629c615c60a6136f289b6b11926c054
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/05/2019
ms.locfileid: "73624863"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (Reglas noexcept de C++17)

El estándar C++ 17 realiza `throw()` un alias para `noexcept`, quita `throw(<type list>)` y `throw(...)`, y permite que ciertos tipos incluyan `noexcept`. Este cambio puede provocar una serie de problemas de compatibilidad de código fuente en el código que se ajusta a C++ 14 o anterior. La opción **/Zc: noexceptTypes** especifica la conformidad con el estándar c++ 17. **/Zc: noexceptTypes:** permite el comportamiento de c++ 14 y versiones anteriores cuando el código se compila en modo c++ 17.

## <a name="syntax"></a>Sintaxis

> **/Zc: noexceptTypes**[-]

## <a name="remarks"></a>Comentarios

Cuando se especifica la opción **/Zc: noexceptTypes** , el compilador se ajusta al estándar de c++ 17 y trata [Throw ()](../../cpp/exception-specifications-throw-cpp.md) como un alias para [noexception](../../cpp/noexcept-cpp.md), quita `throw(<type list>)` y `throw(...)`y permite que determinados tipos incluyan `noexcept`. La opción **/Zc: noexceptTypes** solo está disponible cuando se ha habilitado [/STD: c++ 17](std-specify-language-standard-version.md) o [/STD: latest](std-specify-language-standard-version.md) . **/Zc: noexceptTypes** está habilitado de forma predeterminada para ajustarse al estándar ISO c++ 17. La opción [/permissive-](permissive-standards-conformance.md) no afecta a **/Zc: noexceptTypes**. Desactive esta opción especificando **/Zc: noexceptTypes-** para revertir al comportamiento de c++ 14 de `noexcept` cuando se especifica **/STD: c++ 17** o **/STD: latest** .

A partir de la versión 15,5 de Visual Studio C++ 2017, el compilador diagnostica más especificaciones de excepción no coincidentes en las declaraciones del modo c++ 17 o cuando se especifica la opción [/permissive-](permissive-standards-conformance.md) .

En este ejemplo se muestra cómo se comportan las declaraciones con un especificador de excepción cuando la opción **/Zc: noexceptTypes** está establecida o deshabilitada. Para mostrar el comportamiento cuando se establece, compile con `cl /EHsc /W4 noexceptTypes.cpp`. Para mostrar el comportamiento cuando está deshabilitado, compile con `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Cuando se compila con la configuración predeterminada **/Zc: noexceptTypes**, el ejemplo genera las advertencias enumeradas. Para actualizar el código, use lo siguiente en su lugar:

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Seleccione la página de propiedades **Propiedades de configuración** > **C /C++**  > **Línea de comandos**.

1. Modifique la propiedad **opciones adicionales** para incluir **/Zc: noexceptTypes** o **/Zc: noexceptTypes-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/ZC (conformidad)](zc-conformance.md)\
[noexception](../../cpp/noexcept-cpp.md)\
[Especificaciones de excepciones (Throw)](../../cpp/exception-specifications-throw-cpp.md)
