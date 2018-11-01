---
title: Usar listas de imágenes en un control de barra de herramientas
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], image
- image lists [MFC], toolbar controls
- CToolBarCtrl class [MFC], image lists
ms.assetid: ccbe8df4-4ed9-4b54-bb93-9a1dcb3b97eb
ms.openlocfilehash: f8b19cd54a6fb2dca940c354ef23e7d06b35f0b3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584579"
---
# <a name="using-image-lists-in-a-toolbar-control"></a>Usar listas de imágenes en un control de barra de herramientas

De forma predeterminada, las imágenes utilizadas por los botones en un control de barra de herramientas se almacenan como un único mapa de bits. Sin embargo, también puede almacenar imágenes de los botones en un conjunto de listas de imágenes. El objeto de control de barra de herramientas puede utilizar hasta tres listas de imágenes independientes:

- Habilitar contiene imágenes de lista de imágenes para los botones de barra de herramientas que están habilitadas actualmente.

- Deshabilitar contiene imágenes de lista de imágenes para los botones de barra de herramientas que están deshabilitadas actualmente.

- Resalta contiene imágenes de lista de imágenes para los botones de barra de herramientas que actualmente están resaltados. Esta lista de imágenes sólo se utiliza cuando la barra de herramientas usa el estilo TBSTYLE_FLAT.

Estas listas de imágenes se usan por el control de barra de herramientas cuando se asociación con el `CToolBarCtrl` objeto. Esta asociación se realiza mediante llamadas a [CToolBarCtrl:: SetImageList](../mfc/reference/ctoolbarctrl-class.md#setimagelist), [SetDisabledImageList](../mfc/reference/ctoolbarctrl-class.md#setdisabledimagelist), y [SetHotImageList](../mfc/reference/ctoolbarctrl-class.md#sethotimagelist).

De forma predeterminada, MFC utiliza el `CToolBar` clase para implementar las barras de herramientas de aplicación de MFC. Sin embargo, el `GetToolBarCtrl` función miembro puede usarse para recuperar los datos incrustados `CToolBarCtrl` objeto. A continuación, puede realizar llamadas a `CToolBarCtrl` funciones miembro mediante el objeto devuelto.

En el ejemplo siguiente se muestra esta técnica asignando un habilitada (`m_ToolBarImages`) y deshabilitado (`m_ToolBarDisabledImages`) lista de imágenes a un `CToolBarCtrl` objeto (`m_ToolBarCtrl`).

[!code-cpp[NVC_MFCControlLadenDialog#35](../mfc/codesnippet/cpp/using-image-lists-in-a-toolbar-control_1.cpp)]

> [!NOTE]
>  Las listas de imágenes utilizadas por el objeto de barra de herramientas deben tener objetos permanentes. Por este motivo, normalmente son miembros de datos de una clase MFC; en este ejemplo, la clase de ventana de marco principal.

Una vez que las listas de imágenes asociadas con el `CToolBarCtrl` de objeto, el marco de trabajo muestra automáticamente la imagen correcta del botón.

## <a name="see-also"></a>Vea también

[Uso de CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Controles](../mfc/controls-mfc.md)

