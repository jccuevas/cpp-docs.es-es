---
title: Clases de ventana de marco
ms.date: 11/04/2016
helpviewer_keywords:
- frame window classes [MFC], about frame window classes
- frame window classes [MFC]
- windows [MFC], MDI
- document frame windows [MFC], classes
- single document interface (SDI), frame windows
- window classes [MFC], frame
- MFC, frame windows
- MDI [MFC], frame windows
- classes [MFC], window
ms.assetid: c27e43a7-8ad0-4759-b1b7-43f4725f4132
ms.openlocfilehash: ffa5b966ee042120213896dc7ad9d81c048ef928
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625813"
---
# <a name="frame-window-classes"></a>Clases de ventana de marco

Cada aplicación tiene una "ventana de marco principal", una ventana de escritorio que normalmente tiene el nombre de la aplicación en su título. Cada documento normalmente tiene una "ventana de marco de documento". Una ventana de marco de documento contiene al menos una vista, que presenta los datos del documento.

## <a name="frame-windows-in-sdi-and-mdi-applications"></a>Ventanas de marco en aplicaciones SDI y MDI

En el caso de una aplicación SDI, hay una ventana de marco derivada de la clase [CFrameWnd](reference/cframewnd-class.md). Esta ventana es la ventana de marco principal y la ventana de marco de documento. En el caso de una aplicación MDI, la ventana de marco principal se deriva de la clase [CMDIFrameWnd](reference/cmdiframewnd-class.md)y las ventanas de marco de documento, que son ventanas secundarias MDI, se derivan de la clase [CMDIChildWnd](reference/cmdichildwnd-class.md).

## <a name="use-the-frame-window-class-or-derive-from-it"></a>Usar la clase de ventana de marco o derivarse de ella

Estas clases proporcionan la mayor parte de la funcionalidad de la ventana de marco que necesita para sus aplicaciones. En circunstancias normales, el comportamiento predeterminado y la apariencia que proporcionan se ajustarán a sus necesidades. Si necesita una funcionalidad adicional, derive de estas clases.

### <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Clases de ventana de marco creadas por el Asistente para aplicaciones](frame-window-classes-created-by-the-application-wizard.md)

- [Estilos de ventana de marco](frame-window-styles-cpp.md)

- [Cambio de estilos de una ventana creada por MFC](changing-the-styles-of-a-window-created-by-mfc.md)

## <a name="see-also"></a>Consulte también

[Ventanas de marco](frame-windows.md)
