---
title: "UnorderedMapView::UnorderedMapView (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::UnorderedMapView"
ms.assetid: 408aa6ca-dd8d-4946-a817-42a31d19f429
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::UnorderedMapView (Constructor)
Inicializa una nueva instancia de la clase UnorderedMapView.  
  
## Sintaxis  
  
```cpp  
  
UnorderedMapView();  
  
explicit UnorderedMapView(size_t n);  
  
UnorderedMapView(size_t n, const H& h);  
  
UnorderedMapView(size_t n, const H& h, const P& p);  
  
explicit UnorderedMapView(  
    const std::unordered_map<K, V, H, P>& m  
    );  
explicit UnorderedMapView(  
    std::unordered_map<K, V, H, P>&& m  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h  
    );  
  
template <typename InIt> UnorderedMapView(  
    InIt first,  
    InIt last,  
    size_t n,  
    const H& h,  
    const P& p  
    );  
  
UnorderedMapView(  
    std::initializer_list<std::pair<const K, V>> il  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h  
    );  
  
UnorderedMapView(  
    std::initializer_list< std::pair<const K, V>> il,  
    size_t n,  
    const H& h,  
    const P& p  
    );  
```  
  
#### Parámetros  
 n  
 Número de elementos para los que se preasigna espacio.  
  
 `InIt`  
 Typename del objeto UnorderedMapView.  
  
 `H`  
 Objeto de función que puede generar un valor hash para una clave. Se establece de forma predeterminada en [std::hash\<K\>](http://msdn.microsoft.com/es-es/54f67435-af9d-4217-a29d-fa4d2491a104) para los tipos que admiten `std::hash`.  
  
 `P`  
 Tipo que proporciona un objeto de función que puede comparar dos claves para determinar si son iguales. Se establece de forma predeterminada en [std::equal\_to\<K\>](../standard-library/equal-to-struct.md).  
  
 `m`  
 Referencia o [Lvalues y rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md) a un [std::unordered\_map](../standard-library/unordered-map-class.md) que se usa para inicializar el objeto UnorderedMapView.  
  
 `first`  
 Iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto UnorderedMapView.  
  
 `last`  
 Iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto UnorderedMapView.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::UnorderedMapView \(Clase\)](../cppcx/platform-collections-unorderedmapview-class.md)