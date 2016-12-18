---
title: "Editing Control Properties | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "controls [C++], undoing changes"
  - "controls [C++], editing properties"
  - "dialog box controls, editing properties"
ms.assetid: 9bdae21d-6dec-4344-a197-2ca4fc46d040
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Editing Control Properties
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

### Para editar las propiedades de uno o más controles  
  
1.  En el cuadro de diálogo, seleccione el control que desee modificar.  
  
    > [!NOTE]
    >  Si selecciona varios controles, sólo podrá modificar las propiedades comunes a todos ellos.  
  
2.  En la [ventana Propiedades](../Topic/Properties%20Window.md), cambie las propiedades del control.  
  
    > [!NOTE]
    >  Cuando la propiedad **Bitmap** se establece en **True** para un botón, botón de radio o control de tipo casilla, se implementa el estilo BS\_BITMAP para el control.  Para obtener más información, vea [Estilos de botón](../mfc/reference/button-styles.md).  Si desea un ejemplo de asociación de un mapa de bits con un control, vea [CButton::SetBitmap](../Topic/CButton::SetBitmap.md).  Los mapas de bits no aparecerán en el control mientras se encuentre en el editor de recursos de cuadro de diálogo.  
  
### Para deshacer los cambios de las propiedades de un control  
  
1.  Asegúrese de que el control tiene el foco en el Editor de cuadros de diálogo.  
  
2.  Elija **Deshacer** en el menú **Edición** \(si el foco no está en el control, el comando **Deshacer** no estará disponible\).  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Recursos de aplicaciones](../Topic/Resources%20in%20Desktop%20Apps.md) en la *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, cómo obtener acceso a recursos, cómo mostrar recursos estáticos y cómo asignar cadenas de recursos a propiedades, vea [Tutorial: Adaptar formularios Windows Forms](http://msdn.microsoft.com/es-es/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](../Topic/Walkthrough:%20Using%20Resources%20for%20Localization%20with%20ASP.NET.md).  
  
 Requisitos  
  
 Win32  
  
## Vea también  
 [Controls in Dialog Boxes](../mfc/controls-in-dialog-boxes.md)