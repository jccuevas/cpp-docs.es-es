---
title: "Clases base | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases base"
  - "clases base, virtual"
  - "clases derivadas, bases múltiples"
  - "herencia, múltiple"
  - "herencia múltiple, clases base"
  - "clases base virtuales"
ms.assetid: 6e6d54d0-6f21-4a16-9103-22935d98f596
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Clases base
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El proceso de herencia crea una nueva clase derivada que se compone de los miembros de la clase o clases base más cualquier nuevo miembro agregado por la clase derivada.  En una herencia múltiple, es posible crear un gráfico de herencia donde la misma clase base forme parte de varias de las clases derivadas.  En la ilustración siguiente se muestra este tipo de gráfico.  
  
 ![Varias instancias de una clase base](../cpp/media/vc38xn1.png "vc38XN1")  
Varias instancias de una clase base única  
  
 En la ilustración, se muestran las representaciones gráficas de los componentes de `CollectibleString` y `CollectibleSortable`.  Sin embargo, la clase base, `Collectible`, está en `CollectibleSortableString` a través de la ruta de `CollectibleString` y la ruta de `CollectibleSortable`.  Para eliminar esta redundancia, estas clases se pueden declarar como clases base virtuales cuando se heredan.  
  
 Para obtener información sobre cómo declarar clases base virtuales y cómo se componen los objetos con clases base virtuales, vea [Clases base virtuales](../misc/virtual-base-classes.md).  
  
## Vea también  
 [Información general de las clases derivadas](../misc/overview-of-derived-classes.md)