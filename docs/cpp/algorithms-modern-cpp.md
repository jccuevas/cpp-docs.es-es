---
title: Algoritmos (C++ moderno)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
ms.openlocfilehash: b972e575c982ae2523ec560a6237eac76ceaf834
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220158"
---
# <a name="algorithms-modern-c"></a>Algoritmos (C++ moderno)

Para la programación de C++ moderno, se recomienda que use los algoritmos en el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md). Estos son algunos ejemplos importantes:

- **for_each**, que es el algoritmo predeterminado de recorrido. (También **transformar** para conocer la semántica no en el lugar.)

- **find_if**, que es el algoritmo de búsqueda predeterminado.

- **ordenación**, **lower_bound**y el predeterminado de los algoritmos de búsqueda y ordenación.

Para escribir un comparador, use strict **<** y usar *lambdas con nombre* cuando sea posible.

```cpp
auto comp = [](const widget& w1, const widget& w2)
     { return w1.weight() < w2.weight(); }

sort( v.begin(), v.end(), comp );

auto i = lower_bound( v.begin(), v.end(), comp );
```

## <a name="loops"></a>Bucles

Cuando sea posible, use basado en rango **para** bucles o llamadas de algoritmo o ambos, en lugar de bucles escritos a mano. **copia**, **transformar**, **count_if**, **remove_if**, y otros como ellos son mucho mejores que bucles manuscritos porque su intención es obvia y facilitan la escritura del código sin errores. Además, muchos algoritmos de biblioteca estándar de C++ tienen optimizaciones de implementación que hacen más eficaces.

En lugar del antiguo C++ así:

```cpp
for ( auto i = strings.begin(); i != strings.end(); ++i ) {
    /* ... */
}

auto i = v.begin();

for ( ; i != v.end(); ++i ) {
    if (*i > x && *i < y) break;
}
```

Utilice C++ moderno similar al siguiente:

```cpp
for_each( begin(strings), end(strings), [](string& s) {
  // ...
} );

auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );
```

### <a name="range-based-for-loops"></a>En función de rangos para bucles

Basado en intervalos **para** bucle es una característica del 11 lenguaje C ++, no un algoritmo de la biblioteca estándar de C++. Pero merece que se mencione en este debate acerca de los bucles. Basado en rango **para** bucles son una extensión de la **para** palabra clave y proporcionan una manera sencilla y eficaz para escribir bucles que iteran en un intervalo de valores. Están listos para usar contenedores de la biblioteca estándar de C++, cadenas y matrices en función de rangos **para** bucles. Para habilitar esta nueva sintaxis de iteración para el tipo definido por el usuario, agregue la siguiente compatibilidad:

- Un `begin` método que devuelve un iterador al principio de la estructura y un `end` método que devuelve un iterador al final de la estructura.

- Soporte técnico en el iterador con estos métodos: **operador**<strong>\*</strong>, **operador! =**, y **operator ++** (versión prefija).

Estos métodos pueden ser miembros o funciones independientes.

## <a name="random-numbers"></a>Números aleatorios

No es ningún secreto que CRT antiguo `rand()` función tiene muchos defectos, que se han explicado con detalle en la Comunidad de C++. En C++ moderno, no tiene que ocuparse de esas limitaciones — ni tiene que inventar su propio generador de números aleatorios distribuido uniformemente, dado que las herramientas para crearlos rápida y fácilmente están disponibles en la biblioteca estándar de C++, como se muestra en [ \<aleatorio >](../standard-library/random.md).

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++ (C++ moderno)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
