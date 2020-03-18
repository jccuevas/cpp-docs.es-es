---
title: Configuración de CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: 18c4c780ecf7865d8d648bfa4c54961bbffe7b18
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446388"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Configuración de CStatusBarCtrl

La posición predeterminada de una ventana de estado de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) está a lo largo de la parte inferior de la ventana primaria, pero puede especificar el estilo de CCS_TOP para que aparezca en la parte superior del área de cliente de la ventana primaria.

Puede especificar el estilo de SBARS_SIZEGRIP para incluir un control de tamaño en el extremo derecho de la ventana de estado de la `CStatusBarCtrl`. Un control de tamaño es similar a un borde de tamaño; es un área rectangular en la que el usuario puede hacer clic y arrastrar para cambiar el tamaño de la ventana primaria.

> [!NOTE]
>  Si combina los estilos CCS_TOP y SBARS_SIZEGRIP, el control de tamaño resultante no es funcional, aunque el sistema lo dibuje en la ventana de estado.

El procedimiento de ventana de la ventana de Estado establece automáticamente el tamaño y la posición iniciales de la ventana de control. El ancho es el mismo que el del área de cliente de la ventana primaria. El alto se basa en las métricas de la fuente seleccionada actualmente en el contexto de dispositivo de la ventana de estado y en el ancho de los bordes de la ventana.

El procedimiento de ventana ajusta automáticamente el tamaño de la ventana de estado cada vez que recibe un mensaje de WM_SIZE. Normalmente, cuando cambia el tamaño de la ventana primaria, el elemento primario envía un mensaje de WM_SIZE a la ventana de estado.

Puede establecer el alto mínimo del área de dibujo de una ventana de estado llamando a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), especificando el alto mínimo en píxeles. El área de dibujo no incluye los bordes de la ventana.

El ancho de los bordes de una ventana de estado se recupera mediante una llamada a [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Esta función miembro incluye el puntero a una matriz de tres elementos que recibe el ancho del borde horizontal, el borde vertical y el borde entre los rectángulos.

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
