---
title: Formato de cadena y de E/S (C++ moderno)
description: Opciones de e/s de cadena con formato disponibles C++en moderno.
ms.date: 05/30/2019
ms.topic: conceptual
ms.assetid: 3954e8de-a59b-4175-89c9-4ee842ab89ed
ms.openlocfilehash: facb0b62cc1e92ed09a9ba729d766e5db7404282
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/21/2019
ms.locfileid: "74308190"
---
# <a name="string-and-io-formatting-modern-c"></a>Formato de cadena y de E/S (C++ moderno)

C++[\<iostream >](../standard-library/iostream.md) clases, funciones y operadores admiten la e/s de cadena con formato. Por ejemplo, el código siguiente muestra cómo establecer `cout` para dar formato a un entero para que se genere en hexadecimal. En primer lugar, guarda el estado actual para restablecerlo después, porque una vez que el estado de formato se pasa a `cout`, permanece así hasta que se cambia. No solo se aplica a una línea de código.

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

Este enfoque tiene seguridad de tipos y es extensible, pero también es complejo y detallado.

## <a name="alternative-format-options"></a>Opciones de formato alternativas

Como alternativa, puede usar `Boost.Format` de las bibliotecas de Boost C++ , aunque no sea estándar. Puede descargar cualquier biblioteca de Boost desde el sitio web de [Boost](https://www.boost.org/) .

Algunas de las ventajas de `Boost.Format` son las siguientes:

- Safe: Safe-Type y produce una excepción para los errores, por ejemplo, la especificación de demasiados o demasiados elementos.

- Extensible: funciona para cualquier tipo que se pueda transmitir por secuencias.

- Práctico: POSIX estándar y cadenas de formato similares.

Aunque `Boost.Format` está basado en C++ [\<iostream >](../standard-library/iostream-programming.md) instalaciones, que son seguras y extensibles, no están optimizadas para el rendimiento. Cuando requiera la optimización del rendimiento, considere la posibilidad de usar [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) y [sprintf](../c-runtime-library/reference/sprintf-sprintf-l-swprintf-swprintf-l-swprintf-l.md), que son rápidas y fáciles de usar. Sin embargo, no son extensibles ni seguros frente a las vulnerabilidades. (Las versiones seguras existen, pero incurren en una ligera disminución del rendimiento. Para obtener más información, vea [printf_s, _printf_s_l, wprintf_s, _wprintf_s_l](../c-runtime-library/reference/printf-s-printf-s-l-wprintf-s-wprintf-s-l.md) y [sprintf_s, _sprintf_s_l, swprintf_s, _swprintf_s_l](../c-runtime-library/reference/sprintf-s-sprintf-s-l-swprintf-s-swprintf-s-l.md)).

En el código siguiente se muestran algunas de las características de formato de Boost.

```cpp
    string s = str( format("%2% %2% %1%\n") % "world" % "hello" );
    // s contains "hello hello world"

    for( auto i = 0; i < names.size(); ++i )
        cout << format("%1% %2% %|40t|%3%\n") % first[i] % last[i] % tel[i];
    // Georges Benjamin Clemenceau             +33 (0) 123 456 789
    // Jean de Lattre de Tassigny              +33 (0) 987 654 321
```

## <a name="see-also"></a>Vea también

[Bienvenido de nuevo aC++](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
[\<iostream>](../standard-library/iostream.md)<br/>
[\<limits>](../standard-library/limits.md)<br/>
[\<iomanip>](../standard-library/iomanip.md)
