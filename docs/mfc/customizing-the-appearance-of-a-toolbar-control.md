---
title: "Personalizar la apariencia de un control de barra de herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TBSTYLE_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CToolBar (clase), estilos"
  - "CToolBarCtrl (clase), estilos de objeto"
  - "barras de herramientas planas"
  - "TBSTYLE_ (estilos)"
  - "controles de barra de herramientas [MFC], estilo"
  - "barras de herramientas transparentes"
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Personalizar la apariencia de un control de barra de herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La clase `CToolBarCtrl` proporciona muchos estilos que afectan al aspecto \(y, en ocasiones, el comportamiento\) del objeto de la barra de herramientas.  Modifique el objeto de la barra de herramientas estableciendo el parámetro de `dwCtrlStyle` de funciones miembro de `CToolBarCtrl::Create` \(o `CToolBar::CreateEx`\), al crear el control de barra de herramientas.  
  
 Los estilos siguientes afectan al aspecto “3D” de los botones de la barra de herramientas y la posición del texto del botón:  
  
-   **TBSTYLE\_FLAT** crea una barra de herramientas plana donde transparentes la barra de herramientas y los botones.  El texto del botón aparece en mapas de bits del botón.  Cuando se utiliza este estilo, el botón bajo el cursor se resalta automáticamente.  
  
-   **TBSTYLE\_TRANSPARENT** crea una barra de herramientas transparente.  En la barra de herramientas transparente, la barra de herramientas es transparente pero los botones no.  El texto del botón aparece en mapas de bits del botón.  
  
-   Texto del botón de los lugares de**TBSTYLE\_LIST**a la derecha de mapas de bits del botón.  
  
> [!NOTE]
>  Para evitar para que vuelva a problemas, estilos de **TBSTYLE\_FLAT** y de **TBSTYLE\_TRANSPARENT** establecido antes de que el objeto de la barra de herramientas está visible.  
  
 Los estilos siguientes determinan si la barra de herramientas permite que un usuario coloque los botones de nuevo individuales dentro de un objeto de la barra de herramientas mediante arrastrar y colocar:  
  
-   Usuarios de**TBSTYLE\_ALTDRAG**Permiso para cambiar la posición de un botón de la barra de herramientas arrastrarla para manteniendo ALT.  Si este estilo no se especifica, el usuario debe mantener MAYÚS mientras arrastra un botón.  
  
    > [!NOTE]
    >  El estilo de `CCS_ADJUSTABLE` se debe especificar para habilitar los botones de la barra de herramientas que se arrastrarán.  
  
-   **TBSTYLE\_REGISTERDROP** genera los mensajes de notificación de **TBN\_GETOBJECT** para solicitar los objetos de destino cuando el puntero del mouse pasa sobre los botones de la barra de herramientas.  
  
 Los estilos que afectan a los aspectos visuales y no visuales de objeto de la barra de herramientas:  
  
-   `TBSTYLE_WRAPABLE` crea una barra de herramientas que pueda tener varias líneas de botones.  Los botones de la barra de herramientas pueden “ajuste” a la línea siguiente cuando la barra de herramientas aumenta demasiado estrecha para incluir todos los botones en la misma línea.  El ajuste aparece en límites de separación y de nongroup.  
  
-   **TBSTYLE\_CUSTOMERASE** genera los mensajes de notificación de **NM\_CUSTOMDRAW** cuando procesa mensajes de `WM_ERASEBKGND` .  
  
-   `TBSTYLE_TOOLTIPS` crea un control de información sobre herramientas que una aplicación puede utilizar para mostrar el texto descriptivo para los botones de la barra de herramientas.  
  
 Para obtener una lista completa de la barra de herramientas y estilos extendidos, vea [Control toolbar y estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb760439) y [La barra de herramientas extendidas los estilos](http://msdn.microsoft.com/library/windows/desktop/bb760430) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
## Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)