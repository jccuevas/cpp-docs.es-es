---
title: '/ Zc: noexcepttypes (reglas c ++ 17 noexcept)'
ms.date: 11/14/2017
f1_keywords:
- /Zc:noexceptTypes
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
ms.openlocfilehash: f5f2fa3ef85e7ff15b28188e45a4ec397878873c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462236"
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/ Zc: noexcepttypes (reglas c ++ 17 noexcept)

Hace que el estándar C ++ 17 `throw()` como un alias para `noexcept`, quita `throw(<type list>)` y `throw(...)`y permite que ciertos tipos incluir `noexcept`. Esto puede provocar una serie de problemas de compatibilidad de origen en el código que se ajuste a C ++ 14 o versiones anteriores. El **/Zc: noexcepttypes** opción puede especificar la conformidad con el estándar C ++ 17 o permitir la C ++ 14 y versiones anterior el comportamiento cuando se compila código en modo C ++ 17.

## <a name="syntax"></a>Sintaxis

> **/ Zc: noexcepttypes**[-]

## <a name="remarks"></a>Comentarios

Cuando el **/Zc: noexcepttypes** se especifica la opción, el compilador cumple el estándar C ++ 17 y trata [throw()](../../cpp/exception-specifications-throw-cpp.md) como un alias para [noexcept](../../cpp/noexcept-cpp.md), quita `throw(<type list>)`y `throw(...)`y permite que ciertos tipos incluir `noexcept`. El **/Zc: noexcepttypes** opción solo está disponible cuando [/std: c ++ 17](std-specify-language-standard-version.md) o [/std:latest](std-specify-language-standard-version.md) está habilitado. **/ Zc: noexcepttypes** está habilitada de forma predeterminada para cumplir con la norma ISO C ++ 17 estándar. El [/ permissive-](permissive-standards-conformance.md) no afecta la opción **/Zc: noexcepttypes**. Desactivar esta opción mediante la especificación de **/Zc:noexceptTypes-** para revertir al comportamiento 14 C ++ de `noexcept` cuando **/std::C ++ 17** o **/std::latest** se especifica.

A partir de Visual Studio 2017 versión 15.5, el compilador de C++ diagnostica más especificaciones de excepción no coincidentes en las declaraciones en modo C ++ 17 o cuando el [/ permissive-](permissive-standards-conformance.md) se especifica la opción.

Este ejemplo muestra cómo comportan las declaraciones con un especificador de excepción cuando el **/Zc: noexcepttypes** opción está establecida o desactivada. Para mostrar el comportamiento cuando se establece, compile con `cl /EHsc /W4 noexceptTypes.cpp`. Para mostrar el comportamiento cuando está deshabilitado, compile con `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Al compilar con la configuración predeterminada **/Zc: noexcepttypes**, el ejemplo genera las advertencias enumeradas. Para actualizar el código, use lo siguiente en su lugar:

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: noexcepttypes** o **/Zc:noexceptTypes-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md)
