---
title: "Utilizar varios conjuntos de resultados de un procedimiento almacenado | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "varios conjuntos de resultados"
  - "procedimientos almacenados, devolver conjuntos de resultados"
ms.assetid: c450c12c-a76c-4ae4-9675-071a41eeac05
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Utilizar varios conjuntos de resultados de un procedimiento almacenado
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La mayoría de los procedimientos almacenados devuelven varios conjuntos de resultados.  Estos procedimientos almacenados suelen incluir una o varias instrucciones SELECT.  El consumidor debe considerarlo para poder controlar todos los conjuntos de resultados.  
  
### Para controlar varios conjuntos de resultados  
  
1.  Cree una clase `CCommand` con `CMultipleResults` como argumento de plantilla y el descriptor de acceso que prefiera.  Normalmente, se trata de un descriptor de acceso dinámico o manual.  Si usa otro tipo de descriptor de acceso, puede que no le sea posible determinar las columnas de resultados de cada conjunto de filas.  
  
2.  Ejecute el procedimiento almacenado de la manera habitual y enlace las columnas \(vea [Cómo recuperar datos](../../data/oledb/fetching-data.md)\).  
  
3.  Utilice los datos.  
  
4.  Llame a `GetNextResult` en la clase `CCommand`.  Si hay disponible otro conjunto de filas de resultados, `GetNextResult` devuelve S\_OK y se deben volver a enlazar las columnas si se utiliza un descriptor de acceso manual.  Si `GetNextResult` devuelve un error, no hay más conjuntos de resultados disponibles.  
  
## Vea también  
 [Utilizar procedimientos almacenados](../../data/oledb/using-stored-procedures.md)