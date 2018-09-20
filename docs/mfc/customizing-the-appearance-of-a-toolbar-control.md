---
title: Personalizar la apariencia de un Control de barra de herramientas | Microsoft Docs
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
ms.openlocfilehash: 3c8c66990335e2925e6edd7a884b119df3fc9f88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430233"
---
# <a name="customizing-the-appearance-of-a-toolbar-control"></a>Personalizar la apariencia de un control de barra de herramientas

Clase `CToolBarCtrl` proporciona muchos estilos que afectan a la apariencia (y, en ocasiones, el comportamiento) del objeto de barra de herramientas. Modificar el objeto de barra de herramientas estableciendo el `dwCtrlStyle` parámetro de la `CToolBarCtrl::Create` (o `CToolBar::CreateEx`) función miembro, al crear el control de barra de herramientas.

Los estilos siguientes afectan el aspecto "3D" de los botones de barra de herramientas y la colocación del texto del botón:

- **TBSTYLE_FLAT** crea una barra de herramientas plana donde la barra de herramientas y los botones son transparentes. Texto del botón aparece debajo de los mapas de bits de botón. Cuando se utiliza este estilo, automáticamente se resalta el botón situado debajo del cursor.

- **TBSTYLE_TRANSPARENT** crea una barra de herramientas transparente. En una barra de herramientas transparente, la barra de herramientas es transparente, pero los botones no están. Texto del botón aparece debajo de los mapas de bits de botón.

- **TBSTYLE_LIST** lugares botón texto a la derecha de los mapas de bits de botón.

> [!NOTE]
>  Para evitar problemas repaint, el **TBSTYLE_FLAT** y **TBSTYLE_TRANSPARENT** estilos deben establecerse antes de que el objeto de barra de herramientas está visible.

Los estilos siguientes determinan si la barra de herramientas permite que un usuario a volver a colocar botones individuales dentro de un objeto de barra de herramientas mediante el método arrastrar y colocar:

- **TBSTYLE_ALTDRAG** permite a los usuarios cambiar la posición de un botón de barra de herramientas, arrástrelo manteniendo presionado ALT. Si no se especifica este estilo, el usuario debe mantener presionada la tecla MAYÚS al arrastrar un botón.

    > [!NOTE]
    >  El **CCS_ADJUSTABLE** estilo debe especificarse para habilitar los botones de barra de herramientas.

- **TBSTYLE_REGISTERDROP** genera **TBN_GETOBJECT** notificación de mensajes de solicitud quitar objetos de destino cuando el puntero del mouse pasa por encima de los botones de barra de herramientas.

Los estilos restantes afectan a aspectos visuales y del objeto de barra de herramientas:

- **TBSTYLE_WRAPABLE** crea una barra de herramientas que puede tener varias líneas de botones. Botones de barra de herramientas pueden "encapsular" a la línea siguiente cuando la barra de herramientas se vuelve demasiado estrecho para incluir todos los botones en la misma línea. Ajuste se produce en los límites y de separación.

- **TBSTYLE_CUSTOMERASE** genera **NM_CUSTOMDRAW** cuando procesa los mensajes de notificación **WM_ERASEBKGND** mensajes.

- **TBSTYLE_TOOLTIPS** crea un control de información sobre herramientas que una aplicación puede utilizar para mostrar texto descriptivo para los botones en la barra de herramientas.

Para obtener una lista completa de los estilos de barra de herramientas y los estilos extendidos, vea [Control de barra de herramientas y los estilos de botón](/windows/desktop/Controls/toolbar-control-and-button-styles) y [estilos extendidos de barra de herramientas](/windows/desktop/Controls/toolbar-extended-styles) en el SDK de Windows.

## <a name="see-also"></a>Vea también

[Uso de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

