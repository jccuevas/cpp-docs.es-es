---
title: switch (Instrucción) (C++)
ms.date: 05/06/2019
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 6b09c0eac939f7ca6a12b68ce5deb3fb83ad27c6
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160819"
---
# <a name="switch-statement-c"></a>switch (Instrucción) (C++)

Permite la selección entre varias secciones de código, dependiendo del valor de una expresión entera.

## <a name="syntax"></a>Sintaxis

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Observaciones

La *expresión* debe ser de un tipo entero o de un tipo de clase para el que haya una conversión no ambigua a un tipo entero. La promoción de entero se realiza como se describe en [conversiones estándar](standard-conversions.md).

El cuerpo de la instrucción **Switch** se compone de una serie de etiquetas **Case** y una etiqueta **default** opcional. Dos expresiones constantes en las instrucciones **Case** no pueden evaluarse en el mismo valor. La etiqueta **predeterminada** solo puede aparecer una vez. Las instrucciones etiquetadas no son requisitos sintácticos, pero la instrucción **Switch** no tiene sentido sin ellas.   La instrucción predeterminada no necesita estar al final; puede aparecer en cualquier parte del cuerpo de la instrucción switch. Una etiqueta case o default solo puede aparecer en una instrucción switch.

*Constant-Expression* en cada etiqueta **de caso** se convierte al tipo de *Expression* y se compara con la *expresión* para determinar si son iguales. El control pasa a la instrucción cuya *expresión constante* **Case** coincide con el valor de *Expression*. El comportamiento resultante se muestra en la siguiente tabla.

### <a name="switch-statement-behavior"></a>Comportamiento de la instrucción switch

|Condición|Acción|
|---------------|------------|
|El valor convertido coincide con el de la expresión de control promovida.|El control se transfiere a la instrucción que sigue a esa etiqueta.|
|Ninguna de las constantes coincide con las constantes en las etiquetas **Case** ; existe una etiqueta **predeterminada** .|El control se transfiere a la etiqueta **predeterminada** .|
|Ninguna de las constantes coincide con las constantes en las etiquetas **Case** ; la etiqueta **predeterminada** no está presente.|El control se transfiere a la instrucción después de la instrucción **Switch** .|

Si se encuentra una expresión coincidente, el control no se obstaculiza en las siguientes etiquetas **Case** o **default** . La instrucción [break](../cpp/break-statement-cpp.md) se utiliza para detener la ejecución y transferir el control a la instrucción después de la instrucción **Switch** . Sin una instrucción **break** , se ejecuta cada instrucción de la etiqueta **Case** coincidente al final del **modificador**, incluido el **valor predeterminado**. Por ejemplo:

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

En el ejemplo anterior, se incrementa `capa` si `c` es una `A` mayúscula. La instrucción **break** después de `capa++` finaliza la ejecución del cuerpo de la instrucción **Switch** y el control pasa al bucle **While** . Sin la instrucción **break** , la ejecución pasaría a la siguiente instrucción etiquetada, de modo que también se incrementaría `lettera` y `nota`. Una finalidad similar se sirve de la instrucción **break** para `case 'a'`. Si `c` es una `a`en minúsculas, se incrementa `lettera` y la instrucción **break** finaliza el cuerpo de la instrucción **Switch** . Si `c` no es un `a` o `A`, se ejecuta la instrucción **predeterminada** .

**Visual Studio 2017 y versiones posteriores:** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)) el atributo `[[fallthrough]]` se especifica en el estándar c++ 17. Se puede usar en una instrucción **Switch** como una sugerencia para el compilador (o para cualquier persona que lea el código) que está previsto el comportamiento de paso a través. Actualmente, C++ el compilador de Microsoft no advierte del comportamiento de fallthrough, por lo que este atributo no tiene ningún efecto en el comportamiento del compilador. Tenga en cuenta que el atributo se aplica a una instrucción vacía dentro de la instrucción etiquetada; en otras palabras, es necesario el punto y coma.

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

**Visual Studio 2017 versión 15,3 y posterior** (disponible con [/STD: c++ 17](../build/reference/std-specify-language-standard-version.md)): una instrucción switch puede introducir e inicializar una variable cuyo ámbito está limitado al bloque de la instrucción switch:

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

Un bloque interno de una instrucción **Switch** puede contener definiciones con inicializaciones siempre y cuando se pueda tener acceso a ellas, es decir, no se omiten en todas las rutas de acceso de ejecución posibles. Los nombres proporcionados mediante estas declaraciones tienen ámbito local. Por ejemplo:

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

Una instrucción **Switch** puede estar anidada. En tales casos, las etiquetas **Case** o **default** se asocian con la instrucción **Switch** más cercana que las incluye.

**Específicos de Microsoft**

Microsoft C no limita el número de valores Case en una instrucción **Switch** . El número solo está limitado por la memoria disponible. ANSI C requiere que se permitan, al menos, 257 etiquetas Case en una instrucción **Switch** .

El valor predeterminado para Microsoft C es que las extensiones de Microsoft estén habilitadas. Use la opción del compilador [/za](../build/reference/za-ze-disable-language-extensions.md) para deshabilitar estas extensiones.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Instrucciones de selección](../cpp/selection-statements-cpp.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
