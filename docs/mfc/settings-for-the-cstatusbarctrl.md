---
title: Configuración de CStatusBarCtrl | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CStatusBarCtrl
dev_langs:
- C++
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1dde1f005e53aff7ebe505d1ce619bf5c94410f8
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/26/2018
ms.locfileid: "36955461"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Configuración de CStatusBarCtrl
La posición predeterminada de un [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) ventana de estado está en la parte inferior de la ventana primaria, pero puede especificar el estilo CCS_TOP para que aparezca en la parte superior del área de cliente de la ventana primaria.  
  
 Puede especificar el estilo SBARS_SIZEGRIP para incluir un control de tamaño en el extremo derecho de la `CStatusBarCtrl` ventana de estado. Un control de tamaño es similar a un borde de tamaño; es un área rectangular que el usuario hacer clic y arrastrar para cambiar el tamaño de la ventana primaria.  
  
> [!NOTE]
>  Si combina los estilos CCS_TOP y SBARS_SIZEGRIP, el control de tamaño resultante no es funcional incluso aunque el sistema dibuja en la ventana de estado.  
  
 El procedimiento de ventana para la ventana de estado establece automáticamente el tamaño inicial y la posición de la ventana de control. El ancho es igual que la del área de cliente de la ventana primaria. El alto se basa en las métricas de la fuente que está seleccionada actualmente en el contexto de dispositivo de la ventana de estado y en el ancho de los bordes de la ventana.  
  
 El procedimiento de ventana ajusta automáticamente el tamaño de la ventana de estado cada vez que recibe un mensaje WM_SIZE. Normalmente, cuando se cambia el tamaño de la ventana primaria, el elemento primario envía un mensaje WM_SIZE a la ventana de estado.  
  
 Puede establecer el alto mínimo del área de dibujo de una ventana de estado mediante una llamada a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), especifica el alto mínimo en píxeles. El área de dibujo no incluye los bordes de la ventana.  
  
 Recuperar los anchos de los bordes de una ventana de estado mediante una llamada a [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Esta función miembro incluye el puntero a una matriz de tres elementos que recibe el ancho del borde horizontal, del borde vertical y el borde entre rectángulos.  
  
## <a name="see-also"></a>Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

