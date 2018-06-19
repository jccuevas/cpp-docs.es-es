---
title: Usar botones desplegables en un Control de barra de herramientas | Documentos de Microsoft
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
ms.openlocfilehash: 39edda143e28d262e8eea826ced5c24855fb310b
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383258"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>Usar botones desplegables en un control de barra de herramientas
Además de los botones de comando estándares, una barra de herramientas también puede tener botones desplegables. Normalmente, un botón de lista desplegable se indica por la presencia de una flecha abajo adjunta.  
  
> [!NOTE]
>  La flecha abajo adjunta solo aparecerá si la `TBSTYLE_EX_DRAWDDARROWS` se ha establecido el estilo extendido.  
  
 Cuando el usuario hace clic en esta flecha (o en el botón Sí, si no hay ninguna flecha), un `TBN_DROPDOWN` mensaje de notificación se envía al elemento primario del control de barra de herramientas. A continuación, puede controlar esta notificación y mostrar un menú emergente; es similar al comportamiento de Internet Explorer.  
  
 El siguiente procedimiento muestra cómo implementar un botón de barra de herramientas de lista desplegable con un menú emergente:  
  
### <a name="to-implement-a-drop-down-button"></a>Para implementar un botón de lista desplegable  
  
1.  Una vez el `CToolBarCtrl` ha creado un objeto, establezca el `TBSTYLE_EX_DRAWDDARROWS` de estilo, utilizando el código siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]  
  
2.  Establecer el `TBSTYLE_DROPDOWN` estilo para cualquier nuevo ([InsertButton](../mfc/reference/ctoolbarctrl-class.md#insertbutton) o [AddButtons](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) o existentes ([SetButtonInfo](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)) botones que estarán botones desplegables. En el ejemplo siguiente se muestra cómo modificar un botón existente en un `CToolBarCtrl` objeto:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]  
  
3.  Agregar un `TBN_DROPDOWN` controlador a la clase primaria del objeto de barra de herramientas.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]  
  
4.  En el nuevo controlador, mostrar el menú emergente adecuado. El código siguiente muestra un método:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]  
  
## <a name="see-also"></a>Vea también  
 [Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)

