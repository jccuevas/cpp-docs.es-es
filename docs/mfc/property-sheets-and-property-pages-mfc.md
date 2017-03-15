---
title: "Hojas de propiedades y p&#225;ginas de propiedades (MFC) | Microsoft Docs"
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
  - "CPropertyPage (clase), hojas de propiedades y páginas"
  - "CPropertySheet (clase), hojas de propiedades y páginas"
  - "cuadros de diálogo de MFC, pestañas"
  - "páginas de propiedades, hojas de propiedades"
  - "hojas de propiedades, páginas de propiedades"
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Hojas de propiedades y p&#225;ginas de propiedades (MFC)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

MFC [cuadro de diálogo](../mfc/dialog-boxes.md) puede adquirir un “diálogo de ficha” busca escribiendo las hojas de propiedades y las páginas de propiedades.  Denominado una “hoja de propiedades” en MFC, este tipo de cuadro de diálogo, similar a muchos cuadros de diálogo de Microsoft Word, Excel, y Visual C\+\+, parece contener una pila de hojas con pestañas, como una pila de carpetas de archivos vistas de nuevo para admitir, o grupo de ventanas colocada en cascadas.  Los Controles de la ficha adelantada son visibles; sólo la ficha está visible en pestañas posteriores.  Las hojas de propiedades son especialmente útiles para administrar un gran número de propiedades o valores que entren en lugar cuidadosamente en varios grupos.  Normalmente, una hoja de propiedades puede simplificar una interfaz de usuario reemplazando varios cuadros de diálogo independientes.  
  
 A partir de la versión 4.0 de MFC, las hojas de propiedades y las páginas de propiedades se implementan utilizando controles comunes que vienen con la versión 3.51 de Windows 95 y Windows NT y posterior.  
  
 Las hojas de propiedades se implementan con las clases [CPropertySheet](../mfc/reference/cpropertysheet-class.md) y [CPropertyPage](../mfc/reference/cpropertypage-class.md) \(descritos en la *referencia de MFC*\).  `CPropertySheet` define el cuadro de diálogo total, que puede contener las “varias páginas” basadas en `CPropertyPage`.  
  
 Para obtener información sobre cómo crear y trabajar con hojas de propiedades, vea el tema [Hojas de propiedades](../mfc/property-sheets-mfc.md).  
  
## Vea también  
 [Cuadros de diálogo](../mfc/dialog-boxes.md)   
 [Ciclo de vida de un cuadro de diálogo](../mfc/life-cycle-of-a-dialog-box.md)   
 [Hojas de propiedades y páginas de propiedades en MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)   
 [Intercambiar datos](../mfc/exchanging-data.md)   
 [Crear una hoja de propiedades no modal](../mfc/creating-a-modeless-property-sheet.md)   
 [Controlar el botón Aplicar](../mfc/handling-the-apply-button.md)