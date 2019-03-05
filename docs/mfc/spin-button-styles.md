---
title: Estilos de botón de cuadro de número
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: d955ba1d76ee4d5648613ddaf6c5f6a652f3d3af
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304878"
---
# <a name="spin-button-styles"></a>Estilos de botón de cuadro de número

Muchos de los valores para un botón de número ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) se controlan mediante estilos. Puede establecer los siguientes estilos utilizando el **propiedades** ventana en el editor de cuadro de diálogo.

- **Orientación** Vertical u Horizontal. Controla la orientación de los botones de flecha. Asociado al estilo UDS_HORZ.

- **Alineación** no conectados, izquierda o derecha. Controla la ubicación del botón de número. Left y Right coloque el botón de número situado junto a la ventana relacionada. Se reduce el ancho de la ventana relacionada para acomodar el botón de número. Asociado con los estilos está y UDS_ALIGNRIGHT.

- **Auto Buddy** selecciona automáticamente la ventana anterior en orden Z como ventana relacionada con el botón de número. En una plantilla de cuadro de diálogo, éste es el control que precede al botón de número en el orden de tabulación. Asociado al estilo UDS_AUTOBUDDY.

- **Establecer Buddy Integer** hace que el control de flechas aumentar y disminuir el título de la ventana relacionada como cambia la posición actual. Asociado al estilo UDS_SETBUDDYINT.

- **No Thousands** no inserta las miles separador en el valor en el título de la ventana relacionada. Asociado al estilo UDS_NOTHOUSANDS.

    > [!NOTE]
    >  Establecer este estilo si desea usar el intercambio de datos de cuadro de diálogo (DDX) para obtener el valor entero del control relacionado. `DDX_Text` no acepta separadores de miles incrustados.

- **Ajustar** hace que la posición "encapsular" como el valor se incrementa o se reduce más allá del intervalo del control. Asociado al estilo UDS_WRAP.

- **Teclas de dirección** hace que el botón de número incrementar o disminuir la posición cuando se presionan las teclas flecha arriba y flecha abajo. Asociado al estilo UDS_ARROWKEYS.

## <a name="see-also"></a>Vea también

[Uso de CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
