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
ms.openlocfilehash: 9f4f9d90113d5074555d1b0cc411f854abc67fe5
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81377464"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Personalizar la apariencia de un control de barra de herramientas

Clase `CToolBarCtrl` proporciona muchos estilos que afectan a la apariencia (y, ocasionalmente, el comportamiento) del objeto de barra de herramientas. Modifique el objeto de `dwCtrlStyle` barra `CToolBarCtrl::Create` de `CToolBar::CreateEx`herramientas estableciendo el parámetro de la (o ) función miembro, cuando cree por primera vez el control de barra de herramientas.

Los siguientes estilos afectan al aspecto "3D" de los botones de la barra de herramientas y a la colocación del texto del botón:

- **TBSTYLE_FLAT** Crea una barra de herramientas plana donde tanto la barra de herramientas como los botones son transparentes. El texto del botón aparece debajo de los mapas de bits de los botones. Cuando se utiliza este estilo, el botón debajo del cursor se resalta automáticamente.

- **TBSTYLE_TRANSPARENT** Crea una barra de herramientas transparente. En una barra de herramientas transparente, la barra de herramientas es transparente, pero los botones no. El texto del botón aparece debajo de los mapas de bits de los botones.

- **TBSTYLE_LIST** Coloca el texto del botón a la derecha de los mapas de bits de los botones.

> [!NOTE]
> Para evitar problemas de repintado, los **estilos TBSTYLE_FLAT** y **TBSTYLE_TRANSPARENT** deben establecerse antes de que el objeto de la barra de herramientas esté visible.

Los siguientes estilos determinan si la barra de herramientas permite a un usuario cambiar la posición de botones individuales dentro de un objeto de barra de herramientas mediante arrastrar y colocar:

- **TBSTYLE_ALTDRAG** Permite a los usuarios cambiar la posición de un botón de la barra de herramientas arrastrándolo mientras mantiene presionada la tecla ALT. Si no se especifica este estilo, el usuario debe mantener presionada la tecla May mayús mientras arrastra un botón.

    > [!NOTE]
    >  El estilo **CCS_ADJUSTABLE** debe especificarse para permitir que se arrastren los botones de la barra de herramientas.

- **TBSTYLE_REGISTERDROP** Genera **TBN_GETOBJECT** mensajes de notificación para solicitar objetos de destino de colocación cuando el puntero del mouse pasa por encima de los botones de la barra de herramientas.

Los estilos restantes afectan a los aspectos visuales y no visuales del objeto de barra de herramientas:

- **TBSTYLE_WRAPABLE** Crea una barra de herramientas que puede tener varias líneas de botones. Los botones de la barra de herramientas pueden "ajustar" a la siguiente línea cuando la barra de herramientas se vuelve demasiado estrecha para incluir todos los botones en la misma línea. El ajuste se produce en los límites de separación y no de grupo.

- **TBSTYLE_CUSTOMERASE** Genera mensajes de notificación **NM_CUSTOMDRAW** cuando procesa **WM_ERASEBKGND** mensajes.

- **TBSTYLE_TOOLTIPS** Crea un control de información sobre herramientas que una aplicación puede utilizar para mostrar texto descriptivo para los botones de la barra de herramientas.

Para obtener una lista completa de estilos de barra de herramientas y estilos extendidos, vea Control de barra de herramientas [y Estilos](/windows/win32/Controls/toolbar-control-and-button-styles) de botón y [Estilos extendidos](/windows/win32/Controls/toolbar-extended-styles) de barra de herramientas en el Windows SDK.

## <a name="see-also"></a>Consulte también

[Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
