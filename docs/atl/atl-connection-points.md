---
title: "Puntos de conexi&#243;n en ATL | Microsoft Docs"
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
  - "ATL, puntos de conexión"
  - "puntos de conexión [C++], acerca de los puntos de conexión"
  - "conexiones, puntos de conexión"
ms.assetid: 17d76165-5f83-4f95-b36d-483821c247a1
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Puntos de conexi&#243;n en ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un objeto conectable es aquel que acepta interfaces de salida.  Una interfaz de salida permite que el objeto se comunique con un cliente.  Para cada interfaz de salida, el objeto conectable expone un punto de conexión.  Cada interfaz de salida es implementada por un cliente en un objeto denominado receptor.  
  
 ![Puntos de conexión](../atl/media/vc2zw31.png "vc2ZW31")  
  
 Cada punto de conexión es compatible con la interfaz [IConnectionPoint](http://msdn.microsoft.com/library/windows/desktop/ms694318).  El objeto conectable expone sus puntos de conexión al cliente a través de la interfaz [IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857).  
  
## En esta sección  
 [Clases de puntos de conexión ATL](../atl/atl-connection-point-classes.md)  
 Describe brevemente las clases ATL compatibles con puntos de conexión.  
  
 [Agregar puntos de conexión a un objeto](../atl/adding-connection-points-to-an-object.md)  
 Describe los pasos utilizados para agregar puntos de conexión a un objeto.  
  
 [Ejemplo de puntos de conexión ATL](../atl/atl-connection-point-example.md)  
 Proporciona un ejemplo de cómo declarar un punto de conexión.  
  
## Secciones relacionadas  
 [ATL](../atl/active-template-library-atl-concepts.md)  
 Proporciona vínculos a temas sobre cómo programar utilizando Active Template Library.  
  
## Vea también  
 [Conceptos](../atl/active-template-library-atl-concepts.md)