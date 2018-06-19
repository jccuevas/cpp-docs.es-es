---
title: Estilos de botón de número | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 96b559fcda4825aec71ba4b5c1dd8c3cd319b83d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33380102"
---
# <a name="spin-button-styles"></a>Estilos de botón de cuadro de número
Muchas de las configuraciones de un botón de número ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) se controlan mediante estilos. Puede establecer los siguientes estilos utilizando el **propiedades** ventana en el editor de cuadro de diálogo.  
  
-   **Orientación** Vertical u Horizontal. Controla la orientación de los botones de flecha. Asociado con el `UDS_HORZ` estilo.  
  
-   **Alineación** adjuntas, izquierda o derecha. Controla la ubicación del botón de número. Izquierda y derecha sitúan el botón de número situado junto a la ventana relacionada. Se reduce el ancho de la ventana relacionada para acomodar el botón de número. Asociado a la `UDS_ALIGNLEFT` y `UDS_ALIGNRIGHT` estilos.  
  
-   **Auto amigo** selecciona automáticamente la ventana anterior en el orden Z como ventana relacionada con el botón de número. En una plantilla de cuadro de diálogo, éste es el control que precede al botón de número en el orden de tabulación. Asociado con el `UDS_AUTOBUDDY` estilo.  
  
-   **Establecer entero conocido** hace que el control de número aumentar y disminuir el título de la ventana relacionada a medida que cambia la posición actual. Asociado con el `UDS_SETBUDDYINT` estilo.  
  
-   **No hay miles** no inserta los miles separador en el valor en el título de la ventana relacionada. Asociado con el `UDS_NOTHOUSANDS` estilo.  
  
    > [!NOTE]
    >  Establezca este estilo si desea utilizar intercambio de datos de cuadros de diálogo (DDX) para obtener el valor entero del control relacionado. `DDX_Text` no acepta separadores de miles incrustados.  
  
-   **Ajustar** hace que la posición de "ajustar" si el valor se incrementa o disminuye más allá del intervalo del control. Asociado con el `UDS_WRAP` estilo.  
  
-   **Teclas de dirección** hace que el botón de número incrementar o disminuir la posición cuando se presionan las teclas flecha arriba y flecha abajo. Asociado con el `UDS_ARROWKEYS` estilo.  
  
## <a name="see-also"></a>Vea también  
 [Usar CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Controles](../mfc/controls-mfc.md)

