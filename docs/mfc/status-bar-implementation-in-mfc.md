---
title: Implementación de barra de estado en MFC
ms.date: 11/19/2018
f1_keywords:
- COldStatusBar
helpviewer_keywords:
- status bars [MFC], implementing in MFC
- CStatusBarCtrl class [MFC], and MFC status bars
- CStatusBar class [MFC], and CStatusBarCtrl class [MFC]
- CStatusBarCtrl class [MFC], and CStatusBar class [MFC]
- status bars [MFC], backward compatibility
- status bars [MFC], old with COldStatusBar class [MFC]
- COldStatusBar class [MFC]
- status bars [MFC], and CStatusBarCtrl class
- CStatusBar class [MFC], and MFC status bars
- status indicators
- status bars [MFC], Windows 95 implementation
ms.assetid: be5cd876-38e3-4d5c-b8cb-16d57a16a142
ms.openlocfilehash: 521b24646b673159d14e89bd57ea698a7ba73381
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175380"
---
# <a name="status-bar-implementation-in-mfc"></a>Implementación de barra de estado en MFC

Un [CStatusBar](../mfc/reference/cstatusbar-class.md) objeto es una barra de controles con una fila de paneles de salida de texto. Los paneles de resultados se usan habitualmente como líneas de mensaje y como indicadores de estado. Algunos ejemplos son las líneas de mensaje de Ayuda de menú que se describe brevemente el comando de menú seleccionado y los indicadores que muestran el estado de otras claves, BLOQ NUM y Bloq Despl.

A partir de la versión 4.0 de MFC, las barras de estado se implementan mediante la clase [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), que encapsula el control común de la barra de estado. Por compatibilidad con versiones anteriores, MFC conserva la implementación de barra de estado antigua de la clase `COldStatusBar`. Describe la documentación para versiones anteriores de MFC `COldStatusBar` en `CStatusBar`.

[CStatusBar:: GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), una función miembro nuevo a 4.0 de MFC, le permite aprovechar las ventajas de soporte técnico del control común de Windows para la barra de estado personalización y funcionalidad adicional. `CStatusBar` las funciones miembro proporcionan la mayoría de la funcionalidad de los controles comunes de Windows; Sin embargo, cuando se llama a `GetStatusBarCtrl`, puedes usar las barras de estado aún más las características de una barra de estado. Cuando se llama a `GetStatusBarCtrl`, devolverá una referencia a un `CStatusBarCtrl` objeto. Puede usar esa referencia para manipular el control de barra de estado.

La siguiente ilustración muestra una barra de estado que muestra varios indicadores.

![Barra de estado](../mfc/media/vc37dy1.gif "barra de estado") <br/>
Una barra de estado

Al igual que la barra de herramientas, el objeto de barra de estado está incrustado en su ventana de marco principal y se crea automáticamente cuando se construye la ventana de marco. La barra de estado, al igual que todas las barras de control, se destruye automáticamente también cuando se destruye el marco primario.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Actualizar el texto de un panel de barra de estado](../mfc/updating-the-text-of-a-status-bar-pane.md)

- Clases MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) y [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [Barras de control](../mfc/control-bars.md)

- [Barras de cuadro de diálogo](../mfc/dialog-bars.md)

- [Barras de herramientas (implementación de la barra de herramientas MFC)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>Vea también

[Barras de estado](../mfc/status-bars.md)

