---
title: Personalizar la apariencia de un Control de barra de herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBSTYLE_
dev_langs:
- C++
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96ec459e1c956c805991f2e37d22b8260f0ffdf2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Personalizar la apariencia de un control de barra de herramientas
Clase `CToolBarCtrl` proporciona muchos estilos que afectan a la apariencia (y, en ocasiones, el comportamiento) del objeto de barra de herramientas. Modificar el objeto de barra de herramientas estableciendo el `dwCtrlStyle` parámetro de la `CToolBarCtrl::Create` (o `CToolBar::CreateEx`) función miembro, cuando se crea el control de barra de herramientas.  
  
 Los estilos siguientes afectan el aspecto "3D" de los botones de barra de herramientas y la colocación del texto del botón:  
  
-   **TBSTYLE_FLAT** crea una barra de herramientas plana donde la barra de herramientas y los botones son transparentes. Texto del botón aparece debajo de mapas de bits de botón. Cuando se utiliza este estilo, el botón debajo del cursor se resalta automáticamente.  
  
-   **TBSTYLE_TRANSPARENT** crea una barra de herramientas transparente. En una barra de herramientas transparente, la barra de herramientas es transparente, pero los botones no están. Texto del botón aparece debajo de mapas de bits de botón.  
  
-   **TBSTYLE_LIST** lugares botón texto a la derecha de los mapas de bits de botón.  
  
> [!NOTE]
>  Para evitar problemas de volver a dibujar la **TBSTYLE_FLAT** y **TBSTYLE_TRANSPARENT** estilos deben establecerse antes de que el objeto de barra de herramientas está visible.  
  
 Los estilos siguientes determinan si la barra de herramientas permite que un usuario cambiar la posición de los botones individuales dentro de un objeto de barra de herramientas mediante arrastrar y colocar:  
  
-   **TBSTYLE_ALTDRAG** permite a los usuarios cambiar la posición de un botón de barra de herramientas, arrastre manteniendo presionada la tecla ALT. Si no se especifica este estilo, el usuario debe mantener presionada la tecla MAYÚS al arrastrar un botón.  
  
    > [!NOTE]
    >  El `CCS_ADJUSTABLE` estilo debe especificarse para habilitar los botones de barra de herramientas.  
  
-   **TBSTYLE_REGISTERDROP** genera **TBN_GETOBJECT** notificación de mensajes para solicitar quitan objetos de destino cuando el puntero del mouse pasa por encima de los botones de barra de herramientas.  
  
 Los estilos restantes afectan a aspectos visuales y del objeto de barra de herramientas:  
  
-   `TBSTYLE_WRAPABLE` Crea una barra de herramientas que puede tener varias líneas de botones. Botones de barra de herramientas pueden "ajustarse" a la línea siguiente cuando la barra de herramientas se vuelve demasiado estrecha para incluir todos los botones en la misma línea. Ajuste se produce en los límites y separación.  
  
-   **TBSTYLE_CUSTOMERASE** genera **NM_CUSTOMDRAW** cuando procesa los mensajes de notificación `WM_ERASEBKGND` mensajes.  
  
-   `TBSTYLE_TOOLTIPS` Crea un control de información sobre herramientas que una aplicación puede utilizar para mostrar texto descriptivo para los botones en la barra de herramientas.  
  
 Para obtener una lista completa de los estilos de barra de herramientas y estilos extendidos, vea [Control de barra de herramientas y estilos de botón](http://msdn.microsoft.com/library/windows/desktop/bb760439) y [estilos extendidos de barra de herramientas](http://msdn.microsoft.com/library/windows/desktop/bb760430) en el SDK de Windows.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

