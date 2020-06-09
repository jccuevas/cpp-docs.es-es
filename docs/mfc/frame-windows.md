---
title: Ventanas de marco
ms.date: 11/19/2018
helpviewer_keywords:
- document frame windows [MFC]
- windows [MFC], MDI
- window classes [MFC], frame
- single document interface (SDI) [MFC]
- single document interface (SDI) [MFC], frame windows
- views [MFC], and frame windows
- CFrameWnd class [MFC], frame windows
- frame windows [MFC]
- frame windows [MFC], about frame windows
- MFC, frame windows
- MDI [MFC], frame windows
- splitter windows [MFC], and frame windows
ms.assetid: 40677339-8135-4f5e-aba6-3fced3078077
ms.openlocfilehash: 39c0b4b866fa123d8bcae639342c925570d96e1b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625824"
---
# <a name="frame-windows"></a>Ventanas de marco

Cuando una aplicación se ejecuta en Windows, el usuario interactúa con los documentos que se muestran en ventanas de marco. Una ventana de marco de documento tiene dos componentes principales: el marco y el contenido que trama. Una ventana de marco de documento puede ser una ventana de marco de interfaz de un [único documento](sdi-and-mdi.md) (SDI) o una ventana secundaria de [interfaz de múltiples documentos](sdi-and-mdi.md) (MDI). Windows administra la mayor parte de la interacción del usuario con la ventana de marco: mover y cambiar el tamaño de la ventana, cerrarla y minimizarla y maximizarla. Administra el contenido dentro del marco.

## <a name="frame-windows-and-views"></a>Ventanas de marco y vistas

El marco de trabajo de MFC utiliza ventanas de marco para contener vistas. Los dos componentes (marco y contenido) se representan y administran mediante dos clases diferentes en MFC. Una clase de ventana de marco administra el marco y una clase de vista administra el contenido. La ventana de vista es un elemento secundario de la ventana de marco. El dibujo y otra interacción del usuario con el documento tienen lugar en el área cliente de la vista, no en el área cliente de la ventana de marco. La ventana marco proporciona un marco visible alrededor de una vista, completo con una barra de título y controles de ventana estándar, como un menú de control, botones para minimizar y maximizar la ventana y controles para cambiar el tamaño de la ventana. El "contenido" consta del área de cliente de la ventana, que está totalmente ocupada por una ventana secundaria, la vista. En la siguiente ilustración se muestra la relación entre una ventana de marco y una vista.

![Vista de ventana marco](../mfc/media/vc37fx1.gif "Vista de ventana de marco") <br/>
Vista y ventana de marco

## <a name="frame-windows-and-splitter-windows"></a>Ventanas de marco y ventanas divisoras

Otra disposición común es que la ventana marco contenga varias vistas, normalmente mediante una [ventana divisora](multiple-document-types-views-and-frame-windows.md). En una ventana divisora, el área cliente de la ventana de marco está ocupada por una ventana divisora, que a su vez tiene varias ventanas secundarias, denominadas paneles, que son vistas.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

**Temas generales de la ventana de marco**

- [Objetos de ventana](window-objects.md)

- [Clases de ventana de marco](frame-window-classes.md)

- [Clases de ventana de marco creadas por el Asistente para aplicaciones](frame-window-classes-created-by-the-application-wizard.md)

- [Estilos de ventana de marco](frame-window-styles-cpp.md)

- [¿Qué hacen las ventanas de marco?](what-frame-windows-do.md)

**Temas sobre el uso de ventanas de marco**

- [Uso de ventanas de marco](using-frame-windows.md)

- [Crear ventanas de marco de documento](creating-document-frame-windows.md)

- [Destrucción de ventanas de marco](destroying-frame-windows.md)

- [Administración de ventanas secundarias MDI](managing-mdi-child-windows.md)

- [Administrar la vista actual](managing-the-current-view.md) en una ventana de marco que contiene más de una vista

- [Administrar menús, barras de control y aceleradores (otros objetos que comparten el espacio de la ventana de marco)](managing-menus-control-bars-and-accelerators.md)

**Temas sobre las funcionalidades especiales de la ventana de marco**

- [Arrastrar y colocar archivos](dragging-and-dropping-files-in-a-frame-window.md) del explorador de archivos o del administrador de archivos en una ventana de marco

- [Responder al intercambio dinámico de datos (DDE)](responding-to-dynamic-data-exchange-dde.md)

- [Estados semimodales: ayuda contextual de Windows (orquestar otras acciones de ventana)](orchestrating-other-window-actions.md)

- [Estados semimodales: impresión y vista previa de impresión (orquestar otras acciones de ventana)](orchestrating-other-window-actions.md)

**Temas sobre otros tipos de ventanas**

- [Usar vistas](using-views.md)

- [Cuadros de diálogo](dialog-boxes.md)

- [Permite](controls-mfc.md)

## <a name="see-also"></a>Consulte también

[Windows](windows.md)
