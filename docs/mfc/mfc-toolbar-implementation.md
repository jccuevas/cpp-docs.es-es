---
title: Implementación de barra de herramientas de MFC
ms.date: 11/04/2016
helpviewer_keywords:
- toolbars [MFC], creating
- buttons [MFC], MFC toolbars
- toolbars [MFC], docking
- CToolBar class [MFC], creating toolbars
- MFC toolbars
- floating toolbars [MFC]
- toolbars [MFC], floating
- docking toolbars [MFC]
- bitmaps [MFC], toolbar
- toolbar controls [MFC]
- CToolBarCtrl class [MFC], implementing toolbars
- tool tips [MFC], enabling
- toolbars [MFC]
- toolbars [MFC], implementing MFC toolbars
ms.assetid: af3319ad-c430-4f90-8361-e6a2c06fd084
ms.openlocfilehash: 7876e9403389c19a24e5a482534d0f223eaa4bf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626122"
---
# <a name="mfc-toolbar-implementation"></a>Implementación de barra de herramientas de MFC

Una barra de herramientas es una [barra](control-bars.md) de controles que contiene las imágenes de mapa de bits de los controles. Estas imágenes se comportan como botones de comando, casillas o botones de radio. MFC proporciona la clase [CToolbar](reference/ctoolbar-class.md) para administrar las barras de herramientas.

Si se habilita, los usuarios de las barras de herramientas de MFC pueden acoplarlas al borde de una ventana o hacerlas "flotar" en cualquier parte dentro de la ventana de la aplicación. MFC no admite barras de herramientas personalizables como las del entorno de desarrollo.

MFC admite también información sobre herramientas: pequeñas ventanas emergentes que describen el propósito de un botón de la barra de herramientas cuando se coloca el mouse sobre el botón. De forma predeterminada, cuando el usuario presiona un botón de la barra de herramientas, aparece una cadena de estado en la barra de estado (si hay una). Se puede activar la actualización de la barra de estado al "sobrevolar" para mostrar la cadena de estado cuando el mouse se coloca sobre el botón sin presionarlo.

> [!NOTE]
> A partir de la versión 4.0 de MFC, las barras de herramientas y la información sobre herramientas se implementan con la funcionalidad de Windows 95 y versiones posteriores, en lugar de usar la implementación anterior específica de MFC.

Para mantener la compatibilidad con versiones anteriores, MFC conserva la implementación anterior de la barra de herramientas en la clase `COldToolBar` . La documentación de las versiones anteriores de MFC describe `COldToolBar` en `CToolBar` .

Puede crear la primera barra de herramientas de un programa si selecciona la opción Barra de herramientas en el Asistente para aplicaciones. También puede crear barras de herramientas adicionales.

En este artículo se presenta lo siguiente:

