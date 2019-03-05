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
ms.openlocfilehash: 8d1a13b1921f111d97bb515e7932a0116277f9ed
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261048"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Usar botones desplegables en un control de barra de herramientas

Además de los botones de comando estándares, una barra de herramientas también puede tener botones desplegables. Normalmente, un botón de lista desplegable se indica por la presencia de una flecha abajo adjunta.

> [!NOTE]
>  La flecha abajo adjunta solo aparecerá si se ha establecido el estilo extendido de TBSTYLE_EX_DRAWDDARROWS.

Cuando el usuario hace clic en esta flecha (o el botón Sí, si no hay ninguna flecha), se envía un mensaje de notificación TBN_DROPDOWN al elemento primario del control de barra de herramientas. A continuación, puede controlar esta notificación y mostrar un menú emergente; es similar al comportamiento de Internet Explorer.

El siguiente procedimiento muestra cómo implementar un botón de barra de herramientas de lista desplegable con un menú emergente:

### <a name="to-implement-a-drop-down-button"></a>Para implementar un botón de lista desplegable

1. Una vez su `CToolBarCtrl` se ha creado el objeto, establezca el estilo TBSTYLE_EX_DRAWDDARROWS, utilizando el código siguiente:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. Establecer el estilo TBSTYLE_DROPDOWN para cualquier nuevo ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) o [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) o existente ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) botones que estarán botones desplegables. El ejemplo siguiente muestra la modificación de un botón existente en un `CToolBarCtrl` objeto:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. Agregue un controlador TBN_DROPDOWN a la clase primaria del objeto de barra de herramientas.

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. En el controlador nuevo, mostrar el menú emergente apropiado. El código siguiente muestra un método:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>Vea también

[Uso de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
