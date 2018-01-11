---
title: Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: CToolTipCtrl
dev_langs: C++
helpviewer_keywords:
- tool tips [MFC], creating
- CToolTipCtrl class [MFC], using
ms.assetid: 0a34583f-f66d-46a1-a239-31b80ea395ad
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: da4c98e327d2d78050410e75869c894d73324281
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-ctooltipctrl-to-create-and-manipulate-a-ctooltipctrl-object"></a>Usar CToolTipCtrl para crear y manipular un objeto CToolTipCtrl
Este es un ejemplo de [CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md) uso:  
  
### <a name="to-create-and-manipulate-a-ctooltipctrl"></a>Para crear y manipular un objeto CToolTipCtrl  
  
1.  Construir la `CToolTipCtrl` objeto.  
  
2.  Llame a [crear](../mfc/reference/ctooltipctrl-class.md#create) para crear el control común de Windows tool tip y adjuntarla a la `CToolTipCtrl` objeto.  
  
3.  Llame a [AddTool](../mfc/reference/ctooltipctrl-class.md#addtool) para registrar una herramienta con el control de información sobre herramientas, para que se muestre la información almacenada en la información sobre herramientas cuando el cursor está en la herramienta.  
  
4.  Llame a [SetToolInfo](../mfc/reference/ctooltipctrl-class.md#settoolinfo) para establecer la información que mantiene una información sobre herramientas para una herramienta.  
  
5.  Llame a [SetToolRect](../mfc/reference/ctooltipctrl-class.md#settoolrect) para establecer un nuevo rectángulo delimitador para una herramienta.  
  
6.  Llame a [HitTest](../mfc/reference/ctooltipctrl-class.md#hittest) para probar un punto para determinar si está dentro del rectángulo delimitador de la herramienta especificada y, si es así, recuperar la información acerca de la herramienta.  
  
7.  Llame a [GetToolCount](../mfc/reference/ctooltipctrl-class.md#gettoolcount) recuperar un recuento de las herramientas registrado con el control de información sobre herramientas.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)

