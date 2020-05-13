---
title: switchStatement (C++)
description: Referencia a la instrucción estándar switch de c++ en Microsoft Visual Studio c++.
ms.date: 04/25/2020
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
no-loc:
- switch
- case
- default
- break
- while
- opt
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: d43a7a64b5a74f00833093ae8999d73edd7f5753
ms.sourcegitcommit: c4cf8976939dd0e13e25b82930221323ba6f15d4
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/12/2020
ms.locfileid: "83204161"
---
# <a name="switch-statement-c"></a>`switch`Statement (C++)

Permite la selección entre varias secciones de código, dependiendo del valor de una expresión entera.

## <a name="syntax"></a>Sintaxis

> *`selection-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp;__`switch`__&nbsp;__`(`__&nbsp;*`init-statement`*<sub>opt</sub> <sup>C++ 17</sup>&nbsp;*`condition`*&nbsp;__`)`__&nbsp;*`statement`*

> *`init-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression-statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`simple-declaration`*

> *`condition`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; *`expression`*\
> &nbsp;&nbsp;&nbsp;&nbsp; *`attribute-specifier-seq`*<sub>opt</sub>&nbsp;*`decl-specifier-seq`*&nbsp;*`declarator`*&nbsp;*`brace-or-equal-initializer`*

> *`labeled-statement`*:\
> &nbsp;&nbsp;&nbsp;&nbsp; __`case`__&nbsp;*`constant-expression`*&nbsp;__`:`__&nbsp;*`statement`*\
> &nbsp;&nbsp;&nbsp;&nbsp; __`default`__&nbsp;__`:`__&nbsp;*`statement`*

## <a name="remarks"></a>Observaciones

Una __`switch`__ instrucción hace que el control se transfiera a uno *`labeled-statement`* en su cuerpo de instrucción, dependiendo del valor de *`condition`* .

*`condition`* Debe tener un tipo entero o ser un tipo de clase que tenga una conversión no ambigua a un tipo entero. La promoción de entero tiene lugar tal y como se describe en [conversiones estándar](standard-conversions.md).

El __`switch`__ cuerpo de la instrucción consta de una serie de __`case`__ etiquetas y una __`default`__ etiqueta opcional. Una *`labeled-statement`* es una de estas etiquetas y las instrucciones siguientes. Las instrucciones etiquetadas no son requisitos sintácticos, pero la __`switch`__ instrucción no tiene sentido sin ellas. Dos *`constant-expression`* valores de __`case`__ las instrucciones no pueden evaluarse como el mismo valor. La __`default`__ etiqueta solo puede aparecer una vez. __`default`__ A menudo, la instrucción se coloca al final, pero puede aparecer en cualquier parte del cuerpo de la __`switch`__ instrucción. Una __`case`__ __`default`__ etiqueta o solo puede aparecer dentro de una __`switch`__ instrucción.

*`constant-expression`* En cada __`case`__ etiqueta se convierte en un valor constante que es del mismo tipo que *`condition`* . A continuación, se compara con *`condition`* para determinar si son iguales. El control pasa a la primera instrucción después del __`case`__ *`constant-expression`* valor que coincide con el valor de *`condition`* . El comportamiento resultante se muestra en la siguiente tabla.

### <a name="switch-statement-behavior"></a>`switch`comportamiento de la instrucción

| Condición | Acción |
|--|--|
| El valor convertido coincide con el de la expresión de control promovida. | El control se transfiere a la instrucción que sigue a esa etiqueta. |
| Ninguna de las constantes coincide con las constantes en las __`case`__ etiquetas; existe una __`default`__ etiqueta. | El control se transfiere a la __`default`__ etiqueta. |
| Ninguna de las constantes coincide con las constantes en las __`case`__ etiquetas; no __`default`__ existe ninguna etiqueta. | El control se transfiere a la instrucción después de la __`switch`__ instrucción. |

Si se encuentra una expresión coincidente, la ejecución puede continuar a través __`case`__ de las etiquetas posteriores o __`default`__ . La [`break`](../cpp/break-statement-cpp.md) instrucción se utiliza para detener la ejecución y transferir el control a la instrucción después de la __`switch`__ instrucción. Sin una __`break`__ instrucción, se ejecuta cada instrucción de la __`case`__ etiqueta coincidente hasta el final de __`switch`__ , incluido __`default`__ . Por ejemplo:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   const char *buffer = "Any character stream";
   int uppercase_A, lowercase_a, other;
   char c;
   uppercase_A = lowercase_a = other = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            uppercase_A++;
            break;
         case 'a':
            lowercase_a++;
            break;
         default:
            other++;
      }
   }
   printf_s( "\nUppercase A: %d\nLowercase a: %d\nTotal: %d\n",
      uppercase_A, lowercase_a, (uppercase_A + lowercase_a + other) );
}
```

En el ejemplo anterior, se incrementa `uppercase_A` si `c` es una `'A'` mayúscula. La __`break`__ instrucción después `uppercase_A++` de finaliza la ejecución del __`switch`__ cuerpo de la instrucción y el control pasa al __`while`__ bucle. Sin la __`break`__ instrucción, la ejecución pasaría a la siguiente instrucción etiquetada, por lo que `lowercase_a` `other` también se incrementaría. La instrucción de proporciona un propósito similar __`break`__ `case 'a'` . Si `c` es una minúscula `'a'` , `lowercase_a` se incrementa y la __`break`__ instrucción finaliza el cuerpo de la __`switch`__ instrucción. Si `c` no es `'a'` ni `'A'` , __`default`__ se ejecuta la instrucción.

**Visual Studio 2017 y versiones posteriores:** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)) el `[[fallthrough]]` atributo se especifica en el estándar c++ 17. Se puede utilizar en una __`switch`__ instrucción. Es una sugerencia para el compilador, o cualquier persona que lea el código, el comportamiento de paso a través es intencionado. El compilador de Microsoft C++ no advierte actualmente sobre el comportamiento de fallthrough, por lo que este atributo no tiene ningún efecto en el comportamiento del compilador. En el ejemplo, el atributo se aplica a una instrucción vacía dentro de la instrucción etiquetada sin terminar. Es decir, es necesario el punto y coma.

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)). Una __`switch`__ instrucción puede tener una *`init-statement`* cláusula, que finaliza con un punto y coma. Introduce e inicializa una variable cuyo ámbito se limita al bloque de la __`switch`__ instrucción:

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

Un bloque interno de una __`switch`__ instrucción puede contener definiciones con inicializadores siempre que sean *accesibles*, es decir, no omitir todas las rutas de acceso de ejecución posibles. Los nombres proporcionados mediante estas declaraciones tienen ámbito local. Por ejemplo:

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

Una __`switch`__ instrucción puede estar anidada. Cuando está anidada, __`case`__ las __`default`__ etiquetas o se asocian con la instrucción más cercana __`switch`__ que las incluye.

### <a name="microsoft-specific-behavior"></a>Comportamiento específico de Microsoft

Microsoft C++ no limita el número de __`case`__ valores en una __`switch`__ instrucción. El número solo está limitado por la memoria disponible.

## <a name="see-also"></a>Vea también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
