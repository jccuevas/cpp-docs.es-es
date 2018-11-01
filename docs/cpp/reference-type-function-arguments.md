---
title: Argumentos de función de tipo de referencia
ms.date: 08/27/2018
helpviewer_keywords:
- arguments [C++], function
- functions [C++], paramters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
ms.openlocfilehash: cc5a65e9a6bd74e79856057cf7e7fea220c62d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536214"
---
# <a name="reference-type-function-arguments"></a>Argumentos de función de tipo de referencia

Suele ser más eficaz pasar referencias, en lugar de objetos grandes, a las funciones. De este modo, el compilador puede pasar la dirección del objeto mientras mantiene la sintaxis que se habría utilizado para tener acceso al objeto. Considere el ejemplo siguiente, en el que se usa la estructura `Date`:

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

El código anterior muestra que se accede a los miembros de una estructura pasada por referencia mediante el operador de selección de miembro (**.**) en lugar del operador de selección de miembro de puntero (**->**).

Aunque los argumentos pasados como tipos de referencia, observe la sintaxis de los tipos que no son de puntero, mantienen una característica importante de los tipos de puntero: son modificables a menos que se declara como **const**. Dado que el código anterior no tenía como intención modificar el objeto `date`, un prototipo de función más adecuado sería:

```cpp
long DateOfYear( const Date& date );
```

Este prototipo garantiza que la función `DateOfYear` no cambiará su argumento.

Cualquier función prototipo que toma un tipo de referencia puede aceptar un objeto del mismo tipo en su lugar, porque no hay una conversión estándar de *typename* a *typename* <strong>&</strong>.

## <a name="see-also"></a>Vea también

[Referencias](../cpp/references-cpp.md)<br/>
