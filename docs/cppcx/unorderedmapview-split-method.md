---
title: "UnorderedMapView::Split (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::UnorderedMapView::Split"
ms.assetid: b759d254-40c9-40f1-9838-106ffb2c5626
caps.latest.revision: 3
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# UnorderedMapView::Split (M&#233;todo)
Divide el objeto UnorderedMapView actual en dos objetos UnorderedMapView. Este método no es operativo.  
  
## Sintaxis  
  
```cpp  
void Split(  
   Windows::Foundation::Collections::IMapView<  
                         K,  
                         V>^ * firstPartition,  
   Windows::Foundation::Collections::IMapView<  
                         K,  
                         V>^ * secondPartition  
);  
```  
  
#### Parámetros  
 `firstPartition`  
 La primera parte del objeto UnorderedMapView original.  
  
 `secondPartition`  
 La segunda parte del objeto UnorderedMapView original.  
  
## Comentarios  
 Este método no es operativo; no realiza ninguna acción.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::UnorderedMapView \(Clase\)](../cppcx/platform-collections-unorderedmapview-class.md)