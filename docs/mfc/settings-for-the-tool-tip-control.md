---
title: "Configuraci&#243;n del control de informaci&#243;n sobre herramientas | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "información sobre herramientas [C++], activar"
  - "CToolTipCtrl (clase), configuración"
ms.assetid: ff8c5c46-2047-403a-bd98-ffec3d21ee3a
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Configuraci&#243;n del control de informaci&#243;n sobre herramientas
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede establecer el control de información sobre herramientas \([CToolTipCtrl](../mfc/reference/ctooltipctrl-class.md)\) como activo o inactivo. Si lo establece como activo, el control de información sobre herramientas aparece cuando el cursor está sobre una herramienta. Si lo establece como inactivo, el control de información sobre herramientas no aparece cuando el cursor esté sobre una herramienta. Llame a [Activar](../Topic/CToolTipCtrl::Activate.md) para activar o desactivar un control de información sobre herramientas.  
  
 Puede establecer la información sobre herramientas activa para mostrarla cuando el cursor esté sobre una herramienta, tanto si la ventana propietaria del control de información sobre herramientas está activa como si está inactiva, mediante el estilo **TTS\_ALWAYSTIP**. Si no usa este estilo, el control de información sobre herramientas aparece cuando la ventana propietaria de la herramienta está activa, pero no cuando está inactiva.  
  
 La mayoría de las aplicaciones contienen barras de herramientas con herramientas que corresponden a comandos de menú. Para estas herramientas, es conveniente que el control de información sobre herramientas muestre el mismo texto que el elemento de menú correspondiente. El sistema quita automáticamente los caracteres aceleradores Y comercial \(&\) de todas las cadenas que se pasan a un control de información sobre herramientas, a menos que el control tenga el estilo **TTS\_NOPREFIX**.  
  
## Vea también  
 [Usar CToolTipCtrl](../mfc/using-ctooltipctrl.md)   
 [Controles](../mfc/controls-mfc.md)