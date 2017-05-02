---
title: "MapView::MapView (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::MapView"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::MapView (Constructor)"
ms.assetid: 67a3250c-b527-47ac-a103-0fd186046d71
caps.latest.revision: 4
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::MapView (Constructor)
Inicializa una nueva instancia de la clase MapView.  
  
## Sintaxis  
  
```  
explicit MapView(  
    const C& comp = C()  
    );  
  
explicit MapView(  
    const ::std::map<K, V, C>& m  
    );  
  
explicit MapView(  
    std::map<K, V, C>&& m  
    );  
  
template <typename InIt> MapView(  
    InIt first,  
    InIt last,  
    const C& comp = C()  
    );  
  
MapView(::std::initializer_list<  
    std::pair<const K, V>> il,  
    const C& comp = C()  
    );  
```  
  
#### Parámetros  
 `InIt`  
 El typename del objeto MapView actual.  
  
 `comp`  
 Objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto MapView.  
  
 `m`  
 Una referencia o [Lvalues y rvalues](~/cpp/lvalues-and-rvalues-visual-cpp.md) a un objeto [map \(Clase\)](../standard-library/map-class.md) que se usa para inicializar el objeto MapView actual.  
  
 `first`  
 El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto MapView actual.  
  
 `last`  
 El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto MapView actual.  
  
 il  
 [std::initializer\_list\<std::pair\<K,V\>\>](../standard-library/initializer-list-class.md) cuyos elementos se van a insertar en el objeto MapView.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::MapView \(Clase\)](../cppcx/platform-collections-mapview-class.md)