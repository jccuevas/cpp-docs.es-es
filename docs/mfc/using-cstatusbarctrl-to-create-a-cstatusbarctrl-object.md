---
title: Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- status bar controls [MFC], creating
- CStatusBarCtrl class [MFC], creating
ms.assetid: 365c2b65-12de-49e6-9a2e-416c6ee10d60
ms.openlocfilehash: 12d5664b9fc59c4569ec2ee7db4ae883911f7bcd
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79442381"
---
# <a name="using-cstatusbarctrl-to-create-a-cstatusbarctrl-object"></a>Usar CStatusBarCtrl para crear un objeto CStatusBarCtrl

Este es un ejemplo de uso típico de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md):

### <a name="to-use-a-status-bar-control-with-parts"></a>Para usar un control de barra de estado con partes

1. Construya el objeto de `CStatusBarCtrl`.

1. Llame a [SetMinHeight](../mfc/reference/cstatusbarctrl-class.md#setminheight) si desea establecer el alto mínimo del área de dibujo del control de la barra de estado.

1. Llame a [SetBkColor](../mfc/reference/cstatusbarctrl-class.md#setbkcolor) para establecer el color de fondo del control de barra de estado.

1. Llame a [SetParts](../mfc/reference/cstatusbarctrl-class.md#setparts) para establecer el número de elementos de un control de barra de estado y la coordenada del borde derecho de cada elemento.

1. Llame a [setText](../mfc/reference/cstatusbarctrl-class.md#settext) para establecer el texto en una parte determinada del control de la barra de estado. El mensaje invalida la parte del control que ha cambiado, lo que hace que muestre el nuevo texto cuando el control siguiente recibe el mensaje de WM_PAINT.

En algunos casos, la barra de estado solo necesita mostrar una línea de texto. En este caso, realice una llamada a [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple). Esto coloca el control de la barra de estado en modo "simple", que muestra una sola línea de texto.

## <a name="see-also"></a>Consulte también

[Uso de CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
