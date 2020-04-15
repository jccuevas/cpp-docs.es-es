---
title: Configuración de CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], settings
- CStatusBarCtrl class [MFC], settings
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
ms.openlocfilehash: dd7c68d6721c48f751c04437e43c8770f6ec5736
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365375"
---
# <a name="settings-for-the-cstatusbarctrl"></a>Configuración de CStatusBarCtrl

La posición predeterminada de una ventana de estado [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) se encuentra en la parte inferior de la ventana primaria, pero puede especificar el estilo CCS_TOP para que aparezca en la parte superior del área de cliente de la ventana primaria.

Puede especificar el estilo de SBARS_SIZEGRIP para incluir un `CStatusBarCtrl` pinzamiento de tamaño en el extremo derecho de la ventana de estado. Un pinzamiento de tamaño es similar a un borde de tamaño; es un área rectangular en la que el usuario puede hacer clic y arrastrar para cambiar el tamaño de la ventana principal.

> [!NOTE]
> Si combina los estilos CCS_TOP y SBARS_SIZEGRIP, el pinzamiento de tamaño resultante no es funcional aunque el sistema lo dibuje en la ventana de estado.

El procedimiento de ventana para la ventana de estado establece automáticamente el tamaño inicial y la posición de la ventana de control. El ancho es el mismo que el del área de cliente de la ventana primaria. La altura se basa en las métricas de la fuente que está seleccionada actualmente en el contexto del dispositivo de la ventana de estado y en el ancho de los bordes de la ventana.

El procedimiento de ventana ajusta automáticamente el tamaño de la ventana de estado cada vez que recibe un mensaje de WM_SIZE. Normalmente, cuando cambia el tamaño de la ventana primaria, el elemento primario envía un mensaje de WM_SIZE a la ventana de estado.

Puede establecer la altura mínima del área de dibujo de una ventana de estado llamando a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight), especificando la altura mínima en píxeles. El área de dibujo no incluye los bordes de la ventana.

Recuperar los anchos de los bordes de una ventana de estado mediante una llamada a [GetBorders](../mfc/reference/cstatusbarctrl-class.md#getborders). Esta función miembro incluye el puntero a una matriz de tres elementos que recibe el ancho del borde horizontal, el borde vertical y el borde entre rectángulos.

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
