---
title: Implementación de la barra de estado en MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- COldStatusBar
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e593227daabb2d2c25d593cfb58ef23ba7855be7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436720"
---
# <a name="status-bar-implementation-in-mfc"></a>Implementación de barra de estado en MFC

Un [CStatusBar](../mfc/reference/cstatusbar-class.md) objeto es una barra de controles con una fila de paneles de salida de texto. Los paneles de resultados se usan habitualmente como líneas de mensaje y como indicadores de estado. Algunos ejemplos son las líneas de mensaje de Ayuda de menú que se describe brevemente el comando de menú seleccionado y los indicadores que muestran el estado de otras claves, BLOQ NUM y Bloq Despl.

A partir de la versión 4.0 de MFC, las barras de estado se implementan mediante la clase [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md), que encapsula el control común de la barra de estado. Por compatibilidad con versiones anteriores, MFC conserva la implementación de barra de estado antigua de la clase `COldStatusBar`. Describe la documentación para versiones anteriores de MFC `COldStatusBar` en `CStatusBar`.

[CStatusBar:: GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl), una función miembro nuevo a 4.0 de MFC, le permite aprovechar las ventajas de soporte técnico del control común de Windows para la barra de estado personalización y funcionalidad adicional. `CStatusBar` las funciones miembro proporcionan la mayoría de la funcionalidad de los controles comunes de Windows; Sin embargo, cuando se llama a `GetStatusBarCtrl`, puedes usar las barras de estado aún más las características de una barra de estado. Cuando se llama a `GetStatusBarCtrl`, devolverá una referencia a un `CStatusBarCtrl` objeto. Puede usar esa referencia para manipular el control de barra de estado.

La siguiente ilustración muestra una barra de estado que muestra varios indicadores.

![Barra de estado](../mfc/media/vc37dy1.gif "vc37dy1") una barra de estado

Al igual que la barra de herramientas, el objeto de barra de estado está incrustado en su ventana de marco principal y se crea automáticamente cuando se construye la ventana de marco. La barra de estado, al igual que todas las barras de control, se destruye automáticamente también cuando se destruye el marco primario.

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Actualizar el texto de un panel de barra de estado](../mfc/updating-the-text-of-a-status-bar-pane.md)

- Clases MFC [CStatusBar](../mfc/reference/cstatusbar-class.md) y [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)

- [Barras de control](../mfc/control-bars.md)

- [Barras de cuadro de diálogo](../mfc/dialog-bars.md)

- [Barras de herramientas (implementación de la barra de herramientas MFC)](../mfc/mfc-toolbar-implementation.md)

## <a name="see-also"></a>Vea también

[Barras de estado](../mfc/status-bars.md)

