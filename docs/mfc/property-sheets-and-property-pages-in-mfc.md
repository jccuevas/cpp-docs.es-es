---
title: "Hojas de propiedades y p&#225;ginas de propiedades en MFC | Microsoft Docs"
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
  - "controles [MFC], hojas de propiedades"
  - "páginas de propiedades, MFC"
  - "hojas de propiedades, MFC"
  - "cuadros de diálogo con fichas"
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Hojas de propiedades y p&#225;ginas de propiedades en MFC
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una hoja de propiedades, también conocida como cuadro de diálogo de la ficha, es un cuadro de diálogo que contiene las páginas de propiedades.  Cada página de propiedades se basa en un recurso de plantilla de cuadro de diálogo y contiene controles.  Se incluye en una página con una ficha en la parte superior.  Los nombres de la pestaña la página e indican su propósito.  Los usuarios hacen clic en una pestaña de la hoja de propiedades para seleccionar un conjunto de controles.  
  
 Utilice las páginas para agrupar los controles de la hoja de propiedades en conjuntos significativos.  La hoja de propiedades contenida suele varios controles propios.  Éstos se aplican a todas las páginas.  
  
 Las hojas de propiedades se basan en la clase [CPropertySheet](../mfc/reference/cpropertysheet-class.md).  Las páginas de propiedades se basan en la clase [CPropertyPage](../mfc/reference/cpropertypage-class.md).  
  
 Una hoja de propiedades es una clase especial de cuadro de diálogo que se utiliza normalmente para modificar los atributos de algún objeto externo, como la selección actual en una vista.  La hoja de propiedades tiene tres partes principales: el cuadro de diálogo que contiene, una o más páginas de propiedades mostradas uno a la vez, y una ficha en la parte superior de cada página que el usuario hace clic para seleccionar esa página.  Las hojas de propiedades son útiles en situaciones en las que se tiene varios grupos similares de valores o de opciones de cambiar.  Información de los grupos de la hoja de propiedades de una manera de fácil comprensible.  
  
> [!NOTE]
>  Cuando se intenta mostrar una hoja de propiedades mediante `CPropertySheet::DoModal`, el sistema podría generar una excepción de la primero\- oportunidad.  Esta excepción se produce porque el sistema está intentando cambiar [Estilos de ventana](../mfc/reference/window-styles.md) de objeto antes de crear el objeto.  Para obtener más información sobre esta excepción, y también cómo evitar o controlarla, vea [CPropertySheet::DoModal](../Topic/CPropertySheet::DoModal.md).  
  
## Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)