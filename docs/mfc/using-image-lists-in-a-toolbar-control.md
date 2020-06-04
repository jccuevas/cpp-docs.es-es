---
title: Usar listas de imágenes en un control de barra de herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: 81468528c15300a7e9ace6b20fd9fb34818f1928
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366496"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Usar listas de imágenes en un control de barra de herramientas

De forma predeterminada, las imágenes utilizadas por los botones de un control de barra de herramientas se almacenan como un único mapa de bits. Sin embargo, también puede almacenar imágenes de botones en un conjunto de listas de imágenes. El objeto de control de la barra de herramientas puede utilizar hasta tres listas de imágenes independientes:

- Lista de imágenes habilitadas Contiene imágenes para los botones de la barra de herramientas que están habilitados actualmente.

- Lista de imágenes deshabilitadas Contiene imágenes para los botones de la barra de herramientas que están deshabilitados actualmente.

- Lista de imágenes resaltadas Contiene imágenes para los botones de la barra de herramientas que están resaltados actualmente. Esta lista de imágenes solo se utiliza cuando la barra de herramientas utiliza el estilo TBSTYLE_FLAT.

Estas listas de imágenes las utiliza el `CToolBarCtrl` control de barra de herramientas cuando se asocian con el objeto. Esta asociación se realiza realizando llamadas a [CToolBarCtrl::SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist)y [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

De forma predeterminada, `CToolBar` MFC usa la clase para implementar barras de herramientas de aplicación MFC. Sin `GetToolBarCtrl` embargo, la función miembro `CToolBarCtrl` se puede utilizar para recuperar el objeto incrustado. A continuación, puede `CToolBarCtrl` realizar llamadas a funciones miembro mediante el objeto devuelto.

En el ejemplo siguiente se muestra esta`m_ToolBarImages`técnica asignando una lista de imágenes habilitada ( ) y disabled (`m_ToolBarDisabledImages`) a un `CToolBarCtrl` objeto (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
> Las listas de imágenes utilizadas por el objeto de barra de herramientas deben ser objetos permanentes. Por este motivo, suelen ser miembros de datos de una clase MFC; en este ejemplo, la clase de ventana de marco principal.

Una vez que las `CToolBarCtrl` listas de imágenes están asociadas con el objeto, el marco de trabajo muestra automáticamente la imagen de botón adecuada.

## <a name="see-also"></a>Consulte también

[Usar CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)
