---
title: "Personalizar la apariencia del elemento de encabezado | Microsoft Docs"
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
  - "CHeaderCtrl (clase), personalizar elementos de menú"
  - "estilos HDS_"
  - "controles del encabezado, personalización de elementos"
ms.assetid: b1e1e326-ec7d-4dbd-a46f-96a3e2055618
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Personalizar la apariencia del elemento de encabezado
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Estableciendo el parámetro *de dwStyle* al crear un control de encabezado \([CHeaderCtrl::Create](../Topic/CHeaderCtrl::Create.md)\), puede definir el aspecto y comportamiento de los elementos de encabezado o del control de encabezado propio.  
  
 A continuación se muestra un muestreo de los estilos que puede establecer, y su finalidad:  
  
-   Para que un elemento de encabezado parecer un mismo botón, utilice el estilo de `HDS_BUTTONS` .  
  
     Utilice este estilo si desea realizar acciones en respuesta a los clics del mouse en un elemento de encabezado, como ordenar datos por una columna concreta, como se hace en Microsoft Outlook.  
  
-   Para dar a los elementos de encabezado un aspecto del “seguimiento activo” cuando el cursor pasa sobre ellos, utilice el estilo de `HDS_HOTTRACK` .  
  
     El seguimiento activo muestra un contorno 3D como el pasar el puntero sobre un elemento en una barra de otra forma plana.  
  
-   Para indicar que el control de encabezado debe ocultar, utilice el estilo de `HDS_HIDDEN` .  
  
     El estilo de `HDS_HIDDEN` indica que el control de encabezado está diseñado para utilizarse como un contenedor de datos y no control visual.  Este estilo automáticamente no oculta el control pero, en su lugar, afecta al comportamiento de `CHeaderCtrl::Layout`.  El valor devuelto en el miembro de **cy** de la estructura de `WINDOWPOS` será cero que indica que el control no debe estar visible para el usuario.  
  
 Para obtener más información sobre estas propiedades, vea [Elementos](http://msdn.microsoft.com/library/windows/desktop/bb775238) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  Para obtener información acerca de cómo agregar elementos a un control de encabezado, vea [Agregar elementos al Control de encabezado](../mfc/adding-items-to-the-header-control.md).  
  
## Vea también  
 [Usar CHeaderCtrl](../mfc/using-cheaderctrl.md)   
 [Controles](../mfc/controls-mfc.md)