---
title: Formato de cadena y de E/S (C++ moderno)
description: Opciones para E/S de cadena con formato disponibles en C+++ moderno.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: a3fc93b0baf414759eb50c787c4057fb85dcb370
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375770"
---
# <a name="string-and-io-formatting-modern-c"></a>Formato de cadena y de E/S (C++ moderno)

C++ [ \<iostream>](../standard-library/iostream.md) clases, funciones y operadores admiten E/S de cadena con formato. Por ejemplo, el código siguiente `cout` muestra cómo establecer un formato de un entero para que la salida sea hexadecimal. En primer lugar, guarda el estado actual para restablecerlo después, porque una vez que el estado de formato se pasa a `cout`, se mantiene de esa manera hasta que se cambia. No solo se aplica a la única línea de código.

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

Este enfoque es seguro para tipos y extensible, pero también es complejo y detallado.

## <a name="alternative-format-options"></a>Opciones de formato alternativo

Como alternativa, puedes `Boost.Format` usarlas en las bibliotecas Boost C++, aunque no sea estándar. Puedes descargar cualquier biblioteca de Boost desde el sitio web de [Boost.](https://www.boost.org/)

Algunas ventajas de `Boost.Format` son:

- Seguro: tipo seguro y produce una excepción para errores, por ejemplo, la especificación de demasiados o demasiados elementos.

- Extensible: funciona para cualquier tipo que se pueda transmitir.

- Conveniente: POSIX estándar y cadenas de formato similares.

Aunque `Boost.Format` se basa en las instalaciones de>De C++ [ \<iostream,](../standard-library/iostream-programming.md) que son seguras y extensibles, no están optimizadas para el rendimiento. Cuando necesite una optimización del rendimiento, tenga en cuenta C [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) y [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), que son rápidos y fáciles de usar. Sin embargo, no son extensibles ni seguras de vulnerabilidades. (Existen versiones seguras, pero incurren en una ligera penalización del rendimiento. Para obtener más información, vea [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) y [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

El código siguiente muestra algunas de las características de formato Boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Consulte también

[Bienvenido de nuevo a C++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del idioma C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<>iostream](../standard-library/iostream.md)<br/>
[\<límites>](../standard-library/limits.md)<br/>
[\<>iomanip](../standard-library/iomanip.md)
