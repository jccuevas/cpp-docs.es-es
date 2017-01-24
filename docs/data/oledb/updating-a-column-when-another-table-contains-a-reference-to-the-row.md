---
title: "Actualizar una columna cuando otra tabla contiene una referencia a la fila | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "conjuntos de filas, actualizaciones de columnas"
ms.assetid: abb5db69-055d-431f-b12d-ad2940a661ba
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Actualizar una columna cuando otra tabla contiene una referencia a la fila
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Algunos proveedores pueden detectar qué columnas cambian en la fila, pero muchos otros no.  Como resultado, actualizar una columna puede causar un error cuando hay una referencia a la fila que intentamos actualizar.  Para resolver este problema, cree un descriptor de acceso independiente que contenga sólo las columnas que desea modificar.  Pase el número del descriptor de acceso a `SetData`.  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)