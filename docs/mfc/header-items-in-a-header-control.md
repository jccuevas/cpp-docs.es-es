---
title: Elementos de encabezado en un Control de encabezado | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 21f1893861c5cb6a134cffa75806cc53eadaf059
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46442375"
---
# <a name="header-items-in-a-header-control"></a>Elementos de encabezado en un control de encabezado

Tiene un gran control sobre la apariencia y comportamiento de los elementos de encabezado que componen un control de encabezado ([CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)). Cada elemento de encabezado puede tener una cadena, una imagen de mapa de bits, una imagen de una lista de imágenes asociada o un valor de 32 bits definido por la aplicación asociada con él. La cadena, el mapa de bits o la imagen se muestra en el elemento de encabezado.

Puede personalizar la apariencia y el contenido de los elementos nuevos cuando se crean mediante una llamada [:: InsertItem](../mfc/reference/cheaderctrl-class.md#insertitem) o modificando un elemento existente, con una llamada a [CHeaderCtrl:: GetItem](../mfc/reference/cheaderctrl-class.md#getitem) y [ CHeaderCtrl:: SetItem](../mfc/reference/cheaderctrl-class.md#setitem).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Personalizar la apariencia del elemento de encabezado](../mfc/customizing-the-header-item-s-appearance.md)

- [Ordenar elementos en el control de encabezado](../mfc/ordering-items-in-the-header-control.md)

- [Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado](../mfc/providing-drag-and-drop-support-for-header-items.md)

- [Usar listas de imágenes con controles de encabezado](../mfc/using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Vea también

[Uso de CHeaderCtrl](../mfc/using-cheaderctrl.md)

