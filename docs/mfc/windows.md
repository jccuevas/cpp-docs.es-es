---
title: Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], window
- windows [MFC]
- MFC, windows
- window objects [MFC], MFC Framework
ms.assetid: dd92bf34-842e-40fe-8aea-3028b55314d5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 664afc2d842a7072ed41d579939e530e01c6e33f
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46431780"
---
# <a name="windows"></a>Windows

Esta serie de artículos trata los objetos de ventana en el marco de trabajo MFC. Todas las ventanas MFC se derivan de la clase [CWnd](../mfc/reference/cwnd-class.md), incluidos controles, las vistas, cuadros de diálogo y ventanas de marco.

El primer grupo de artículos describe [window (objetos)](../mfc/window-objects.md) en general. Hacer referencia a este grupo para obtener información general sobre los objetos de ventana de C++, cómo encapsulan un `HWND`, y cómo usarlos al crear sus propias ventanas, como ventanas secundarias.

El segundo grupo de artículos describe [ventanas de marco](../mfc/frame-windows.md): windows que coloca un marco alrededor de contenido, en particular. Hacer referencia a este grupo para obtener información acerca de cómo administra el marco de trabajo MFC ventanas de marco y el contenido que enmarcan, incluidas las barras de control y vistas.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

*Temas sobre objetos de ventana en General*

- [Window (objetos)](../mfc/window-objects.md)

- [Relación entre un C++ administra objetos de ventana y HWND](../mfc/relationship-between-a-cpp-window-object-and-an-hwnd.md)

- [Clases de ventana derivadas](../mfc/derived-window-classes.md)

- [Creación de objetos de ventana](../mfc/creating-windows.md)

- [Destrucción de objetos de ventana](../mfc/destroying-window-objects.md)

- [Registrar clases de ventana""](../mfc/registering-window-classes.md)

- [Trabajar con objetos window](../mfc/working-with-window-objects.md)

- [Contextos de dispositivo](../mfc/device-contexts.md): objetos que facilitan el dibujo de Windows independientes del dispositivo

- [Objetos gráficos](../mfc/graphic-objects.md): lápices, pinceles, fuentes, los mapas de bits, paletas, regiones

*Temas de la ventana de marco*

- [Ventanas de marco](../mfc/frame-windows.md): window (objetos) que ofrecen marcos

- [Las vistas y ventanas de marco](../mfc/frame-windows.md)

- [Clases de ventana de marco](../mfc/frame-window-classes.md)

- [Estilos de ventana de marco](../mfc/frame-window-styles-cpp.md)

- [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [¿Qué ventanas de marco](../mfc/what-frame-windows-do.md)

- [Usar ventanas de marco](../mfc/using-frame-windows.md)

- [Administrar ventanas MD/secundarias (la ventana MDICLIENT)](../mfc/managing-mdi-child-windows.md)

- [Administrar menús, barras de control y aceleradores](../mfc/managing-menus-control-bars-and-accelerators.md)

- [CFrameWnd](../mfc/reference/cframewnd-class.md)

- [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)

- [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)

- [Uso de vistas](../mfc/using-views.md)

- [Varios tipos de documentos, vistas y marco de Windows (ventanas divisoras)](../mfc/multiple-document-types-views-and-frame-windows.md)

- [Mensajes (mapas y funciones del controlador)](../mfc/messages.md)

*Crear y destruir Windows*

- [Secuencia de creación de ventanas general](../mfc/general-window-creation-sequence.md)

- [Destruir objetos window](../mfc/destroying-window-objects.md)

- [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)

- [Destruir ventanas de marco](../mfc/destroying-frame-windows.md)

*Crear Windows divisor*

- [Crear ventanas divisoras](../mfc/multiple-document-types-views-and-frame-windows.md)

*Administrar Windows secundarios y la vista actual*

- [Administrar ventanas secundarias MDI](../mfc/managing-mdi-child-windows.md)

- [Administrar la vista actual](../mfc/managing-the-current-view.md)

- [Administrar menús, barras de control y aceleradores](../mfc/managing-menus-control-bars-and-accelerators.md)

*Trabajar con contextos de dispositivo y estilos de ventana*

- [Usar lápices y otros objetos gráficos en un contexto de dispositivo](../mfc/graphic-objects.md)

- [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Vea también

[Elementos de la interfaz de usuario](../mfc/user-interface-elements-mfc.md)<br/>
[Cuadros de diálogo](../mfc/dialog-boxes.md)<br/>
[Barras de herramientas](../mfc/toolbars.md)<br/>
[Barras de estado](../mfc/status-bars.md)<br/>
[Barras de cuadro de diálogo](../mfc/dialog-bars.md)

