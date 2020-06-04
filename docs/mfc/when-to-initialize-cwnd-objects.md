---
title: Cuándo inicializar los objetos CWnd
ms.date: 11/04/2016
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
ms.openlocfilehash: aa396ade2e8ab4e1245e161423de7bd5bfafaaf8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405721"
---
# <a name="when-to-initialize-cwnd-objects"></a>Cuándo inicializar los objetos CWnd

No se puede crear sus propios secundarios windows o llamar a las funciones de API de Windows en el constructor de un `CWnd`-objeto derivado. Esto es porque el `HWND` para el `CWnd` objeto aún no se ha creado. Inicialización de Windows más específico, como agregar ventanas secundarias, debe realizarse dentro de un [OnCreate](../mfc/reference/cwnd-class.md#oncreate) controlador de mensajes.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Crear ventanas de marco de documento](../mfc/creating-document-frame-windows.md)

- [Crear documentos y vistas](../mfc/document-view-creation.md)

## <a name="see-also"></a>Vea también

[Uso de ventanas de marco](../mfc/using-frame-windows.md)
