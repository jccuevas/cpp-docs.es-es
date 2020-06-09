---
title: Personalizar la apariencia de un control de barra de herramientas
ms.date: 11/04/2016
f1_keywords:
- TBSTYLE_
helpviewer_keywords:
- flat toolbars
- CToolBar class [MFC], styles
- transparent toolbars
- TBSTYLE_ styles [MFC]
- CToolBarCtrl class [MFC], object styles
- toolbar controls [MFC], style
ms.assetid: fd0a73db-7ad1-4fe4-889b-02c3980f49e8
ms.openlocfilehash: ddccb5f05152d95377b430d7492ede3c86926e37
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619284"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Personalizar la apariencia de un control de barra de herramientas

La clase `CToolBarCtrl` proporciona muchos estilos que afectan a la apariencia (y, en ocasiones, al comportamiento) del objeto de barra de herramientas. Modifique el objeto de barra de herramientas estableciendo el `dwCtrlStyle` parámetro de la `CToolBarCtrl::Create` `CToolBar::CreateEx` función miembro (o), cuando cree por primera vez el control de barra de herramientas.

Los estilos siguientes afectan al aspecto "3D" de los botones de la barra de herramientas y a la posición del texto del botón:

- **TBSTYLE_FLAT** Crea una barra de herramientas plana donde la barra de herramientas y los botones son transparentes. El texto del botón aparece en mapas de bits de botón. Cuando se usa este estilo, el botón situado debajo del cursor se resalta automáticamente.

- **TBSTYLE_TRANSPARENT** Crea una barra de herramientas transparente. En una barra de herramientas transparente, la barra de herramientas es transparente, pero no los botones. El texto del botón aparece en mapas de bits de botón.

- **TBSTYLE_LIST** Coloca el texto del botón a la derecha de los mapas de bits del botón.

> [!NOTE]
> Para evitar problemas de Repaint, se deben establecer los estilos **TBSTYLE_FLAT** y **TBSTYLE_TRANSPARENT** antes de que el objeto de barra de herramientas esté visible.

Los estilos siguientes determinan si la barra de herramientas permite a un usuario cambiar la posición de botones individuales dentro de un objeto Toolbar mediante arrastrar y colocar:

- **TBSTYLE_ALTDRAG** Permite a los usuarios cambiar la posición de un botón de la barra de herramientas arrastrándolo mientras mantiene presionada la tecla ALT. Si no se especifica este estilo, el usuario debe mantener presionada la tecla Mayús mientras arrastra un botón.

    > [!NOTE]
    >  Se debe especificar el estilo de **CCS_ADJUSTABLE** para permitir el arrastre de los botones de la barra de herramientas.

- **TBSTYLE_REGISTERDROP** Genera mensajes de notificación de **TBN_GETOBJECT** para solicitar la eliminación de objetos de destino cuando el puntero del mouse pasa por encima de los botones de la barra de herramientas.

Los estilos restantes afectan a los aspectos visuales y no visuales del objeto Toolbar:

- **TBSTYLE_WRAPABLE** Crea una barra de herramientas que puede tener varias líneas de botones. Los botones de la barra de herramientas pueden "ajustarse" a la línea siguiente cuando la barra de herramientas se vuelve demasiado estrecha para incluir todos los botones en la misma línea. El ajuste se produce en los límites de separación y de no agrupación.

- **TBSTYLE_CUSTOMERASE** Genera mensajes de notificación de **NM_CUSTOMDRAW** cuando procesa mensajes **WM_ERASEBKGND** .

- **TBSTYLE_TOOLTIPS** Crea un control de información sobre herramientas que una aplicación puede usar para mostrar el texto descriptivo de los botones de la barra de herramientas.

Para obtener una lista completa de los estilos de barra de herramientas y los estilos extendidos, vea el [control de barra de herramientas y](/windows/win32/Controls/toolbar-control-and-button-styles) los estilos [extendidos](/windows/win32/Controls/toolbar-extended-styles) de barra de herramientas en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Usar CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[Permite](controls-mfc.md)
