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
ms.openlocfilehash: 3c22944537370a44aee1af1cf71281264ed4969b
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626458"
---
# <a name="frame-window-styles-c"></a>Estilos de ventana de marco (C++)

Las ventanas de marco que obtiene con el marco de trabajo son adecuadas para la mayoría de los programas, pero puede obtener flexibilidad adicional mediante las funciones avanzadas [PreCreateWindow](reference/cwnd-class.md#precreatewindow) y la función global de MFC [AfxRegisterWndClass (](reference/application-information-and-management.md#afxregisterwndclass). `PreCreateWindow`es una función miembro de `CWnd` .

Si aplica los estilos **WS_HSCROLL** y **WS_VSCROLL** a la ventana de marco principal, se aplican en su lugar a la ventana **MdiClient** para que los usuarios puedan desplazarse por el área **MdiClient** .

Si se establece el bit de estilo **FWS_ADDTOTITLE** de la ventana (que es de forma predeterminada), la vista indica a la ventana de marco el título que se va a mostrar en la barra de título de la ventana basándose en el nombre del documento de la vista.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Administrar ventanas secundarias MDI (MdiClient)](managing-mdi-child-windows.md), la ventana de un marco MDI que contiene las ventanas SECUNDARIAs MDI

- [Cambio de estilos de una ventana creada por MFC](changing-the-styles-of-a-window-created-by-mfc.md)

- [Estilos de ventana](reference/styles-used-by-mfc.md#window-styles)

## <a name="see-also"></a>Consulte también

[Ventanas de marco](frame-windows.md)
