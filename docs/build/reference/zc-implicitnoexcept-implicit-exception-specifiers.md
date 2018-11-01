---
title: /Zc:implicitNoexcept (especificadores de excepción implícita)
ms.date: 03/06/2018
f1_keywords:
- /Zc:implicitNoexcept
helpviewer_keywords:
- /Zc:implicitNoexcept
- Zc:implicitNoexcept
- -Zc:implicitNoexcept
ms.assetid: 71807652-6f9d-436b-899e-f52daa6f500b
ms.openlocfilehash: 0ca03cc2a3afa0d5665f217ccb0d41eb1e41d3be
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50480940"
---
# <a name="zcimplicitnoexcept-implicit-exception-specifiers"></a>/Zc:implicitNoexcept (especificadores de excepción implícita)

Cuando el **/Zc: implicitnoexcept** se especifica la opción, el compilador agrega implícita [noexcept](../../cpp/noexcept-cpp.md) especificador de excepción para las funciones miembro especiales definidas por el compilador y los destructores definidos por el usuario y desasignadores. De forma predeterminada, **/Zc: implicitnoexcept** está habilitado para cumplir el estándar C ++ 11 de ISO. Al desactivar esta opción, se deshabilita el `noexcept` implícito en los destructores y desasignadores definidos por el usuario, así como las funciones miembro especiales definidas por el compilador.

## <a name="syntax"></a>Sintaxis

> **/ Zc: implicitnoexcept**[**-**]

## <a name="remarks"></a>Comentarios

**/ Zc: implicitnoexcept** indica al compilador que siga la sección 15.4 de la imagen ISO C ++ 11 estándar. Agrega implícitamente una `noexcept` especificador de excepción para cada función miembro especial declarada implícitamente o explícitamente establecidas como valor predeterminado, el constructor predeterminado, copiar el constructor, el constructor de movimiento, destructor, operador de asignación o asignación de movimiento operador y cada función de destructor o desasignador definido por el usuario. Un desasignador definido por el usuario tiene un especificador de excepción `noexcept(true)` implícito. Para los destructores definidos por el usuario, el especificador de excepción implícito es `noexcept(true)` a menos que una clase de miembro independiente o una clase base tengan un destructor que no sea `noexcept(true)`. Para las funciones miembro especiales generadas por el compilador, si cualquier función invocada directamente por esta función es `noexcept(false)`, el especificador de excepción implícito será `noexcept(false)`. De lo contrario, el especificador de excepción implícito es `noexcept(true)`.

El compilador no genera ningún especificador de excepción implícito para las funciones declaradas mediante los especificadores explícitos `noexcept` o `throw`, o un atributo `__declspec(nothrow)`.

De forma predeterminada, **/Zc: implicitnoexcept** está habilitado. El [/ permissive-](permissive-standards-conformance.md) no afecta la opción **/Zc: implicitnoexcept**.

Si se deshabilita la opción especificando **/Zc:implicitNoexcept-**, el compilador no genera ningún especificador de excepción implícito. Este comportamiento es el mismo que en Visual Studio 2013, donde los destructores y desasignadores que no disponían de especificadores de excepción podían tener instrucciones `throw`. De forma predeterminada y cuándo **/Zc: implicitnoexcept** se especifica si un `throw` se encuentra la instrucción en tiempo de ejecución en una función con implícita `noexcept(true)` especificador, provoca una invocación inmediata de `std::terminate`, y no se garantiza el comportamiento normal de desenredado los controladores de excepciones. Para ayudar a identificar esta situación, el compilador genera [advertencia del compilador (nivel 1) C4297](../../error-messages/compiler-warnings/compiler-warning-level-1-c4297.md). Si el `throw` es intencionada, le recomendamos que cambie la declaración de función para que tenga una explícita `noexcept(false)` especificador en lugar de usar **/Zc:implicitNoexcept-**.

Este ejemplo muestra cómo comporta un destructor definido por el usuario que no tenga ningún especificador de excepción explícito cuando la **/Zc: implicitnoexcept** opción está establecida o desactivada. Para mostrar el comportamiento cuando se establece, compile con `cl /EHsc /W4 implicitNoexcept.cpp`. Para mostrar el comportamiento cuando está deshabilitado, compile con `cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp`.

```cpp
// implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 implicitNoexcept.cpp
// Compile by using: cl /EHsc /W4 /Zc:implicitNoexcept- implicitNoexcept.cpp

#include <iostream>
#include <cstdlib>      // for std::exit, EXIT_FAILURE, EXIT_SUCCESS
#include <exception>    // for std::set_terminate

void my_terminate()
{
    std::cout << "Unexpected throw caused std::terminate" << std::endl;
    std::cout << "Exit returning EXIT_FAILURE" << std::endl;
    std::exit(EXIT_FAILURE);
}

struct A {
    // Explicit noexcept overrides implicit exception specification
    ~A() noexcept(false) {
        throw 1;
    }
};

struct B : public A {
    // Compiler-generated ~B() definition inherits noexcept(false)
    ~B() = default;
};

struct C {
    // By default, the compiler generates an implicit noexcept(true)
    // specifier for this user-defined destructor. To enable it to
    // throw an exception, use an explicit noexcept(false) specifier,
    // or compile by using /Zc:implicitNoexcept-
    ~C() {
        throw 1; // C4297, calls std::terminate() at run time
    }
};

struct D : public C {
    // This destructor gets the implicit specifier of its base.
    ~D() = default;
};

int main()
{
    std::set_terminate(my_terminate);

    try
    {
        {
            B b;
        }
    }
    catch (...)
    {
        // exception should reach here in all cases
        std::cout << "~B Exception caught" << std::endl;
    }
    try
    {
        {
            D d;
        }
    }
    catch (...)
    {
        // exception should not reach here if /Zc:implicitNoexcept
        std::cout << "~D Exception caught" << std::endl;
    }
    std::cout << "Exit returning EXIT_SUCCESS" << std::endl;
    return EXIT_SUCCESS;
}
```

Al compilar con la configuración predeterminada **/Zc: implicitnoexcept**, el ejemplo genera este resultado:

```Output
~B Exception caught
Unexpected throw caused std::terminate
Exit returning EXIT_FAILURE
```

Cuando se compila con la opción **/Zc:implicitNoexcept-**, el ejemplo genera este resultado:

```Output
~B Exception caught
~D Exception caught
Exit returning EXIT_SUCCESS
```

Para obtener más información sobre los problemas de conformidad de Visual C++, vea [Nonstandard Behavior](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zc: implicitnoexcept** o **/Zc:implicitNoexcept-** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[/Zc (Ajuste)](../../build/reference/zc-conformance.md)<br/>
[noexcept](../../cpp/noexcept-cpp.md)<br/>
[Especificaciones de excepciones (throw)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[terminate](../../standard-library/exception-functions.md#terminate)<br/>
