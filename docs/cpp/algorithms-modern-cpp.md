---
title: Algoritmos (C++ moderno) | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6f758d3c-a7c7-4a50-92bb-97b2f6d4ab27
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fdd5742bb86992ce20f5a52f587c8557d46a97eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32412301"
---
# <a name="algorithms-modern-c"></a>Algoritmos (C++ moderno)
Para la programación de C++ moderno, recomendamos que use los algoritmos en el [biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md). Estos son algunos ejemplos importantes:  
  
-   `for_each`, que es el algoritmo de cruce seguro de forma predeterminada. (También `transform` para semántica no in situ.)  
  
-   `find_if`, que es el algoritmo de búsqueda predeterminado.  
  
-   `sort`, `lower_bound`y el predeterminado de algoritmos de búsqueda y ordenación.  
  
 Para escribir un comparador, utilice estricta `<` y usar *denominado lambdas* siempre que se pueda.  
  
```cpp  
auto comp = [](const widget& w1, const widget& w2)  
      { return w1.weight() < w2.weight(); }  
  
sort( v.begin(), v.end(), comp );  
  
auto i = lower_bound( v.begin(), v.end(), comp );  
```  
  
## <a name="loops"></a>Bucles  
 Cuando sea posible, utilice basada en intervalo `for` bucles o llamadas de algoritmo o ambas, en lugar de bucles escrita a mano.`copy`, `transform`, `count_if`, `remove_if`, y otros como ellos son mucho mejores que los bucles escritas a mano porque su intención es obvio y resulten más fácil escribir código sin errores. Además, muchos algoritmos de la biblioteca estándar de C++ tienen las optimizaciones de implementación que las hacen más eficaz.  
  
 En lugar de C++ antiguo como el siguiente:  
  
```cpp  
for ( auto i = strings.begin(); i != strings.end(); ++i ) {  
   /* ... */  
}  
  
auto i = v.begin();  
  
for ( ; i != v.end(); ++i ) {  
  if (*i > x && *i < y) break;  
}  
```  
  
 Use C++ moderno similar al siguiente:  
  
```cpp  
for_each( begin(strings), end(strings), [](string& s) {  
   // ...  
} );  
  
auto i = find_if( begin(v), end(v),  [=](int i) { return i > x && i < y; } );  
```  
  
### <a name="range-based-for-loops"></a>Basado en intervalo for (bucles)  
 Basado en el intervalo `for` bucle es una característica del 11 lenguaje C ++, no un algoritmo de la biblioteca estándar de C++. Pero merece mención en esta documentación acerca de los bucles. Basado en intervalo `for` bucles son una extensión de la `for` (palabra clave) y proporcionan una manera sencilla y eficaz para escribir bucles que iterar sobre un intervalo de valores. Contenedores de la biblioteca estándar de C++, cadenas y matrices están listos para su uso para basada en intervalo `for` bucles. Para habilitar esta nueva sintaxis de iteración para el tipo definido por el usuario, agregue la siguiente compatibilidad:  
  
-   A `begin` método que devuelve un iterador al principio de la estructura y un `end` método que devuelve un iterador al final de la estructura.  
  
-   Soporte técnico en el iterador de estos métodos: `operator*`, `operator!=`, y `operator++` (versión prefija).  
  
 Estos métodos pueden ser miembros o funciones independientes.  
  
## <a name="random-numbers"></a>Números aleatorios  
 No es ningún secreto que CRT antiguo `rand()` función tiene muchos errores, que se han explicado ampliamente en la Comunidad de C++. En C++ moderno, no tiene que tratar con los inconvenientes, ni es necesario inventar su propio generador de números aleatorios distribuido uniformemente, porque las herramientas de forma rápida y sencilla crearlos están disponibles en la biblioteca estándar de C++, como se muestra en [ \<aleatorio >](../standard-library/random.md).  
  
## <a name="see-also"></a>Vea también  
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)