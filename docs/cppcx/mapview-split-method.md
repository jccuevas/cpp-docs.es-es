---
title: "MapView::Split (M&#233;todo) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "collection/Platform::Collections::MapView::Split"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "MapView::Split (Método)"
ms.assetid: b863e223-2282-4d1a-b995-77a690120542
caps.latest.revision: 5
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
---
# MapView::Split (M&#233;todo)
Divide el objeto MapView actual en dos objetos MapView. Este método no es operativo.  
  
## Sintaxis  
  
```  
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
 La primera parte del objeto MapView original.  
  
 `secondPartition`  
 La segunda parte del objeto MapView original.  
  
## Comentarios  
 Este método no es operativo; no realiza ninguna acción.  
  
## Requisitos  
 **Encabezado:** collection.h  
  
 **Espacio de nombres:** Platform::Collections  
  
## Vea también  
 [Platform::Collections::MapView \(Clase\)](../cppcx/platform-collections-mapview-class.md)