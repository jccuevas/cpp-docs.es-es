---
title: ¿Qué marco Windows | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- frame windows [MFC], about frame windows
- frame windows [MFC], tasks
- MFC, frame windows
ms.assetid: 1148a952-6786-4622-b5a8-68a2d7eae584
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bf97fb086f9ede43f9679e66a7c917b800f97dc8
ms.sourcegitcommit: e4a690bf33b44432179de0bc537e26616d13c553
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/09/2018
ms.locfileid: "48892194"
---
# <a name="what-frame-windows-do"></a>¿Para qué sirven las ventanas de marco?

Además de contener una vista, ventanas de marco son responsables de numerosas tareas relacionadas con la coordinación del marco con su vista y con la aplicación. [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) y [CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md) heredar [CFrameWnd](../mfc/reference/cframewnd-class.md), por lo que tienen `CFrameWnd` capacidades, así como nuevas capacidades que agreguen. Algunos ejemplos de las ventanas secundarias son vistas, controles como botones y cuadros de lista y barras de control, incluidas las barras de herramientas, barras de estado y las barras de cuadro de diálogo.

La ventana de marco es responsable de administrar el diseño de sus ventanas secundarias. En el marco de trabajo MFC, una ventana de marco coloca las barras de control, vistas y otras ventanas secundarias dentro de su área de cliente.

La ventana de marco también envía comandos a sus vistas y puede responder a mensajes de notificación de ventanas de control.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Barras de control (cómo encajan en la ventana de marco)](../mfc/control-bars.md)

- [Administrar menús, barras de control y aceleradores (cómo encajan en la ventana de marco)](../mfc/managing-menus-control-bars-and-accelerators.md)

- [Enrutamiento de comandos (desde la ventana de marco para su vista y otros destinos de comando)](../mfc/command-routing.md)

- [Arquitectura de documento /View](../mfc/document-view-architecture.md)

- [Barras de control](../mfc/control-bars.md)

- [Controles](../mfc/controls-mfc.md)

## <a name="see-also"></a>Vea también

[Ventanas de marco](../mfc/frame-windows.md)

