---
title: Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
ms.openlocfilehash: 8dfaabf3da62c216d3da662f59c57b63e695d9ad
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371162"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado

Para proporcionar compatibilidad con arrastrar y colocar elementos de encabezado, especifique el estilo de HDS_DRAGDROP. La compatibilidad con arrastrar y colocar para elementos de encabezado ofrece al usuario la capacidad de reordenar los elementos de encabezado de un control de encabezado. El comportamiento predeterminado proporciona una imagen de arrastre semitransparente del elemento de encabezado que se arrastra y un indicador visual de la nueva posición, si se quita el elemento de encabezado.

Al igual que con la funcionalidad común de arrastrar y colocar, puede ampliar el comportamiento predeterminado de arrastrar y colocar controlando las notificaciones HDN_BEGINDRAG y HDN_ENDDRAG. También puede personalizar la apariencia de la imagen de arrastre reemplazando el [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) función miembro.

> [!NOTE]
> Si proporciona compatibilidad con arrastrar y colocar para un control de encabezado incrustado en un control de lista, consulte la sección Estilo extendido en el tema [Cambiar estilos](../mfc/changing-list-control-styles.md) de control de lista.

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)
