---
title: Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 21ff14982baac93fac1cf3ee441353c079f4f760
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50602974"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado

Para proporcionar compatibilidad con arrastrar y colocar en elementos de encabezado, especifique HDS_DRAGDROP (estilo). Compatibilidad con arrastrar y colocar elementos de encabezado proporciona al usuario la capacidad para volver a ordenar los elementos de encabezado de un control de encabezado. El comportamiento predeterminado proporciona una imagen de arrastre semitransparente del elemento de encabezado que se arrastran y un indicador visual de la nueva posición, si se quita el elemento de encabezado.

Como con una funcionalidad común de arrastrar y colocar, puede ampliar el comportamiento de arrastrar y colocar de forma predeterminada al controlar las notificaciones igual y HDN_ENDDRAG. También puede personalizar la apariencia de la imagen de arrastre invalidando el [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) función miembro.

> [!NOTE]
>  Si va a proporcionar compatibilidad con arrastrar y colocar para un control de encabezado incrustado en un control de lista, consulte la sección de estilo extendido en el [cambiar los estilos de Control de lista](../mfc/changing-list-control-styles.md) tema.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

