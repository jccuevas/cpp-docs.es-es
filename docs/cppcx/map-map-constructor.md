---
title: "Map::Map (Constructor) | Microsoft Docs"
ms.custom: ""
ms.date: "01/24/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::Map::Map"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Map::Map (Constructor)"
ms.assetid: 4cd314eb-e3e3-4fa7-8c58-96e48d167246
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# Map::Map (Constructor)
Inicializa una nueva instancia de la clase Map.  
  
## Sintaxis  
  
```  
explicit Map(  
   const C& comp = C()  
);  
explicit Map(  
   const StdMap& m  
);  
explicit Map(  
   StdMap&& m  
);  
template <  
   typename InIt  
>  
Map(  
   InItfirst,  
   InItlast,  
   const C& comp = C()  
);  
```  
  
#### Parámetros  
 `InIt`  
 typename del objeto Map actual.  
  
 `comp`  
 Tipo que proporciona un objeto de función que puede comparar dos valores de elemento como claves de ordenación para determinar su orden relativo en el objeto Map.  
  
 `m`  
 Una referencia o [Lvalues y rvalues](../Topic/Lvalues%20and%20Rvalues%20\(Visual%20C++\).md) a un objeto [map \(Clase\)](../standard-library/map-class.md) que se usa para inicializar el objeto Map actual.  
  
 `first`  
 El iterador de entrada del primer elemento en un intervalo de elementos utilizados para inicializar el objeto Map actual.  
  
 `last`  
 El iterador de entrada del primer elemento tras un intervalo de elementos utilizados para inicializar el objeto Map actual.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::Map \(Clase\)](../cppcx/platform-collections-map-class.md)