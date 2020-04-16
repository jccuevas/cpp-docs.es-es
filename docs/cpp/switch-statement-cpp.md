---
title: switch(C++)
description: Referencia a la instrucción Standard C++ switch en Microsoft Visual Studio C++.
ms.date: 04/15/2020
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
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 1f65d4699423d74be9c75a9be47e543a9a1256e2
ms.sourcegitcommit: 9266fc76ac2e872e35a208b4249660dfdfc87cba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2020
ms.locfileid: "81480819"
---
# <a name="opno-locswitch-statement-c"></a>switch(C++)

Permite la selección entre varias secciones de código, dependiendo del valor de una expresión entera.

## <a name="syntax"></a>Sintaxis

> **`switch (`**\[ *inicialización* **`;`** *]***`)`**\
> **`{`**\
> &nbsp;&nbsp;&nbsp;&nbsp;**`case`***constant-expression* **`:`** *declaración* de expresión constante\
> &nbsp;&nbsp;&nbsp;&nbsp;\[**`default :`***declaración*] \
> **`}`**

## <a name="remarks"></a>Observaciones

La *expresión* debe tener un tipo entero o ser un tipo de clase que tenga una conversión inequívoca a tipo entero. La promoción integral tiene lugar como se describe en [Conversiones estándar](standard-conversions.md).

El **switch** cuerpo de la **case** instrucción consta **default** de una serie de etiquetas y una etiqueta opcional. Colectivamente, las instrucciones que siguen a las etiquetas se denominan instrucciones *etiquetadas.* Las instrucciones etiquetadas no son requisitos sintácticos, pero la **switch** instrucción no tiene sentido sin ellas. No hay dos **case** expresiones constantes en instrucciones que pueden evaluarse con el mismo valor. La **default** etiqueta puede aparecer una sola vez. La **default** instrucción se coloca a menudo al final, pero **switch** puede aparecer en cualquier parte del cuerpo de la instrucción. Una **case** **default** o etiqueta solo **switch** puede aparecer dentro de una instrucción.

La *expresión constante* **case** de cada etiqueta se convierte al tipo de *expresión*. Luego, se compara con la *expresión* para la igualdad. Control pasa a la **case** instrucción cuya *expresión constante* coincide con el valor de *expression*. El comportamiento resultante se muestra en la siguiente tabla.

### <a name="switch-statement-behavior"></a>Cambiar el comportamiento de la declaración

| Condición | Acción |
|--|--|
| El valor convertido coincide con el de la expresión de control promovida. | El control se transfiere a la instrucción que sigue a esa etiqueta. |
| Ninguna de las constantes coincide **case** con las constantes de las etiquetas; una **default** etiqueta está presente. | El control se **default** transfiere a la etiqueta. |
| Ninguna de las constantes coincide **case** con las constantes de las etiquetas; no **default** hay ninguna etiqueta presente. | El control se transfiere **switch** a la instrucción después de la instrucción. |

Si se encuentra una expresión coincidente, **case** **default** la ejecución puede continuar más adelante o etiquetas. La [`break`](../cpp/break-statement-cpp.md) instrucción se utiliza para detener la **switch** ejecución y transferir el control a la instrucción después de la instrucción. Sin **break** una instrucción, se **case** ejecuta cada instrucción desde la etiqueta coincidente hasta el final del **switch** archivo , incluido el **default** archivo , . Por ejemplo:

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

En el ejemplo anterior, se incrementa `uppercase_A` si `c` es una `'A'` mayúscula. La **break** instrucción después `uppercase_A++` **switch** de termina la ejecución **while** del cuerpo de la instrucción y el control pasa al bucle. Sin **break** la instrucción, la ejecución "pasaría" a `lowercase_a` la `other` siguiente instrucción etiquetada, de modo que y también se incrementaría. Un propósito similar es **break** servido `case 'a'`por la declaración para . Si `c` es un `'a'` `lowercase_a` en minúsculas **break** , se **switch** incrementa y la instrucción termina el cuerpo de la instrucción. Si `c` no es `'a'` `'A'`un **default** or , se ejecuta la instrucción.

**Visual Studio 2017 y versiones posteriores:** (disponible con [/std:c++17](../build/reference/std-specify-language-standard-version.md)) El `[[fallthrough]]` atributo se especifica en el estándar C++17. Puede usarlo en **switch** una instrucción. Es una sugerencia para el compilador, o cualquiera que lea el código, que el comportamiento de caída es intencional. El compilador de Microsoft C++ actualmente no advierte sobre el comportamiento de caída, por lo que este atributo no tiene ningún efecto en el comportamiento del compilador. En el ejemplo, el atributo se aplica a una instrucción vacía dentro de la instrucción etiquetada sin terminar. En otras palabras, el punto y coma es necesario.

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

**Visual Studio 2017 versión 15.3 y versiones posteriores** (disponible con [/std:c++17](../build/reference/std-specify-language-standard-version.md)). Una switch instrucción puede tener una cláusula *de inicialización.* Presenta e inicializa una variable cuyo ámbito está limitado switch al bloque de la instrucción:

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

Un bloque interno **switch** de una instrucción puede contener definiciones con inicializaciones siempre que sean *accesibles,* es decir, no se omitan por todas las rutas de ejecución posibles. Los nombres proporcionados mediante estas declaraciones tienen ámbito local. Por ejemplo:

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

Se **switch** puede anidar una instrucción. Cuando se **case** anidan, las etiquetas **default** **switch** o se asocian a la instrucción más cercana que las encierra.

### <a name="microsoft-specific-behavior"></a>Comportamiento específico de Microsoft

Microsoft C no limita el **case** número **switch** de valores de una instrucción. El número solo está limitado por la memoria disponible. ANSI C requiere que se **case** permitan al **switch** menos 257 etiquetas en una declaración.

El default para Microsoft C es que las extensiones de Microsoft están habilitadas. Utilice la opción del compilador [/Za](../build/reference/za-ze-disable-language-extensions.md) para deshabilitar estas extensiones.

## <a name="see-also"></a>Consulte también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
