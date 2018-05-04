---
title: '-Zc: noexceptTypes (C ++ 17 noexcept reglas) | Documentos de Microsoft'
ms.date: 11/14/2017
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zc:noexceptTypes
dev_langs:
- C++
helpviewer_keywords:
- /Zc:noexceptTypes
- Zc:noexceptTypes
- -Zc:noexceptTypes
ms.assetid: 1cbf7e3c-0f82-4f91-84dd-612bcf26d2c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 25ad2a662af2cda49e3e8dd8c769fa75dafee94b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zcnoexcepttypes-c17-noexcept-rules"></a>/Zc:noexceptTypes (c ++ 17 noexcept reglas)

Hace que el estándar C ++ 17 `throw()` como un alias para `noexcept`, quita `throw(<type list>)` y `throw(...)`y permite determinados tipos debe incluir `noexcept`. Esto puede provocar una serie de problemas de compatibilidad de origen en el código que se ajuste a C ++ 14 o versiones anteriores. El **/Zc:noexceptTypes** opción puede especificar la conformidad con el estándar C ++ 17 o permitir la C ++ 14 y versiones anterior de comportamiento cuando se compila código en modo de C ++ 17.

## <a name="syntax"></a>Sintaxis

> **/Zc:noexceptTypes**[-]

## <a name="remarks"></a>Comentarios

Cuando el **/Zc:noexceptTypes** se especifica la opción, el compilador cumple el estándar C ++ 17 y trata [throw()](../../cpp/exception-specifications-throw-cpp.md) como un alias para [noexcept](../../cpp/noexcept-cpp.md), quita `throw(<type list>)`y `throw(...)`y permite determinados tipos debe incluir `noexcept`. El **/Zc:noexceptTypes** opción sólo está disponible cuando [/std:c ++ 17](std-specify-language-standard-version.md) o [/std:latest](std-specify-language-standard-version.md) está habilitado. **/Zc:noexceptTypes** está habilitada de forma predeterminada para que se ajuste a la norma ISO C ++ 17 estándar. El [/ permisivo-](permissive-standards-conformance.md) no afecta la opción **/Zc:noexceptTypes**. Desactivar esta opción mediante la especificación de **/Zc:noexceptTypes-** para revertir al comportamiento 14 C ++ de `noexcept` cuando **/std::C ++ 17** o **/std::latest** se especifica.

A partir de Visual Studio 2017 versión 15,5, el compilador de C++ diagnostica más especificaciones de excepciones que no coincidan en declaraciones de C ++ 17 modo o cuando la [/ permisivo-](permissive-standards-conformance.md) se especifica la opción.

Este ejemplo muestra cómo comportan las declaraciones con un especificador de excepción cuando la **/Zc:noexceptTypes** opción está establecida o desactivada. Para mostrar el comportamiento cuando se establece, compile con `cl /EHsc /W4 noexceptTypes.cpp`. Para mostrar el comportamiento cuando está deshabilitado, compile con `cl /EHsc /W4 /Zc:noexceptTypes- noexceptTypes.cpp`.

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

Cuando se compila con la configuración predeterminada **/Zc:noexceptTypes**, el ejemplo genera las advertencias de la lista. Para actualizar el código, use lo siguiente en su lugar:

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

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zc:noexceptTypes** o **/Zc:noexceptTypes-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)  
[noexcept](../../cpp/noexcept-cpp.md)  
[Especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md)  
