---
title: Estilos de ventana de marco (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- window styles [MFC]
- PreCreateWindow method, setting window styles
- windows [MFC], MFC
- frame windows [MFC], styles
- MFC, frame windows
- styles [MFC], windows
ms.assetid: fc5058c1-eec8-48d8-9f76-3fc01cfa53f7
ms.openlocfilehash: cade8e7e50779437feb73a94058dc62118c03c10
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274653"
---
# <a name="frame-window-styles-c"></a>Estilos de ventana de marco (C++)

Las ventanas de marco que obtiene con el marco de trabajo son adecuadas para la mayoría de los programas, pero puede obtener una flexibilidad adicional mediante el uso de las funciones avanzadas [PreCreateWindow](../mfc/reference/cwnd-class.md#precreatewindow) y la función global de MFC [AfxRegisterWndClass ](../mfc/reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow` es una función miembro de `CWnd`.

Si aplica el **WS_HSCROLL** y **WS_VSCROLL** estilos a la ventana de marco principal, en su lugar, se aplican a la **MDICLIENT** ventana, por lo que los usuarios pueden desplazarse el **MDICLIENT** área.

Si la ventana **FWS_ADDTOTITLE** bit de estilo se establece (que es de forma predeterminada), la vista indica qué título que se mostrará en la barra de título de la ventana según el nombre de la vista del documento de la ventana de marco.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Administrar ventanas secundarias MDI (MDICLIENT)](../mfc/managing-mdi-child-windows.md), la ventana dentro de un marco de MDI que contiene las ventanas secundarias MDI

- [Cambiar los estilos de una ventana creada por MFC](../mfc/changing-the-styles-of-a-window-created-by-mfc.md)

- [Estilos de ventana](../mfc/reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Vea también

[Ventanas de marco](../mfc/frame-windows.md)
