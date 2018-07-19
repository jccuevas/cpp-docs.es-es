---
title: Control de información sobre configuración de la herramienta | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 39de60d17dae5a6d7b2965350162117d049c29c8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951119"
---
# <a name="settings-for-the-tool-tip-control"></a>Configuración del control de información sobre herramientas
Puede establecer el control de información sobre herramientas ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) como activo o inactivo. Si lo establece como activo, el control de información sobre herramientas aparece cuando el cursor está sobre una herramienta. Si lo establece como inactivo, el control de información sobre herramientas no aparece cuando el cursor esté sobre una herramienta. Llame a [Activar](../mfc/reference/ctooltipctrl-class.md#activate) para activar o desactivar un control de información sobre herramientas.  
  
 Puede establecer una información sobre herramientas activa para mostrar la información sobre herramientas cuando el cursor esté sobre una herramienta, ventana propietaria del control de información sobre herramientas está activa o inactiva, usando el estilo TTS_ALWAYSTIP como si no. Si no usa este estilo, el control de información sobre herramientas aparece cuando la ventana propietaria de la herramienta está activa, pero no cuando está inactiva.  
  
 La mayoría de las aplicaciones contienen barras de herramientas con herramientas que corresponden a comandos de menú. Para estas herramientas, es conveniente que el control de información sobre herramientas muestre el mismo texto que el elemento de menú correspondiente. El sistema quita automáticamente el "y" comercial (&) caracteres aceleradores de todas las cadenas que se pasa a un control de información sobre herramientas, a menos que el control tiene el estilo TTS_NOPREFIX.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)

