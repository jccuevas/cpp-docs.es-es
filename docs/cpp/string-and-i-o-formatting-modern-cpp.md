---
title: Formato de cadena y E/s (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: 816eb71dae011f853a6e7ade1a1a2a8144a457c5
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/09/2018
ms.locfileid: "51326191"
---
# <a name="string-and-io-formatting-modern-c"></a>Formato de cadena y de E/S (C++ moderno)

C++ [iostreams](../standard-library/iostream.md) son capaces de cadena con formato E/S. Por ejemplo, el código siguiente muestra cómo establecer cout para dar formato a un número entero y de salida en formato hexadecimal, en primer lugar, guardando fuera del estado actual y estableciéndolo de nuevo más adelante, porque una vez que el formato de estado se pasa a cout, permanece así hasta que cambie, no solo para la línea de código.

```cpp
#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    ios state(nullptr);

    cout << "The answer in decimal is: " << 42 << endl;

    state.copyfmt(cout); // save current formatting
    cout << "In hex: 0x" // now load up a bunch of formatting modifiers
        << hex
        << uppercase
        << setw(8)
        << setfill('0')
        << 42            // the actual value we wanted to print out
        << endl;
    cout.copyfmt(state); // restore previous formatting
}
```

Esto puede ser demasiado complejo en muchos casos. Como alternativa, puede utilizar Boost.Format de las bibliotecas de Boost de C++, aunque no es estándar. Puede descargar cualquier biblioteca de Boost desde el [Boost](http://www.boost.org/) sitio Web.

Algunas ventajas de Boost.Format son:

- Seguro: Seguro y produce una excepción para errores, por ejemplo, la especificación de muy pocos o demasiados elementos.

- Extensible: Funciona para cualquier tipo que se puede transmitir.

- Adecuado: Posix estándar y cadenas de formato similares.

Aunque Boost.Format está compilado en C++ [iostreams](../standard-library/iostream-programming.md), que son seguros y extensible, no optimizado para el rendimiento. Cuando necesite la optimización del rendimiento, considere la posibilidad de C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) y [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), que son rápidos y fáciles de usar. Sin embargo, no son extensibles ni están seguros frente a vulnerabilidades. (Las versiones seguras existen, pero incurren en una ligera disminución del rendimiento. Para obtener más información, consulte [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) y [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

El código siguiente muestra algunas de la mejora de las características de formato.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)