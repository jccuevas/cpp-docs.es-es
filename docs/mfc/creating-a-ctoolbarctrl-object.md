---
title: Crear un objeto CToolBarCtrl
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: cf1d2eeb9efd2f8a1e7b433c0e18dd868a8b9aca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/17/2020
ms.locfileid: "79445895"
---
# <a name="creating-a-ctoolbarctrl-object"></a>Crear un objeto CToolBarCtrl

Los objetos [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) contienen varias estructuras de datos internas (una lista de mapas de bits de imagen de botón, una lista de cadenas de etiqueta de botón y una lista de estructuras `TBBUTTON`) que asocian una imagen o cadena con la posición, el estilo, el estado y el identificador de comando del botón. Un índice basado en cero hace referencia a cada uno de los elementos de estas estructuras de datos. Antes de poder usar un objeto de `CToolBarCtrl`, debe configurar estas estructuras de datos. Para obtener una lista de las estructuras de datos, vea [controles de barra de herramientas](controls-mfc.md) en el Windows SDK. La lista de cadenas solo se puede usar para las etiquetas de botón; no se pueden recuperar cadenas de la barra de herramientas.

Para usar un objeto de `CToolBarCtrl`, normalmente se siguen estos pasos:

### <a name="to-use-a-ctoolbarctrl-object"></a>Para utilizar un objeto CToolBarCtrl

1. Construya el objeto [CToolBarCtrl](../mfc/reference/ctoolbarctrl-class.md) .

1. Llame a [Create](../mfc/reference/ctoolbarctrl-class.md#create) para crear el control común de barra de herramientas de Windows y adjuntarlo al objeto `CToolBarCtrl`. Si desea imágenes de mapa de bits para botones, agregue los mapas de bits de botón a la barra de herramientas llamando a [AddBitmap](../mfc/reference/ctoolbarctrl-class.md#addbitmap). Si desea etiquetas de cadena para botones, agregue las cadenas a la barra de herramientas llamando a [addString](../mfc/reference/ctoolbarctrl-class.md#addstring) y/o [AddStrings](../mfc/reference/ctoolbarctrl-class.md#addstrings). Después de llamar a `AddString` y/o `AddStrings`, debe llamar a [AutoSize](../mfc/reference/ctoolbarctrl-class.md#autosize) para que aparezcan la cadena o las cadenas.

1. Agregue estructuras de botón a la barra de herramientas llamando a [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons).

1. Si desea información sobre herramientas, controle **TTN_NEEDTEXT** mensajes en la ventana propietaria de la barra de herramientas, como se describe en control de las [notificaciones de la información sobre herramientas](../mfc/handling-tool-tip-notifications.md).

1. Si desea que el usuario pueda personalizar la barra de herramientas, controle los mensajes de notificación de personalización en la ventana propietaria tal y como se describe en [control de notificaciones de personalización](../mfc/handling-customization-notifications.md).

## <a name="see-also"></a>Consulte también

[Uso de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
