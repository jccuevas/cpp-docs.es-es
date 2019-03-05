---
title: Configuración de CStatusBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: b41997fb9342a651260bc2196d212016dc0deb7e
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57285183"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Configuración de CStatusBarCtrl

La posición predeterminada de un [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) ventana de estado es a lo largo de la parte inferior de la ventana primaria, pero puede especificar el estilo CCS_TOP para que aparezca en la parte superior del área de cliente de la ventana primaria.

Puede especificar el estilo SBARS_SIZEGRIP para incluir un control de tamaño en el extremo derecho de la `CStatusBarCtrl` ventana de estado. Un control de tamaño es similar a un borde de tamaño; es un área rectangular que el usuario hacer clic y arrastre para cambiar el tamaño de la ventana primaria.

> [!NOTE]
>  Si combina los estilos CCS_TOP y SBARS_SIZEGRIP, el control de tamaño resultante no es funcional, aunque el sistema lo dibuja en la ventana de estado.

El procedimiento de ventana para la ventana de estado establece automáticamente el tamaño inicial y la posición de la ventana de control. El ancho es igual que el del área de cliente de la ventana primaria. El alto se basa en las métricas de la fuente que está seleccionada actualmente en el contexto de dispositivo de la ventana de estado y el ancho de los bordes de la ventana.

El procedimiento de ventana ajusta automáticamente el tamaño de la ventana de estado cada vez que reciba un mensaje WM_SIZE. Normalmente, cuando cambia el tamaño de la ventana primaria, el elemento primario envía un mensaje WM_SIZE a la ventana de estado.

Puede establecer el alto mínimo del área de dibujo de una ventana de estado mediante una llamada a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), especifica el alto mínimo en píxeles. El área de dibujo no incluye los bordes de la ventana.

Recuperar los anchos de los bordes de una ventana de estado mediante una llamada a [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Esta función miembro incluye el puntero a una matriz de tres elementos que recibe el ancho del borde horizontal del borde vertical y el borde entre los rectángulos.

## <a name="see-also"></a>Vea también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
