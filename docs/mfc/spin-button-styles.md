---
title: Estilos de botón de cuadro de número
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 1aae4b7e4c63929ebe03c97d50f05754bc13ec26
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907857"
---
# <a name="spin-button-styles"></a>Estilos de botón de cuadro de número

Muchas de las opciones de un botón de número ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) se controlan mediante estilos. Puede establecer los siguientes estilos mediante el [Asistente para clases](reference/mfc-class-wizard.md).

- **Orientación** Vertical u horizontal. Controla la orientación de los botones de flecha. Asociado al estilo UDS_HORZ.

- **Alineación** de Uno de los no adjuntos, izquierda o derecha. Controla la ubicación del botón de número. Izquierda y derecha Coloque el botón de número junto a la ventana relacionada. El ancho de la ventana relacionada se reduce para acomodar el botón de número. Se asocia a los estilos UDS_ALIGNLEFT y UDS_ALIGNRIGHT.

- **Colega automático** Selecciona automáticamente la ventana anterior en el orden Z como ventana relacionada con el botón de número. En una plantilla de cuadro de diálogo, este es el control que precede al botón de número en el orden de tabulación. Asociado al estilo UDS_AUTOBUDDY.

- **Establecer un entero de Buddy** Hace que el control de número aumente y disminuya el título de la ventana relacionada a medida que cambia la posición actual. Asociado al estilo UDS_SETBUDDYINT.

- **Sin miles** No inserta el separador de miles en el valor en el título de la ventana relacionada. Asociado al estilo UDS_NOTHOUSANDS.

    > [!NOTE]
    >  Establezca este estilo si desea utilizar el intercambio de datos de cuadros de diálogo (DDX) para obtener el valor entero del control relacionado. `DDX_Text`no acepta separadores de miles incrustados.

- **Ajustar** Hace que la posición se "ajuste", ya que el valor se incrementa o disminuye más allá del intervalo del control. Asociado al estilo UDS_WRAP.

- **Teclas de dirección** Hace que el botón de número aumente o disminuya la posición cuando se presionan las teclas flecha arriba y flecha abajo. Asociado al estilo UDS_ARROWKEYS.

## <a name="see-also"></a>Vea también

[Uso de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
