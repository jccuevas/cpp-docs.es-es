---
title: "UnorderedMap::UnorderedMap (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMap::UnorderedMap"
ms.assetid: bd62e663-7f3a-43ef-ad6d-8266128c778b
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMap::UnorderedMap (Constructor)
Inicializa una nueva instancia de la clase UnorderedMap.  
  
## Sintaxis  
  
```scr  
UnorderedMap();  
  
  explicit UnorderedMap(  
      size_t n  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  explicit UnorderedMap(  
      const std::unordered_map<K, V, H, P>& m  
      );  
  
  explicit UnorderedMap(  
      std::unordered_map<K, V, H, P>&& m  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h  
      );  
  
  template <typename InIt> UnorderedMap(  
      InIt first,  
      InIt last,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
  
  UnorderedMap(std::initializer_list<  
      std::pair<const K, V>> il  
      );  
  
  UnorderedMap(::std::initializer_list<  
      std::pair<const K, V>> il,  
      size_t n  
      );  
  
  UnorderedMap(  
      ::std::initializer_list< ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h  
      );  
  
  UnorderedMap(::std::initializer_list<  
      ::std::pair<const K, V>> il,  
      size_t n,  
      const H& h,  
      const P& p  
      );  
```  
  
#### Parámetros  
 `InIt`  
 El typename del objeto UnorderedMap actual.  
  
 `P`  
 Un objeto de función que puede comparar dos claves para determinar si son iguales. El valor predeterminado de este parámetro es [std::equal\_to\<K\>](../standard-library/equal-to-struct.md).  
  
 `H`  
 Un objeto de función que genera un valor hash para una clave. El valor predeterminado de este parámetro es [hash \(Clase\)](../Topic/hash%20Class%201.md) para los tipos de clave que admite esa clase.  
  
 `m`  
 Referencia o [Lvalues y rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md) a un [std::unordered\_map](../standard-library/unordered-map-class.md) que se usa para inicializar el objeto UnorderedMap actual.  
  
 il  
 [std::initializer\_list](../standard-library/initializer-list-class.md) de los objetos [std::pair](../standard-library/pair-structure.md) que se va a usar para inicializar el mapa.  
  
 `first`  
 El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.  
  
 `last`  
 El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto UnorderedMap actual.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections \(Espacio de nombres\)](../cppcx/platform-collections-namespace.md)   
 [Colecciones](../cppcx/collections-c-cx.md)