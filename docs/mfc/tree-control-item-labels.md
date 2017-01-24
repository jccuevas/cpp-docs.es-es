---
title: "Etiquetas de elemento de control de &#225;rbol | Microsoft Docs"
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
  - "CTreeCtrl (clase), etiquetas del elemento"
  - "etiquetas del elemento"
  - "etiquetas del elemento, controles de árbol"
  - "etiquetas, CTreeCtrl (elementos)"
  - "controles de árbol, etiquetas del elemento"
ms.assetid: fe834107-1a25-4280-aced-774c11565805
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Etiquetas de elemento de control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Especifica normalmente el texto de la etiqueta de elemento al agregar el elemento al control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\).  La función miembro de `InsertItem` puede pasar una estructura de [TVITEM](http://msdn.microsoft.com/library/windows/desktop/bb773456) que define las propiedades del elemento, incluida una cadena que contiene el texto de la etiqueta.  `InsertItem` tiene varias sobrecargas que se puede llamar con diferentes combinaciones de parámetros.  
  
 Un control de árbol asigna memoria para almacenar cada elemento; el texto de las etiquetas de elemento toma una parte significativa de esta memoria.  Si la aplicación mantiene una copia de las cadenas en el control de árbol, puede reducir los requisitos de memoria del control especificando el valor de **LPSTR\_TEXTCALLBACK** en el miembro de **pszText** de `TV_ITEM` o el parámetro de `lpszItem` en lugar de pasar cadenas reales al control de árbol.  Mediante las causas de **LPSTR\_TEXTCALLBACK** el control de árbol para recuperar el texto de la etiqueta de un elemento de la aplicación cada vez que el elemento necesite volver a dibujar.  Para recuperar el texto, el control de árbol envía un mensaje de notificación de [TVN\_GETDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773518) , que incluye la dirección de una estructura de [NMTVDISPINFO](http://msdn.microsoft.com/library/windows/desktop/bb773418) .  Debe responder estableciendo los miembros adecuados de la estructura incluida.  
  
 Un control de árbol utiliza la memoria asignada de la pila del proceso que crea el control de árbol.  El número máximo de elementos en un control de árbol se basa en la cantidad de memoria disponible en el montón.  Cada elemento toma 64 bytes.  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)