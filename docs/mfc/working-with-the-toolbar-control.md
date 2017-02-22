---
title: "Trabajar con el control de barra de herramientas | Microsoft Docs"
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
  - "CToolBarCtrl (clase), obtener acceso a la barra de herramientas"
  - "GetToolBarCtrl (método)"
  - "controles de barra de herramientas [MFC], obtener acceso"
  - "barras de herramientas [C++], obtener acceso a controles comunes"
ms.assetid: b19409d5-3831-42c7-80ae-195c49dc9085
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Trabajar con el control de barra de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica cómo puede tener acceso a [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) que es la base de [CToolBar](../mfc/reference/ctoolbar-class.md) para tener un mayor control sobre las barras de herramientas.  Éste es un tema avanzado.  
  
## Procedimientos  
  
#### Para tener acceso al control común de la barra de herramientas al objeto de CToolBar  
  
1.  Llamada [CToolBar::GetToolBarCtrl](../Topic/CToolBar::GetToolBarCtrl.md).  
  
 `GetToolBarCtrl` devuelve una referencia a un objeto de [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .  Puede utilizar la referencia a las funciones miembro de llamada de la clase de control toolbar.  
  
> [!CAUTION]
>  Mientras que llamar a las funciones de `CToolBarCtrl`**Get** es seguro, tenga cuidado si llama a las funciones de **Establecer** .  Éste es un tema avanzado.  No debería ser necesario normalmente tener acceso al control toolbar subyacente.  
  
### ¿Sobre qué desea obtener más información?  
  
-   [Controles \(controles comunes de Windows\)](../mfc/controls-mfc.md)  
  
-   [Fundamentos de la barra de herramientas](../mfc/toolbar-fundamentals.md)  
  
-   [Barras de herramientas de acoplamiento y flotantes](../mfc/docking-and-floating-toolbars.md)  
  
-   [Dinámicamente el tamaño de la barra de herramientas](../mfc/docking-and-floating-toolbars.md)  
  
-   [Información sobre herramientas de la barra de herramientas](../mfc/toolbar-tool-tips.md)  
  
-   [Actualizaciones de barra de estado de la exhibición de vuelo](../mfc/toolbar-tool-tips.md)  
  
-   [Administrar notificaciones de información sobre herramientas](../mfc/handling-tool-tip-notifications.md)  
  
-   Clases [CToolBar](../mfc/reference/ctoolbar-class.md) y [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md)  
  
-   [Administrar notificaciones de personalización](../mfc/handling-customization-notifications.md)  
  
-   [Barras de herramientas varias](../mfc/toolbar-fundamentals.md)  
  
-   [Mediante las barras de herramientas anteriores](../mfc/using-your-old-toolbars.md)  
  
-   [Barras de controles](../mfc/control-bars.md)  
  
 Para obtener información general sobre cómo utilizar los controles comunes de Windows, vea [Controles comunes](http://msdn.microsoft.com/library/windows/desktop/bb775493).  
  
## Vea también  
 [Implementación de barra de herramientas de MFC](../mfc/mfc-toolbar-implementation.md)