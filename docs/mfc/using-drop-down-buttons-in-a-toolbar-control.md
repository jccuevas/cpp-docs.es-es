---
title: Usar botones desplegables en un Control de barra de herramientas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
dev_langs:
- C++
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5e58b6b9d64111e021586fc23a985f31c0edf9de
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50063775"
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

