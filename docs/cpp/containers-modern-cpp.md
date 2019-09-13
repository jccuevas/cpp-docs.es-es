---
title: Contenedores (C++ moderno)
ms.date: 01/18/2018
ms.topic: conceptual
ms.openlocfilehash: 37b540132fc9ddc03d5eaafd33c545b5db5e7935
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926260"
---
# <a name="containers-modern-c"></a>Contenedores (C++ moderno)

De forma predeterminada, utilice [Vector](../standard-library/vector-class.md) como contenedor secuencial preferido en C++. Esto es equivalente a `List<T>` en los lenguajes .net.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Utilice [map](../standard-library/map-class.md) (no `unordered_map`) como el contenedor asociativo predeterminado. Utilice [set](../standard-library/set-class.md), [Multimap](../standard-library/multimap-class.md)y [MultiSet](../standard-library/multiset-class.md) para los casos en los que se degeneran & múltiples.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Cuando la optimización del rendimiento es necesaria, considere utilizar:

- El tipo de [matriz](../standard-library/array-class-stl.md) cuando la incrustación es importante, por ejemplo, como un miembro de clase.

- Contenedores asociativos desordenados como [unordered_map](../standard-library/unordered-map-class.md). Estos tienen menor sobrecarga por elemento y búsqueda de tiempo constante, pero pueden ser más difíciles de usar de forma correcta y eficaz.

- `vector`Ordenado. Para más información, vea [Algoritmos](../cpp/algorithms-modern-cpp.md).

No utilice matrices de estilo C. En el caso de las API más antiguas que necesiten acceso directo a los datos `f(vec.data(), vec.size());` , use métodos de descriptor de acceso como en su lugar.

Para obtener más información acerca de los contenedores, vea [ C++ contenedores de la biblioteca estándar](../standard-library/stl-containers.md).

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++ (C++ moderno)](../cpp/welcome-back-to-cpp-modern-cpp.md)<br/>
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)<br/>
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
