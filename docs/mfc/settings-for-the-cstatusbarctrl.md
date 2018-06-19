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
ms.openlocfilehash: 1eea701c33001ffa3585c2d5847f3056454b7850
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380167"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Configuración de CStatusBarCtrl
La posición predeterminada de un [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) ventana de estado es a lo largo de la parte inferior de la ventana primaria, pero puede especificar el `CCS_TOP` estilo que se va a hacer que aparezca en la parte superior del área de cliente de la ventana primaria.  
  
 Puede especificar el **SBARS_SIZEGRIP** estilo que se va a incluir un control de tamaño en el extremo derecho de la `CStatusBarCtrl` ventana de estado. Un control de tamaño es similar a un borde de tamaño; es un área rectangular que el usuario hacer clic y arrastrar para cambiar el tamaño de la ventana primaria.  
  
> [!NOTE]
>  Si combina la `CCS_TOP` y **SBARS_SIZEGRIP** estilos, el control de tamaño resultante no es funcional incluso aunque el sistema dibuja en la ventana de estado.  
  
 El procedimiento de ventana para la ventana de estado establece automáticamente el tamaño inicial y la posición de la ventana de control. El ancho es igual que la del área de cliente de la ventana primaria. El alto se basa en las métricas de la fuente que está seleccionada actualmente en el contexto de dispositivo de la ventana de estado y en el ancho de los bordes de la ventana.  
  
 El procedimiento de ventana ajusta automáticamente el tamaño de la ventana de estado cada vez que recibe un `WM_SIZE` mensaje. Normalmente, cuando cambia el tamaño de la ventana primaria, el sitio principal envía un `WM_SIZE` mensaje en la ventana de estado.  
  
 Puede establecer el alto mínimo del área de dibujo de una ventana de estado mediante una llamada a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), especifica el alto mínimo en píxeles. El área de dibujo no incluye los bordes de la ventana.  
  
 Recuperar los anchos de los bordes de una ventana de estado mediante una llamada a [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Esta función miembro incluye el puntero a una matriz de tres elementos que recibe el ancho del borde horizontal, del borde vertical y el borde entre rectángulos.  
  
## <a name="see-also"></a>Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

