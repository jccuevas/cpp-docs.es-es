---
title: "Control de información sobre configuración de la herramienta | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- tool tips [MFC], activating
- CToolTipCtrl class [MFC], settings
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 406e35b6ab694ca972d4cd6add0dcca7586e5005
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="settings-for-the-tool-tip-control"></a>Configuración del control de información sobre herramientas
Puede establecer el control de información sobre herramientas ([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)) como activo o inactivo. Si lo establece como activo, el control de información sobre herramientas aparece cuando el cursor está sobre una herramienta. Si lo establece como inactivo, el control de información sobre herramientas no aparece cuando el cursor esté sobre una herramienta. Llame a [Activar](../mfc/reference/ctooltipctrl-class.md#activate) para activar o desactivar un control de información sobre herramientas.  
  
 Puede establecer la información sobre herramientas activa para mostrarla cuando el cursor esté sobre una herramienta, tanto si la ventana propietaria del control de información sobre herramientas está activa como si está inactiva, mediante el estilo **TTS_ALWAYSTIP** . Si no usa este estilo, el control de información sobre herramientas aparece cuando la ventana propietaria de la herramienta está activa, pero no cuando está inactiva.  
  
 La mayoría de las aplicaciones contienen barras de herramientas con herramientas que corresponden a comandos de menú. Para estas herramientas, es conveniente que el control de información sobre herramientas muestre el mismo texto que el elemento de menú correspondiente. El sistema quita automáticamente los caracteres aceleradores de "y" comercial (&) de todas las cadenas que se pasa a un control de información sobre herramientas, a menos que el control tiene el **TTS_NOPREFIX** estilo.  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)

