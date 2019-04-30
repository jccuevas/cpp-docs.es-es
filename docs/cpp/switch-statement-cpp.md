---
title: switch (Instrucción) (C++)
ms.date: 11/04/2016
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 67918b7df747d3bee923da500729e60b4fe04336
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62267094"
---
# <a name="switch-statement-c"></a>switch (Instrucción) (C++)

Permite la selección entre varias secciones de código, dependiendo del valor de una expresión entera.

## <a name="syntax"></a>Sintaxis

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Comentarios

El *expresión* debe ser de tipo entero o de un tipo de clase para el que hay una conversión no ambigua a un tipo entero. Promoción de entero se realiza como se describe en [conversiones estándar](standard-conversions.md).

El **cambiar** cuerpo de instrucción consiste en una serie de **caso** etiquetas y opcional **predeterminada** etiqueta. No hay dos expresiones constantes en **caso** instrucciones pueden evaluar en el mismo valor. El **predeterminada** etiqueta puede aparecer solo una vez. Las instrucciones con etiquetas no son requisitos sintácticos, pero la **cambiar** instrucción tiene sentida sin ellas.   La instrucción predeterminada no necesita estar al final; puede aparecer en cualquier parte del cuerpo de la instrucción switch. Una etiqueta case o default solo puede aparecer en una instrucción switch.

El *expresión-constante* en cada **caso** etiqueta se convierte al tipo de *expresión* y se compara con *expresión* para igualdad. Control pasa a la instrucción cuya **caso** *expresión-constante* coincide con el valor de *expresión*. El comportamiento resultante se muestra en la siguiente tabla.

### <a name="switch-statement-behavior"></a>Comportamiento de la instrucción switch

|Condición|Acción|
|---------------|------------|
|El valor convertido coincide con el de la expresión de control promovida.|El control se transfiere a la instrucción que sigue a esa etiqueta.|
|Ninguna de las constantes coincide con las constantes en el **caso** etiquetas; una **predeterminada** etiqueta está presente.|El control se transfiere a la **predeterminada** etiqueta.|
|Ninguna de las constantes coincide con las constantes en el **caso** etiquetas; **predeterminada** etiqueta no está presente.|El control se transfiere a la instrucción después de la **cambiar** instrucción.|

Si se encuentra una expresión coincidente, control no se interrumpa por posteriores **caso** o **predeterminada** etiquetas. El [salto](../cpp/break-statement-cpp.md) instrucción se utiliza para detener la ejecución y transferir el control a la instrucción después de la **cambiar** instrucción. Sin un **salto** instrucción, todas las instrucciones de la coincidente **caso** etiqueta al final de la **cambiar**, incluido el **predeterminada**, es ejecuta. Por ejemplo:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

En el ejemplo anterior, se incrementa `capa` si `c` es una `A` mayúscula. El **salto** instrucción después `capa++` finaliza la ejecución de la **cambiar** cuerpo de instrucción y el control pasa a la **mientras** bucle. Sin el **salto** instrucción, ejecución sería "pasen" a la siguiente instrucción con etiqueta, por lo que `lettera` y `nota` también se incrementarían. Se sirve un propósito similar por la **salto** instrucción para `case 'a'`. Si `c` es minúscula `a`, `lettera` se incrementa y el **salto** instrucción termina el **cambiar** cuerpo de instrucción. Si `c` no es un `a` o `A`, **predeterminada** se ejecuta la instrucción.

**Visual Studio 2017 y versiones posterior:** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)) el `[[fallthrough]]` atributo se especifica en el estándar C ++ 17. Se puede usar en un **cambiar** instrucción como una sugerencia al compilador (o a cualquiera que lea el código) está pensado ese comportamiento. Actualmente el compilador de Visual C++ no advierte sobre el comportamiento de fallthrough, por lo que este atributo no tiene ningún efecto en el comportamiento del compilador. Tenga en cuenta que el atributo se aplica a una instrucción vacía en la instrucción con etiqueta; en otras palabras, el punto y coma es necesario.

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

**Visual Studio 2017 versión 15.3 y versiones posterior** (disponible con [/std: c ++ 17](../build/reference/std-specify-language-standard-version.md)):  Una instrucción switch puede introducir e inicializar una variable cuyo ámbito está limitado al bloque de la instrucción switch:

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

Un bloque interno de un **cambiar** instrucción puede contener definiciones con inicializaciones siempre son accesibles, es decir, no las omitan todas las rutas de ejecución posibles. Los nombres proporcionados mediante estas declaraciones tienen ámbito local. Por ejemplo:

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

Un **cambiar** se puede anidar la instrucción. En tales casos, **caso** o **predeterminada** asociación etiquetas con la más cercana **cambiar** instrucción que contenga.

**Específicos de Microsoft**

Microsoft C no limita el número de valores case en una **cambiar** instrucción. El número solo está limitado por la memoria disponible. ANSI C requiere al menos 257 etiquetas case se permitan en una **cambiar** instrucción.

El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas. Use la [/Za](../build/reference/za-ze-disable-language-extensions.md) opción del compilador para deshabilitar estas extensiones.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)