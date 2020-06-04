---
title: Métodos de creación de información sobre herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
ms.openlocfilehash: 2ba935f52f24f62dded3b89df1563454cf7e0335
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383921"
---
# <a name="methods-of-creating-tool-tips"></a>Métodos de creación de información sobre herramientas

MFC proporciona tres clases para crear y administrar el control de información sobre herramientas: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) y [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). Las funciones de miembro de sugerencia de herramienta en estas clases ajustan la API del control común de Windows. Clase `CToolBarCtrl` y clase `CToolTipCtrl` se derivan de la clase `CWnd`.

`CWnd` proporciona cuatro funciones de miembro para crear y administrar información sobre herramientas: [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), y [OnToolHitTest](../mfc/reference/cwnd-class.md#ontoolhittest). Vea estas funciones miembro individuales para obtener más información acerca de cómo implementar la información sobre herramientas.

Si crea una barra de herramientas mediante `CToolBarCtrl`, puede implementar información sobre herramientas para esa barra de herramientas directamente mediante las funciones miembro siguientes: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) y [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Vea estas funciones miembro individuales y [controlar herramienta notificaciones](../mfc/handling-tool-tip-notifications.md) para obtener más información acerca de cómo implementar la información sobre herramientas.

La `CToolTipCtrl` clase proporciona la funcionalidad del control de sugerencia de herramienta común de Windows. Control de información sobre una sola herramienta puede proporcionar información de más de una herramienta. Una herramienta es cualquier ventana, como una ventana secundaria de control o un área rectangular definida por la aplicación dentro del área cliente de una ventana. El [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) clase se deriva de `CToolTipCtrl` y proporciona la funcionalidad y los estilos visuales adicionales.

## <a name="see-also"></a>Vea también

[Uso de CToolTipCtrl](../mfc/using-ctooltipctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
