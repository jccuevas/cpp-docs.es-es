---
title: "Contenedores (C++ moderno) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 6e10b758-e928-4827-9c3f-86cafe54bf5b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Contenedores (C++ moderno)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, utilice [vector](vector%20Class.md) como contenedor secuencial predeterminado en C++. Esto es el equivalente de List \< T> en otros idiomas.  
  
```cpp  
vector<string> v;  
v.push_back( "Geddy Lee" );  
  
```  
  
 Use [mapa](../standard-library/map-class.md) (no unordered_map) como contenedor asociativo predeterminado. Use [establecer](../standard-library/set-class.md), [multimap](../standard-library/multimap-class.md), [multiset](../standard-library/multiset-class.md) para casos degenerados y múltiples.  
  
```cpp  
map<string, string> phone_book;  
// ...  
phone_book["Alex Lifeson"] = "+1 (416) 555-1212";  
  
```  
  
 Cuando la optimización del rendimiento es necesaria, considere utilizar:  
  
1.  el tipo de matriz cuando la incrustación es importante (por ejemplo, como miembro de clase).  
  
2.  contenedores asociativos desordenados (unordered_map, etc.): menor sobrecarga por elemento (principal) y búsqueda de tiempo constante (potencialmente mayor, a veces menor). Es más difícil de utilizar de forma correcta y eficaz, debido a los inconvenientes y a la nitidez de los bordes.  
  
3.  vector ordenado. (Consulte: [Algoritmos](../cpp/algorithms-modern-cpp.md).)  
  
 No use matrices de C. (Para obtener las API más antiguas, utilice `f( vec.data(), vec.size() );`).  
  
 Para otro artículo acerca de los contenedores, consulte [contenedores STL](../standard-library/stl-containers.md).  
  
## <a name="container-sizes"></a>Tamaños de contenedor  
 En las tablas siguientes se muestran los tamaños del contenedor, en bytes, para las plataformas x86 y x64.  (Para estos fines, ARM de 32 bits equivale a x86).  En estas tablas se cubre el modo de lanzamiento porque el modo de depuración contiene la comprobación de la maquinaria, que utiliza espacio y tiempo.  Las columnas independientes son para [!INCLUDE[cpp_orcas_long](../cpp/includes/cpp_orcas_long_md.md)] SP1, donde `_SECURE_SCL` se estableció en 1 como valor predeterminado y para [!INCLUDE[cpp_orcas_long](../cpp/includes/cpp_orcas_long_md.md)] SP1 con `_SECURE_SCL` establecido manualmente en 0 para lograr la velocidad máxima.  Visual C++ en Visual Studio 2010, [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)] y [!INCLUDE[cpp_dev12_long](../build/reference/includes/cpp_dev12_long_md.md)] cambian `_SECURE_SCL` a 0 de forma predeterminada (ahora conocido como `_ITERATOR_DEBUG_LEVEL`).  
  
|Tamaños del contenedor x86 (bytes)|VC9 SP1|VC9 SP1<br /><br /> SCL=0|VC10|VC11|  
|-----------------------------------|-------------|------------------------|----------|----------|  
|vector \< int>|24|16|16|12|  
|array\<int, 5>|20|20|20|20|  
|deque \< int>|32|32|24|20|  
|forward_list \< int>|N/D|N/D|8|4|  
|lista \< int>|28|12|12|8|  
|priority_queue \< int>|28|20|20|16|  
|cola \< int>|32|32|24|20|  
|pila \< int>|32|32|24|20|  
|pair\<int, int>|8|8|8|8|  
|tuple\<int, int, int>|16|16|16|12|  
|map\<int, int>|32|12|16|8|  
|multimap\<int, int>|32|12|16|8|  
|establecer \< int>|32|12|16|8|  
|MULTISET \< int>|32|12|16|8|  
|hash_map\<int, int>|72|44|44|32|  
|hash_multimap\<int, int>|72|44|44|32|  
|hash_set \< int>|72|44|44|32|  
|hash_multiset \< int>|72|44|44|32|  
|unordered_map\<int, int>|72|44|44|32|  
|unordered_multimap\<int, int>|72|44|44|32|  
|unordered_set \< int>|72|44|44|32|  
ordered_multiset \< int>|72|44|44|32|  
|string|28|28|28|24|  
|wstring|28|28|28|24|  
  
|Tamaños del contenedor x64 (bytes)|VC9 SP1|VC9 SP1<br /><br /> SCL=0|VC10|VC11|  
|-----------------------------------|-------------|------------------------|----------|----------|  
|vector \< int>|48|32|32|24|  
|array\<int, 5>|20|20|20|20|  
|deque \< int>|64|64|48|40|  
|forward_list \< int>|N/D|N/D|16|8|  
|lista \< int>|56|24|24|16|  
|priority_queue \< int>|56|40|40|32|  
|cola \< int>|64|64|48|40|  
|pila \< int>|64|64|48|40|  
|pair\<int, int>|8|8|8|8|  
|tuple\<int, int, int>|16|16|16|12|  
|map\<int, int>|64|24|32|16|  
|multimap\<int, int>|64|24|32|16|  
|establecer \< int>|64|24|32|16|  
|MULTISET \< int>|64|24|32|16|  
|hash_map\<int, int>|144|88|88|64|  
|hash_multimap\<int, int>|144|88|88|64|  
|hash_set \< int>|144|88|88|64|  
|hash_multiset \< int>|144|88|88|64|  
|unordered_map\<int, int>|144|88|88|64|  
|unordered_multimap\<int, int>|144|88|88|64|  
|unordered_set \< int>|144|88|88|64|  
ordered_multiset \< int>|144|88|88|64|  
|string|40|40|40|32|  
|wstring|40|40|40|32|  
  
## <a name="see-also"></a>Vea también  
 [Bienvenido nuevamente a C++](../cpp/welcome-back-to-cpp-modern-cpp.md)   
 [Referencia del lenguaje C++](../cpp/cpp-language-reference.md)   
 [Biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)