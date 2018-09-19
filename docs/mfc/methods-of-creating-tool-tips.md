---
title: Métodos de creación de información sobre herramientas | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 26f6e7cbf8c6464afa90c52f9cd91dcdb55de767
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33349537"
---
# <a name="methods-of-creating-tool-tips"></a>Métodos de creación de información sobre herramientas
MFC proporciona tres clases para crear y administrar la herramienta de control de sugerencia: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) y [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). Las funciones de miembro de sugerencia de herramienta en estas clases ajustan la API del control común de Windows. Clase `CToolBarCtrl` y clase `CToolTipCtrl` se derivan de la clase `CWnd`.  
  
 `CWnd` proporciona cuatro funciones de miembro para crear y administrar información sobre herramientas: [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), y [OnToolHitTest ](../mfc/reference/cwnd-class.md#ontoolhittest). Vea estas funciones miembro individuales para obtener más información sobre cómo implementar la información sobre herramientas.  
  
 Si crea una barra de herramientas mediante `CToolBarCtrl`, puede implementar información sobre herramientas para esa barra de herramientas directamente utilizando las siguientes funciones miembro: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) y [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Vea estas funciones miembro individuales y [controlar notificaciones de sugerencia de herramienta](../mfc/handling-tool-tip-notifications.md) para obtener más información sobre cómo implementar la información sobre herramientas.  
  
 La `CToolTipCtrl` clase proporciona la funcionalidad de control de sugerencia de herramienta común de Windows. Control de información sobre una única herramienta puede proporcionar información de más de una herramienta. Una herramienta es ya sea una ventana, como una ventana secundaria, control o un área rectangular definida por la aplicación en el área de cliente de una ventana. El [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) clase se deriva de `CToolTipCtrl` y proporciona la funcionalidad y estilos visuales adicionales.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)

