---
title: "Métodos de creación de información sobre herramientas | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CToolTipCtrl class [MFC], creating tool tips
- tool tips [MFC], tool tip controls
- tool tips [MFC], creating
ms.assetid: b015e9f4-ddfb-49a4-a5a6-fa2d45e4d328
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c2d38bd76ff5c8d06daf474cf1c1dcc0286183bc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="methods-of-creating-tool-tips"></a>Métodos de creación de información sobre herramientas
MFC proporciona tres clases para crear y administrar la herramienta de control de sugerencia: [CWnd](../mfc/reference/cwnd-class.md), [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md), [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) y [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md). Las funciones de miembro de sugerencia de herramienta en estas clases ajustan la API del control común de Windows. Clase `CToolBarCtrl` y clase `CToolTipCtrl` se derivan de la clase `CWnd`.  
  
 `CWnd`proporciona cuatro funciones de miembro para crear y administrar información sobre herramientas: [EnableToolTips](../mfc/reference/cwnd-class.md#enabletooltips), [CancelToolTips](../mfc/reference/cwnd-class.md#canceltooltips), [FilterToolTipMessage](../mfc/reference/cwnd-class.md#filtertooltipmessage), y [ OnToolHitTest](../mfc/reference/cwnd-class.md#ontoolhittest). Vea estas funciones miembro individuales para obtener más información sobre cómo implementar la información sobre herramientas.  
  
 Si crea una barra de herramientas mediante `CToolBarCtrl`, puede implementar información sobre herramientas para esa barra de herramientas directamente utilizando las siguientes funciones miembro: [GetToolTips](../mfc/reference/ctoolbarctrl-class.md#gettooltips) y [SetToolTips](../mfc/reference/ctoolbarctrl-class.md#settooltips). Vea estas funciones miembro individuales y [controlar notificaciones de sugerencia de herramienta](../mfc/handling-tool-tip-notifications.md) para obtener más información sobre cómo implementar la información sobre herramientas.  
  
 La `CToolTipCtrl` clase proporciona la funcionalidad de control de sugerencia de herramienta común de Windows. Control de información sobre una única herramienta puede proporcionar información de más de una herramienta. Una herramienta es ya sea una ventana, como una ventana secundaria, control o un área rectangular definida por la aplicación en el área de cliente de una ventana. El [CMFCToolTipCtrl](../mfc/reference/cmfctooltipctrl-class.md) clase se deriva de `CToolTipCtrl` y proporciona la funcionalidad y estilos visuales adicionales.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)

