---
title: Elementos de encabezado en un control de encabezado
ms.date: 11/04/2016
helpviewer_keywords:
- header controls [MFC], header items in
- header items in header controls [MFC]
- CHeaderCtrl class [MFC], header items in
- controls [MFC], header
ms.assetid: ac79ef1f-a671-4ab2-93e9-b1aa016a48bf
ms.openlocfilehash: a70d1d9225d2ac8ef2f7ed3ad9f603a64a937bc7
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620097"
---
# <a name="header-items-in-a-header-control"></a>Elementos de encabezado en un control de encabezado

Tiene un control considerable sobre la apariencia y el comportamiento de los elementos de encabezado que componen un control de encabezado ([CHeaderCtrl](reference/cheaderctrl-class.md)). Cada elemento de encabezado puede tener una cadena, una imagen de mapa de bits, una imagen de una lista de imágenes asociada o un valor de 32 bits definido por la aplicación asociado a ella. La cadena, el mapa de bits o la imagen se muestran en el elemento de encabezado.

Puede personalizar la apariencia y el contenido de los nuevos elementos cuando se crean realizando una llamada a [CHeaderCtrl:: InsertItem](reference/cheaderctrl-class.md#insertitem) o modificando un elemento existente, con una llamada a [CHeaderCtrl:: GetItem](reference/cheaderctrl-class.md#getitem) y [CHeaderCtrl:: SetItem](reference/cheaderctrl-class.md#setitem).

## <a name="what-do-you-want-to-know-more-about"></a>¿Qué desea saber más sobre

- [Personalizar la apariencia del elemento de encabezado](customizing-the-header-item-s-appearance.md)

- [Ordenar elementos en el control de encabezado](ordering-items-in-the-header-control.md)

- [Proporcionar compatibilidad con arrastrar y colocar para los elementos de encabezado](providing-drag-and-drop-support-for-header-items.md)

- [Usar listas de imágenes con controles de encabezado](using-image-lists-with-header-controls.md)

## <a name="see-also"></a>Consulte también

[Uso de CHeaderCtrl](using-cheaderctrl.md)
