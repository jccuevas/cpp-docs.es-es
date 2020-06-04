---
title: Selección de elementos de control de árbol
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item selection
- controls [MFC], selecting items in
- CTreeCtrl class [MFC], item selection
- item selection in tree controls
ms.assetid: 7bcb3b16-b9c8-4c06-9350-7bc3c1c5009b
ms.openlocfilehash: 07c7b673e0f9029f8ece928b0ab17760b3863cc7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513339"
---
# <a name="tree-control-item-selection"></a>Selección de elementos de control de árbol

Cuando la selección cambia de un elemento a otro, un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) envía mensajes de notificación [TVN_SELCHANGING](/windows/win32/Controls/tvn-selchanging) y [TVN_SELCHANGED](/windows/win32/Controls/tvn-selchanged) . Ambas notificaciones incluyen un valor que especifica si el cambio es el resultado de un clic del mouse o una pulsación de tecla. Las notificaciones también incluyen información sobre el elemento que obtiene la selección y el elemento que pierde la selección. Puede usar esta información para establecer atributos de elementos que dependen del estado de selección del elemento. Devolver **true** en respuesta a `TVN_SELCHANGING` impide que la selección cambie; si se devuelve **false** , se permite el cambio.

Una aplicación puede cambiar la selección mediante una llamada a la función miembro [SelectItem](../mfc/reference/ctreectrl-class.md#selectitem) .

## <a name="see-also"></a>Vea también

[Uso de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
