---
title: Contenedores (C++ moderno) | Documentos de Microsoft
ms.custom: 
ms.date: 1/18/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d43570f644e9627de5a40fc5b824a17e4fd33ffc
ms.sourcegitcommit: 6f40bba1772a09ff0e3843d5f70b553e1a15ab50
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/22/2018
---
# <a name="containers-modern-c"></a>Contenedores (C++ moderno)

De forma predeterminada, use [vector](../standard-library/vector-class.md) como el contenedor preferido secuencial en C++. Esto es equivalente a `List<T>` en lenguajes de. NET.

```cpp
vector<string> apples;
apples.push_back("Granny Smith");
```

Use [mapa](../standard-library/map-class.md) (no `unordered_map`) como el contenedor asociativo predeterminado. Use [establecer](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), y [multiset](../standard-library/multiset-class.md) para casos degenerados y múltiples.

```cpp
map<string, string> apple_color;
// ...
apple_color["Granny Smith"] = "Green";
```

Cuando la optimización del rendimiento es necesaria, considere utilizar:

- El [matriz](../standard-library/array-class-stl.md) escriba cuando la incrustación es importante, por ejemplo, como un miembro de clase.

- Contenedores asociativos desordenados como [unordered_map](../standard-library/unordered-map-class.md). Estos tienen sobrecarga por elemento inferior y búsqueda de tiempo constante, pero puede ser más difíciles de usar de manera correcta y eficaz.

- Ordenar **vector**. Para más información, vea [Algoritmos](../cpp/algorithms-modern-cpp.md).

No use matrices de estilo C. Para obtener información sobre las API más antiguas que necesitan acceso directo a los datos, use métodos de descriptor de acceso como `f(vec.data(), vec.size());` en su lugar.

Para obtener más información acerca de los contenedores, vea [contenedores de biblioteca estándar de C++](../standard-library/stl-containers.md).

## <a name="see-also"></a>Vea también

[Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)  
[Referencia del lenguaje C++](../cpp/cpp-language-reference.md)  
[Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)  
