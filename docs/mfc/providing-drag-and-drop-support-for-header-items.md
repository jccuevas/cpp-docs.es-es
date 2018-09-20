---
title: Que proporciona compatibilidad con arrastrar y colocar elementos de encabezado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- HDS_DRAGDROP style
- header items in header controls
- CHeaderCtrl class [MFC], drag and drop support
- HDN_ notifications [MFC]
ms.assetid: 93a152ec-804f-488f-b260-b3a438d0dc0f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b2eaa5040d34a442868a8fa6cb9f2aae08b0a6f3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46407704"
---
# <a name="providing-drag-and-drop-support-for-header-items"></a>Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado

Para proporcionar compatibilidad con arrastrar y colocar en elementos de encabezado, especifique HDS_DRAGDROP (estilo). Compatibilidad con arrastrar y colocar elementos de encabezado proporciona al usuario la capacidad para volver a ordenar los elementos de encabezado de un control de encabezado. El comportamiento predeterminado proporciona una imagen de arrastre semitransparente del elemento de encabezado que se arrastran y un indicador visual de la nueva posición, si se quita el elemento de encabezado.

Como con una funcionalidad común de arrastrar y colocar, puede ampliar el comportamiento de arrastrar y colocar de forma predeterminada al controlar las notificaciones igual y HDN_ENDDRAG. También puede personalizar la apariencia de la imagen de arrastre invalidando el [CHeaderCtrl::CreateDragImage](../mfc/reference/cheaderctrl-class.md#createdragimage) función miembro.

> [!NOTE]
>  Si va a proporcionar compatibilidad con arrastrar y colocar para un control de encabezado incrustado en un control de lista, consulte la sección de estilo extendido en el [cambiar los estilos de Control de lista](../mfc/changing-list-control-styles.md) tema.

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

