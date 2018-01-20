---
title: Contenedores (C++ moderno) | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4fc8bbc3a983e6fa50e4ae5e8590e1f1de37f02f
ms.sourcegitcommit: ff9bf140b6874bc08718674c07312ecb5f996463
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/19/2018
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
  
1.  El [matriz](../standard-library/array-class-stl.md) escriba cuando la incrustación es importante, por ejemplo, como un miembro de clase.  
  
2.  Contenedores asociativos desordenados como [unordered_map](../standard-library/unordered-map-class.md). Estos tienen sobrecarga por elemento inferior y búsqueda de tiempo constante, pero puede ser más difíciles de usar de manera correcta y eficaz.  
  
3.  Ordenar `vector`. Para más información, vea [Algoritmos](../cpp/algorithms-modern-cpp.md).  
  
No use matrices de estilo C. Para obtener información sobre las API más antiguas que necesitan acceso directo a los datos, use métodos de descriptor de acceso como `f(vec.data(), vec.size());` en su lugar.  
  
Para obtener más información acerca de los contenedores, vea [contenedores de biblioteca estándar de C++](../standard-library/stl-containers.md).  
  
## <a name="see-also"></a>Vea también  
 [Aquí está otra vez C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)
