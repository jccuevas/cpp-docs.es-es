---
title: "Agregar controles a una hoja de propiedades | Microsoft Docs"
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
  - "controles [MFC], agregar a hojas de propiedades"
  - "hojas de propiedades, agregar controles"
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Agregar controles a una hoja de propiedades
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

De forma predeterminada, una hoja de propiedades asigna el área de ventana para las páginas de propiedades, el índice de tabulación, y OK, delete, y aplica los botones. \(La hoja de propiedades no modal de A no tiene OK, no cancela, y no aplicado los botones\). Puede agregar otros controles a la hoja de propiedades.  Por ejemplo, puede agregar una ventana de vista previa a la derecha del área de la página de propiedades para mostrar al usuario a parecerían la configuración actual si se aplicarán a un objeto externo.  
  
 Puede agregar controles al diálogo de la hoja de propiedades en el controlador de `OnCreate` .  Los controles adicionales serviciales suelen expandir el tamaño del diálogo de la hoja de propiedades.  Después de llamar a la clase base **CPropertySheet::OnCreate**, la llamada [GetWindowRect](../Topic/CWnd::GetWindowRect.md) para obtener el ancho y alto de la ventana actualmente asignada de la hoja de propiedades, expanda las dimensiones del rectángulo, y llamada [MoveWindow](../Topic/CWnd::MoveWindow.md) para cambiar el tamaño de la ventana de la hoja de propiedades.  
  
## Vea también  
 [Hojas de propiedades](../mfc/property-sheets-mfc.md)   
 [CPropertyPage Class](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet Class](../mfc/reference/cpropertysheet-class.md)