- [Botones de barra de herramientas](#_core_toolbar_buttons)

- [Barras de herramientas de acoplamiento y flotantes](#_core_docking_and_floating_toolbars)

- [Barras de herramientas y información sobre herramientas](#_core_toolbars_and_tool_tips)

- [Clases CToolBar y CToolBarCtrl](#_core_the_ctoolbar_and_ctoolbarctrl_classes)

- [Mapa de bits de la barra de herramientas](#_core_the_toolbar_bitmap)

## <a name="toolbar-buttons"></a><a name="_core_toolbar_buttons"></a>Botones de barra de herramientas

Los botones de una barra de herramientas son análogos a los elementos de un menú. Ambos tipos de objetos de la interfaz de usuario generan comandos, que se pueden administrar mediante las funciones de controlador que el programa proporciona. Los botones de la barra de herramientas duplican a menudo la funcionalidad de los comandos de menú y proporcionan una interfaz de usuario alternativa para la misma funcionalidad. Para organizar esta duplicación de forma sencilla, asigne el mismo id. al botón y al elemento de menú.

Puede hacer que los botones de una barra de herramientas aparezcan y se comporten como botones de comando, las casillas o los botones de radio. Para obtener más información, vea la clase [CToolBar](reference/ctoolbar-class.md).

## <a name="docking-and-floating-toolbars"></a><a name="_core_docking_and_floating_toolbars"></a>Barras de herramientas de acoplamiento y flotantes

Una barra de herramientas de MFC puede:

- Mantenerse estática a lo largo de un lado de la ventana primaria.

- Arrastrarse y "acoplarse", o asociarse, a cualquier lado o lados de la ventana primaria que el usuario especifique.

- "Flotar", o desasociarse de la ventana marco, en su propia ventana minimarco para que el usuario pueda moverla a cualquier posición adecuada.

- Cambiar de tamaño mientras flota.

Para obtener más información, vea el artículo [barras de herramientas de acoplamiento y flotantes](docking-and-floating-toolbars.md).

## <a name="toolbars-and-tool-tips"></a><a name="_core_toolbars_and_tool_tips"></a>Barras de herramientas y información sobre herramientas

También se puede hacer que las barras de herramientas de MFC muestren "información sobre herramientas", que son ventanas emergentes minúsculas que contienen una breve descripción de texto del propósito de un botón de la barra de herramientas. Cuando el usuario mueve el mouse sobre un botón de la barra de herramientas, la ventana de información sobre herramientas emerge para proporcionar una sugerencia. Para obtener más información, vea la información sobre herramientas de la [barra de herramientas](toolbar-tool-tips.md)del artículo.

## <a name="the-ctoolbar-and-ctoolbarctrl-classes"></a><a name="_core_the_ctoolbar_and_ctoolbarctrl_classes"></a>Clases CToolBar y CToolBarCtrl

Las barras de herramientas de la aplicación se administran a través de la clase [CToolBar](reference/ctoolbar-class.md). A partir de la versión 4.0 de MFC, `CToolBar` se ha implementado de nuevo para utilizar el control común de barra de herramientas que está disponible en Windows 95 o versiones posteriores y en Windows NT versión 3.51 o versiones posteriores.

Esta nueva implementación da lugar a menos código MFC para las barras de herramientas, porque MFC utiliza la compatibilidad con el sistema operativo. La nueva implementación también mejora la capacidad. Puede utilizar `CToolBar` las funciones miembro para manipular barras de herramientas, o puede obtener una referencia al objeto [CToolBarCtrl](reference/ctoolbarctrl-class.md) subyacente y llamar a sus funciones miembro para la personalización de la barra de herramientas y la funcionalidad adicional.

> [!TIP]
> Si ha invertido mucho en la implementación MFC anterior de `CToolBar`, esa compatibilidad sigue estando disponible. Vea el artículo [uso de las barras de herramientas anteriores](using-your-old-toolbars.md).

Vea también el ejemplo general de MFC [DOCKTOOL](../overview/visual-cpp-samples.md).

## <a name="the-toolbar-bitmap"></a><a name="_core_the_toolbar_bitmap"></a>Mapa de bits de la barra de herramientas

Una vez construido, un objeto `CToolBar` carga un solo mapa de bits que contiene una imagen de cada botón para crear la imagen de la barra de herramientas. El Asistente para aplicaciones crea un mapa de bits de la barra de herramientas estándar que se puede personalizar con el editor de la [barra de herramientas](../windows/toolbar-editor.md)Visual C++.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Aspectos básicos de las barras de herramientas](toolbar-fundamentals.md)

- [Barras de herramientas de acoplamiento y flotantes](docking-and-floating-toolbars.md)

- [Información sobre herramientas de barra de herramientas](toolbar-tool-tips.md)

- [Trabajar con el control ToolBar](working-with-the-toolbar-control.md)

- [Usar las barras de herramientas anteriores](using-your-old-toolbars.md)

- Clases [CToolBar](reference/ctoolbar-class.md) y [CToolBarCtrl](reference/ctoolbarctrl-class.md)

## <a name="see-also"></a>Consulte también

[Barras de herramientas](toolbars.md)<br/>
[Editor de barras de herramientas](../windows/toolbar-editor.md)
