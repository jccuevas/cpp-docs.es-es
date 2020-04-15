---
title: Usar botones desplegables en un control de barra de herramientas
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 0bc4df4c07ec4b8bc5b488925cbb140609302186
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365063"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Usar botones desplegables en un control de barra de herramientas

Además de los botones de pulsación estándar, una barra de herramientas también puede tener botones desplegables. Un botón desplegable suele indicarse por la presencia de una flecha hacia abajo.

> [!NOTE]
> La flecha hacia abajo adjunta solo aparecerá si se ha establecido el TBSTYLE_EX_DRAWDDARROWS estilo extendido.

Cuando el usuario hace clic en esta flecha (o el propio botón, si no hay ninguna flecha presente), se envía un mensaje de notificación TBN_DROPDOWN al elemento primario del control de barra de herramientas. A continuación, puede controlar esta notificación y mostrar un menú emergente; similar al comportamiento de Internet Explorer.

El siguiente procedimiento ilustra cómo implementar un botón de barra de herramientas desplegable con un menú emergente:

### <a name="to-implement-a-drop-down-button"></a>Para implementar un botón desplegable

1. Una `CToolBarCtrl` vez creado el objeto, establezca el estilo TBSTYLE_EX_DRAWDDARROWS, utilizando el código siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Establezca el estilo TBSTYLE_DROPDOWN para los botones nuevos ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) o [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) o existentes ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) que serán botones desplegables. En el ejemplo siguiente se muestra `CToolBarCtrl` cómo modificar un botón existente en un objeto:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Agregue un controlador de TBN_DROPDOWN a la clase primaria del objeto de barra de herramientas.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. En el nuevo controlador, muestre el menú emergente adecuado. El código siguiente muestra un método:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Consulte también

[Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
